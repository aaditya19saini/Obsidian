# SnapNutrition — Project Design Notes

> A personal food recognition and nutrition tracking system using computer vision and NLP.  
> These notes capture the full problem space, design decisions, pitfalls, and proposed solutions discussed during the initial design session.

---

## 1. Project Overview

**Goal:** Build a personal-use app that automatically identifies food from a photo and logs its nutritional content — with zero or minimal manual input from the user.

**Core technologies:**
- Computer vision (CV) — identify food items from images
- NLP — parse text descriptions, generate smart disambiguation questions, extract quantity from natural language
- Nutrition database lookup — map food items to calories, macros, micronutrients
- Bayesian inference — combine visual signals with contextual priors for better accuracy

**Inputs the system should handle:**
- A photo of a plate (primary)
- Text description (e.g. "2 boiled eggs and toast")
- Barcode / packaged food label scan

**Output:**
- Identified food items with estimated quantities
- Nutritional breakdown (calories, protein, carbs, fat)
- A personal meal log and dashboard

---

## 2. The Core Pipeline

```
Photo / Text / Barcode
        ↓
[Food identification — CV + NLP]
        ↓
[Quantity estimation]
        ↓
[Nutrition database lookup]
        ↓
[Meal log + dashboard]
```

---

## 3. Quantity Estimation — The Hard Problem

Identifying *what* the food is is only half the battle. Estimating *how much* of it is on the plate — without the user typing anything — is significantly harder.

### 3.1 Approaches Considered

#### Reference object detection
Use a known object in the frame (fork, coin, hand) as a scale anchor. Detect its pixel size, infer pixel-to-cm ratio, then estimate food area.

**Problem:** Cutlery dimensions vary wildly across regions and contexts. An Indian fork (~18cm), a US dinner fork (~20cm), a dessert fork (~16cm) — that's a 25% variance before accounting for chopsticks, spoons, or hand-eating contexts. Plates vary too (thali vs pasta bowl vs western dinner plate). This makes the calibration anchor unreliable.

#### [[Monocular depth estimation]]
Use models like MiDaS or ZoeDepth to infer a depth map from a single image. Combined with food segmentation masks, estimate 3D volume per food item.

`volume = segmented area × average depth from depth map`

**Pros:** Single photo, no special hardware, works on any smartphone.  
**Cons:** Accuracy depends on lighting and texture.

#### Multi-photo 3D reconstruction
User takes 2–3 photos from different angles. Structure-from-motion builds a 3D point cloud, and volume is estimated per food segment.

**Pros:** High accuracy.  
**Cons:** High user friction — defeats the zero-effort goal.

#### Plate-normalized estimation (recommended starting point)
Assume the plate diameter is a known constant (e.g. 25cm). The detected plate circle gives an exact pixel-to-cm conversion for that photo. Each food item's area is computed as a fraction of the plate, then multiplied by a per-food density prior.

`grams = (food area / plate area) × plate_fraction_to_grams_lookup[food_class]`

**For many foods, height estimation isn't even needed.** "Rice covering 30% of a 25cm plate ≈ 180g" is a learnable rule. Residual error comes from density variation (fluffy vs packed rice), which is a simpler secondary classifier.

#### Height estimation (to improve plate-normalization)
- **Shadow geometry:** Light source + shadow length → trigonometric height estimate
- **Shading cues:** CNN learns height from highlight/shading patterns on food mounds
- **Food-class height priors:** Per-class lookup (e.g. roti = always 3–5mm flat, rice mound = height-to-area ratio learned from data)

---

## 4. The Standardized Plate Assumption

**Key insight:** If we can guarantee every user photographs food on a standard-sized plate, the entire quantity estimation problem simplifies dramatically.

- The plate becomes the coordinate system
- Pixel-to-cm ratio is instantly known from plate detection
- No reference object needed in frame
- Coverage fraction → grams becomes a simple learned lookup per food class

**Unlocked trick:** For many foods, you don't need height at all. Area fraction alone, combined with a density prior, gives a good enough estimate for a personal tracker.

---

## 5. Photo Quality Pitfalls

Three failure modes that break the estimation pipeline:

| Failure mode | Problem | Defense |
|---|---|---|
| Bad lighting | Shadows obscure boundaries; shiny sauces reflect; dark foods on dark plates disappear | Photo quality gate before pipeline runs |
| Bad angle | Tilted plate → ellipse → broken pixel-to-cm calibration | Ellipse-to-circle homography correction |
| Bad photo quality | Blur, low resolution, steam | Pre-pipeline quality classifier with user feedback |

### Defenses

**Photo quality gating** — a lightweight pre-check before the main pipeline runs. Checks: is plate fully visible? Is lighting sufficient? Is angle within range? If a check fails, prompt the user with specific feedback ("too much glare", "plate partially cut off") rather than running a bad estimate silently.

**Homography (angle) correction** — when a circular plate is photographed at an angle it becomes a detectable ellipse. The minor/major axis ratio gives the exact tilt angle. Standard homography correction unwarps the image to a top-down view before any area calculation.

**Confidence scores, not just estimates** — every food item gets a confidence score. Low-confidence items are flagged visually. User corrects only flagged items, not everything.

**Multi-shot cross-checking** — optionally take two photos (top-down + 45°). If the two estimates agree within 15%, confidence is high. If they diverge, fall back gracefully.

**Learn from corrections** — every user correction is stored and used to tighten the personal prior. Over time, the model needs the photo less because it knows your eating patterns.

**Key design principle:** Show a range, not a false precise number. "Estimated 160–200g of rice" with a confidence indicator is more honest and more trusted than "182g."

---

## 6. The Lookalike Food Problem

Visual similarity between foods — especially in the Indian context — is a fundamental limitation of pure CV approaches.

### 6.1 Nightmare Pairs (Indian Context)

- Dal tadka vs dal makhani vs sambhar — all brown/orange liquids
- Paneer bhurji vs scrambled eggs vs crumbled tofu
- Kheer vs raita vs shrikhand — all white, creamy, in bowls
- Poha vs upma vs sabudana khichdi — all pale, granular
- Rajma vs chole vs black-eyed peas — all legume curries in similar gravy
- Besan cheela vs dosa vs uttapam — all flat, slightly brown, circular

A standard ResNet trained on Food-101 (predominantly Western food) will completely fail here. Even an Indian-food-specific model struggles because the visual difference (e.g. dal tadka vs dal makhani) is largely in the garnish and the oil sheen — not in shape or color distribution.

### 6.2 The Multi-Layer Disambiguation Pipeline

```
Visual classifier
      ↓
Top-k predictions with confidence scores
      ↓
Confidence above threshold?
   → YES: auto-log (with one-tap correction option)
   → NO: pass to context signal layer
      ↓
Layer 2: Context signals (time, co-occurring foods, history, location)
      ↓
Layer 3: Smart NLP micro-question to user (one targeted question, not "what is this?")
      ↓
Layer 4: Store correction → update personal prior
```

### 6.3 Context Signals

| Signal | Example |
|---|---|
| Time of day | 8am photo → breakfast foods upweighted (poha, idli, paratha); dal makhani downweighted |
| Co-occurring foods | Roti in same photo → North Indian dal likely; rice in same photo → sambhar/rasam likely |
| Day of week | User eats rajma every Sunday → strong prior |
| Location | Mumbai → pav bhaji/vada pav upweighted; Chennai → idli/dosa/rasam upweighted |
| User history | Has never logged dal makhani → prior near zero |
| Home vs restaurant | Changes the entire distribution of likely foods |

**Smart micro-question example:** Instead of asking "what food is this?", ask a razor-specific question generated by the NLP layer based on exactly which pair is ambiguous: "Does this dal have cream in it?" — one tap, yes/no, disambiguates dal tadka vs dal makhani.

**Key principle:** Never block the user with uncertainty. Make the best guess, log it, show a subtle "does this look right?" nudge. Friction must be near zero or users stop logging.

---

## 7. Food Co-occurrence Graphs — The Regional Cuisine Layer

### 7.1 The Core Insight

The moment the CV model confidently identifies *one* food item on a plate, every other ambiguous item's probability distribution shifts dramatically. This is a conditional probability system, not a simple lookup.

**Example:** If bhature is detected with high confidence, the probability of the brown gravy being chole jumps to ~85%. It physically cannot be rajma-chawal — because bhature and chawal don't coexist on the same plate in any Indian regional cuisine. This is a hard constraint, not a soft preference.

### 7.2 Known Strong Pairings

| Food | Almost always paired with |
|---|---|
| Rajma | Chawal |
| Chole | Bhature OR chawal |
| Dosa | Sambar + coconut/tomato chutney |
| Idli | Sambar + chutney |
| Dal tadka | Roti or chawal |
| Rasam | Rice |
| Pav bhaji | Pav (dinner rolls) |
| Biryani | Raita |

### 7.3 Regional Cuisine Clusters

Foods cluster by regional cuisine. Items within a cluster pull toward each other; items across clusters are anti-correlated.

- **South Indian cluster:** Idli, dosa, uttapam, sambar, rasam, coconut chutney, tomato chutney, filter coffee, vada
- **North Indian cluster:** Dal tadka, dal makhani, roti, naan, paneer dishes, rajma, chole, jeera rice
- **Gujarati thali cluster:** Dal dhokli, kadhi, thepla, undhiyu, shrikhand, chaas
- **Bengali cluster:** Machher jhol, dal, begun bhaja, mishti doi, luchi

Knowing the user's home region (asked once at setup) gives a powerful prior across the entire session.

### 7.4 How to Build the Graph

**Data sources:**
- Zomato / Swiggy order data — every order is a ground truth co-occurrence signal ("people who ordered dosa also ordered sambar 94% of the time")
- Food blogs and recipe sites — a chole bhature recipe always mentions both items
- Restaurant menus — items listed together on a thali define co-occurrence sets

**Representation:** Train food embeddings (similar to word2vec) on meal co-occurrence data. Foods that always appear together cluster tightly in embedding space. Foods from different regional cuisines land far apart — cross-cluster distance is itself a signal that something is wrong with a classification.

### 7.5 The Meal Completion Model

The most powerful application of the co-occurrence graph: given the items already identified on a plate, predict what else is likely there — and go looking for it specifically in the image.

If rice and a yellow liquid are found → the model predicts sambar or dal with high probability → it runs a targeted search for sambar/dal rather than a blind classification pass over the rest of the plate.

This converts the problem from open-ended classification to guided verification — dramatically more accurate and computationally cheaper.

---

## 8. What Makes This Novel

Combining all of the above into a unified system for Indian food is genuinely underexplored. Specifically:

1. **Indian food co-occurrence graph as a Bayesian prior on top of visual classification** — not just a lookup table but a learned embedding that captures regional cuisine structure
2. **Plate-normalized area estimation as the primary quantity signal** — simple, robust, no depth camera needed
3. **Confidence-aware UX** — the system knows what it doesn't know and handles uncertainty gracefully rather than silently
4. **Personalisation loop** — every correction tightens the prior, so the system gets more accurate the more you use it

---

## 9. Recommended Build Phases

### Phase 1 — Foundation
- Plate detection (Hough circle transform or YOLO)
- Food classification (fine-tuned ResNet or EfficientNet on Indian food dataset)
- Plate-normalized area → gram estimation with static density priors
- Basic nutrition lookup via USDA FoodData Central or Open Food Facts API
- Simple meal log + SQLite storage

### Phase 2 — Smarter Estimation
- Monocular depth integration (MiDaS or ZoeDepth) for height dimension
- Food segmentation (SAM — Segment Anything Model)
- Photo quality gating + homography angle correction
- Confidence scores in UI

### Phase 3 — Intelligence Layer
- Food co-occurrence graph (build from public recipe/menu data)
- Context signals (time of day, co-occurring food priors, regional prior)
- NLP micro-question generator for disambiguation
- User correction loop → personal prior updates

### Phase 4 — Advanced
- Meal completion model (predict what else is on the plate from partial identification)
- Regional cuisine embedding model
- Multi-photo cross-validation (optional, for power users)

---

## 10. Tech Stack Suggestions

| Component | Options |
|---|---|
| Backend | Python + FastAPI |
| CV / segmentation | PyTorch + torchvision, SAM, MiDaS |
| Food classifier | Fine-tuned EfficientNet or ResNet on Indian food dataset |
| NLP / disambiguation | Claude API (fast to prototype) |
| Depth estimation | MiDaS, ZoeDepth, or Apple Depth API (on-device) |
| Nutrition database | USDA FoodData Central (free API), Open Food Facts |
| Storage | SQLite (local), JSON flat files |
| Frontend | CLI for personal use, or simple web UI |

---

## 11. Open Questions / Future Exploration

- What is the best publicly available Indian food image dataset, or does one need to be built?
- Can Zomato/Swiggy order data be approximated from public menu scraping for co-occurrence training?
- What is the right confidence threshold for auto-logging vs prompting the user?
- How many user corrections are needed before the personal prior dominates the visual signal?
- Is the meal completion model worth the complexity in Phase 1, or is it strictly a Phase 3 feature?

---

*Notes compiled from initial design session. Use this document to resume the conversation with any LLM by sharing it as context.*
