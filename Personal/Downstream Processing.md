# Filtration (Bioprocess Engineering Notes)

## 1. Why Filtration Exists

In downstream processing, the **first job** is often to separate **cells from the fermentation broth**.

This is required when:

1. **Cells are the product**  
    Example: yeast biomass
    
2. **Product is extracellular**  
    Example: antibiotics in broth
    
3. **Product is intracellular**  
    Cells must be broken first, then components separated
    

Because fermentation broths contain **large amounts of suspended solids**, separation becomes a major processing step.

---

# 2. Methods for Removing Cells

Three main approaches exist:

|Method|Separation Principle|
|---|---|
|**Filtration**|Particle size|
|**Centrifugation**|Density|
|**Coagulation / flocculation**|Aggregation of particles|

Filtration is usually preferred because it is **simple and cost effective**.

---

# 3. What Is Filtration?

Filtration separates **solid particles from a liquid-solid mixture** by passing the mixture through a **filter medium**.

Basic rule:

**Particles larger than filter pores are retained.**

### Terminology

|Term|Meaning|
|---|---|
|**Feed**|slurry entering filter|
|**Filter medium**|membrane or cloth|
|**Filtrate**|liquid passing through|
|**Residue / filter cake**|solids retained|

The diagram on **page 4** shows this clearly: feed passes through a porous barrier while solids remain on top forming a cake.

---

# 4. Filter Cake Formation

During filtration:

1. Solids accumulate on the filter surface
    
2. This layer becomes the **filter cake**
    
3. Cake thickness increases with time
    

Consequences:

|Effect|Result|
|---|---|
|Cake thicker|resistance increases|
|Filtration rate|decreases|
|Filtrate clarity|improves|

So filtration has a tradeoff:

**Better purity but slower flow.**

---

# 5. Filtration Pressure Drop

Filtration requires a **pressure difference across the filter**.

This pressure difference drives liquid through the medium.

Pressure difference can be created by:

1. Applying **pressure on feed side**
    
2. Applying **vacuum on filtrate side**
    

Industrial filters use both methods.

---

# 6. Filter Aids

Early in filtration, the filter cake is thin and inefficient.

To improve performance, **filter aids** are used.

Common filter aids:

- Diatomaceous earth
    
- Cellulose
    
- Supercel
    

Purpose:

• increase cake porosity  
• prevent clogging  
• improve filtration rate

However:

If the **residue is the desired product**, filter aids are usually avoided to prevent contamination.

---

# 7. Compressibility of Microbial Cakes

Microbial biomass behaves differently from rigid particles.

Most microbial cakes are **compressible**.

Meaning:

Increasing pressure compresses the cake → reduces porosity → decreases filtration rate.

Filter aids help solve this issue.

---

# 8. Types of Filtration

Filtration systems are divided into **three categories**.

## 1. Cake Filtration

Used when:

• slurry has high solid concentration

Process:

Solids accumulate and form a thick **filter cake**.

Purpose:

Recover solid biomass.

---

## 2. Clarifying Filtration

Used when:

• solids concentration is low

Goal:

Produce a **clear liquid**.

Example:

fruit juice clarification.

---

## 3. Cross-Flow Filtration

Here the fluid flows **parallel to the membrane surface**.

Instead of cake buildup:

• solids remain in flowing stream  
• liquid passes through membrane

Purpose:

**concentrate dilute suspensions**.

The diagram on **page 10** shows the difference between dead-end filtration and cross-flow filtration.

---

# 9. Plate and Frame Filter Press

One of the most common industrial filters.

Structure:

• multiple plates  
• hollow frames  
• filter cloth

Plates and frames are stacked together forming chambers.

Operation:

1. Slurry pumped into chambers
    
2. Liquid passes through filter cloth
    
3. Solids accumulate in frames as cake
    
4. Filtrate leaves through outlet channels
    

Typical pressure:

**3–10 atm**.

When cake becomes thick:

The system is opened and solids are removed.

---

# 10. Pressure Leaf Filter

Improved version of plate and frame filter.

Features:

• filter leaves stacked inside cylindrical vessel  
• operates at **higher pressures**  
• slurry pumped into drum  
• filtrate collected through manifold

This design allows **compact and efficient filtration**.

---

# 11. Rotary Vacuum Filter

Used for **continuous filtration**.

Key parts (shown in diagram on page 15):

• rotating drum  
• slurry trough  
• vacuum system  
• scraper blade

Operation:

1. Drum rotates through slurry
    
2. Vacuum pulls liquid through filter cloth
    
3. Cake forms on drum surface
    
4. Cake scraped off continuously
    

Advantages:

• continuous operation  
• high throughput  
• suitable for industrial fermentation broths.

---

# Quick Exam Cheat Sheet

Filtration separates **solid from liquid using a porous medium**.

Key concepts:

Residue → solids retained  
Filtrate → liquid passing through

Cake buildup:

↑ cake thickness  
↓ filtration rate  
↑ filtrate clarity

Types:

1. Cake filtration
    
2. Clarifying filtration
    
3. Cross-flow filtration
    

Industrial filters:

• Plate & frame filter press  
• Pressure leaf filter  
• Rotary vacuum filter

---
# Centrifugation, Coagulation and Flocculation


# 1. Why Centrifugation Exists

In downstream processing we often need to separate **cells from liquid broth**.

Gravity settling is slow because:

• cells are very small  
• density difference is small  
• broth viscosity is high

So we use **centrifugation**, which applies a force much greater than gravity.

Think of it like this:

**Gravity settling = sand falling in water**

**Centrifugation = spinning the container so particles slam outward.**

---

# 2. Physics of Particle Settling

When a particle moves through a liquid, **three forces act on it**:

|Force|Meaning|
|---|---|
|FG|gravitational force|
|FD|drag force|
|FB|buoyant force|

At steady state:


$F_G = F_D + F_B$  


When this balance occurs, the particle moves at **terminal velocity**.

---

# 3. Stokes Law (Drag Force)

For small biological particles:

$[$  
$F_D = 6 \pi r \mu v$  
$]$

Where:

|Variable|Meaning|
|---|---|
|r|particle radius|
|μ|fluid viscosity|
|v|particle velocity|

Valid when **Re < 1**, which is true for most biological particles.

---

# 4. Terminal Settling Velocity

For gravitational settling:


$v_g =$  $\frac{2 r^2 (\rho_p - \rho_m) g}{9 \mu}$  


Important conclusions:

Settling becomes faster when:

• particle size increases  
• density difference increases  
• viscosity decreases

This equation explains **why bacteria settle extremely slowly**.

---

# 5. Centrifugal Settling

Instead of gravity (g), centrifugation uses **centrifugal acceleration**.

$[$  
$a = r\omega^2$  
$]$

$So terminal velocity becomes:$

$[$  
$v_c =$  
$\frac{2 r^2 (\rho_p - \rho_m) r\omega^2}{9\mu}$  
$]$

Meaning:

Higher **rotation speed → faster separation**.

---

# 6. Relative Centrifugal Force (RCF)

Scientists usually describe centrifuge power using **g-force**.

$[$  
$Z = \frac{F_c}{F_g}$  
$]$

$Simplified form:$

$[$  
$Z = 0.001119 , r n^2$  
$]$

Where:

|Variable|Meaning|
|---|---|
|r|rotor radius|
|n|rotational speed (rpm)|

RCF tells us **how strong the centrifuge is compared to gravity**.

Example:

10,000 g means **10,000 times stronger than gravity**.

---

# 7. When Centrifugation Works Best

Centrifugation works best when:

• particle size is large  
• density difference is high  
• viscosity is low  
• rotation speed is high

But biological systems often have:

• tiny cells  
• similar densities

So **very high speeds are needed**.

---

# 8. Types of Centrifuges

## 1. Laboratory Centrifuge

Used for small-scale separations.

Typical volume:

**1 mL – 5 L**

Process:

1. Sample placed in tubes
    
2. Tubes mounted symmetrically on rotor
    
3. Spinning causes particles to sediment
    

The diagram on **page 10** shows the formation of **pellet and supernatant** after centrifugation.

---

# 9. Types of Rotors

## Fixed Angle Rotor

Tubes stay at fixed angle.

Advantages:

• faster sedimentation  
• smaller pellet area

---

## Swing-Out Rotor

Tubes swing outward during spinning.

Advantages:

• better layer separation

The diagram on **page 11** illustrates this difference clearly.

---

# 10. Preparative Centrifuges

Used in industrial scale.

Handle volumes:

**1 L to thousands of liters**

Features:

• tubular rotating chamber  
• continuous or semi-continuous operation.

---

# 11. Types of Industrial Centrifuges

## 1. Tubular Bowl Centrifuge

Structure:

• vertical cylindrical rotor  
• feed enters from bottom  
• particles move outward to wall

Operation:

• solids stick to bowl walls  
• liquid exits from top

Industrial usage:

• protein precipitation  
• pharmaceutical processing

Typical force:

**13,000 – 16,000 g**.

---

### Advantages

• very high centrifugal force  
• good dewatering

### Disadvantages

• efficiency decreases as bowl fills

---

# 12. Basket Centrifuge

Structure:

• perforated bowl  
• nylon filter bag

Operation:

• slurry fed continuously  
• solids form cake on basket

Applications:

• fungal mycelia  
• crystalline compounds

Typical speed:

**up to 4000 rpm**.

---

# 13. Ultracentrifuge

Used for **very small particles**.

Applications:

• ribosomes  
• DNA  
• RNA  
• viruses

Acceleration:

**50,000 – 100,000 g**.

Major use:

**vaccine production**.

---

# 14. Centrifuge Scale-Up

Industrial centrifuges are compared using the **sigma factor (Σ)**.

$[$  
$\Sigma = \frac{Q}{v_g}$  
$]$

Where:

|Symbol|Meaning|
|---|---|
|Q|feed flow rate|
|vg|gravitational settling velocity|

Used to scale equipment between laboratory and industrial systems.

---

# 15. Coagulation and Flocculation

Microbial cells normally **do not stick together**.

Why?

1️⃣ Negative surface charge → repulsion  
2️⃣ Hydrophilic cell walls → water barrier  
3️⃣ Irregular surfaces → steric hindrance

So aggregation is difficult.

---

# 16. How Aggregation Is Induced

Aggregation can occur by:

1️⃣ **Charge neutralization**  
2️⃣ **Reducing hydrophilicity**  
3️⃣ **Polymer bridging**

The diagram on **page 19** shows polymer chains connecting cells to form flocs.

---

# 17. Difference Between Coagulation and Flocculation

|Process|Type|Mechanism|
|---|---|---|
|**Coagulation**|Chemical|neutralizes charges|
|**Flocculation**|Physical|particles aggregate|

---

### Coagulation agents

• alum  
• lime  
• iron salts

---

### Flocculating agents

• polyacrylamide  
• guar gum

Flocculation forms **large particles that settle easily**.

---

# Ultimate 1-Minute Summary

Centrifugation = **accelerated sedimentation using centrifugal force**

Key equation:

$[$  
$F_c = m r \omega^2$  
$]$

Types of centrifuges:

• laboratory centrifuge  
• tubular bowl centrifuge  
• basket centrifuge  
• ultracentrifuge

Coagulation & flocculation:

Methods to **aggregate cells before separation**.

---

# Cell Disruption

(Bioprocess Engineering Notes)

---

# 1. Where Cell Disruption Fits in Downstream Processing

After fermentation, product recovery usually follows these stages:

1️⃣ Removal of solids  
2️⃣ Primary isolation  
3️⃣ Purification & concentration  
4️⃣ Final product isolation

But if the product is **inside the cells**, we must first **break the cells open**.

Example intracellular products:

• enzymes  
• recombinant proteins  
• DNA / RNA

These remain trapped inside the **cell wall**, so disruption is necessary.

---

# 2. When Cell Disruption Is Needed

Two cases exist.

### Extracellular products

Examples:

• ethanol  
• citric acid

Product is secreted outside the cell.

So we only need:

**filtration or centrifugation**

---

### Intracellular products

Examples:

• enzymes  
• recombinant proteins

Product remains **inside cells**.

So we must:

**break cell wall → release product**

This step is called **cell disruption**.

---

# 3. Types of Cell Disruption

The diagram on **page 4** divides the methods into two main categories.

### Mechanical methods

Use physical forces.

Examples:

• bead mill  
• high-pressure homogenization  
• ultrasonication  
• press methods

---

### Non-mechanical methods

Use chemicals or biological agents.

Examples:

• enzymes  
• detergents  
• osmotic shock  
• solvents

---

# 4. Mechanical Cell Disruption Methods

Mechanical methods are **most common in industry**.

Because:

• scalable  
• efficient  
• no chemical contamination.

---

# 5. Liquid Shear (Homogenization)

Cells are broken by forcing them through **a narrow gap under pressure**.

This causes **shear stress** that ruptures cell membranes.

Examples of homogenizers:

### 1. Dounce homogenizer

Manual pestle inside glass tube.

### 2. Potter-Elvehjem homogenizer

PTFE pestle with mechanical rotation.

### 3. French Press

The **most powerful** method.

Cells are pushed through a tiny orifice using **very high pressure**.

Only **two passes** usually required for lysis.

---

# 6. Solid Shear (Pressure Extrusion)

Frozen cells are forced through a **small opening**.

Equipment used:

• Hughes press  
• X-press

Working principle:

Cell disruption occurs due to:

1️⃣ shear forces  
2️⃣ ice crystal formation

Efficiency:

Up to **90% disruption** with one pass for yeast.

Good for:

**temperature-sensitive products**.

---

# 7. Freeze-Thaw Method

Simple but slow.

Process:

1️⃣ Freeze cell suspension  
2️⃣ Ice crystals form inside cells  
3️⃣ Thawing causes rupture

Because:

Ice expands during freezing → damages cell membranes.

Used for:

• enzyme extraction  
• yeast cells.

But:

Low efficiency → often combined with other methods.

---

# 8. Bead Mill / Abrasive Agitation

One of the **most common industrial methods**.

Working principle:

Cells collide with **small beads** that are rapidly agitated.

Important parameters:

• bead size  
• agitator speed  
• cell concentration  
• bead loading

Typical conditions:

• bead loading: **80–85% chamber volume**  
• agitator speed: **1500–2250 rpm**.

Bead size depends on cell type:

|Cell type|Bead size|
|---|---|
|Yeast|>0.5 mm|
|Bacteria|<0.5 mm|

---

# 9. Ultrasonication

Uses **high frequency sound waves (~20 kHz)**.

These waves create **cavitation bubbles** in liquid.

When bubbles collapse → shock waves → cell rupture.

The diagram on **page 13** shows the cavitation cycle:

1️⃣ bubble formation  
2️⃣ bubble growth  
3️⃣ collapse → energy release

This energy disrupts cells.

---

### Time required

|Organism|Time|
|---|---|
|Bacteria|30–180 sec|
|Yeast|2–10 min|

---

### Drawbacks

• high energy consumption  
• heating of sample  
• probe wear

Therefore:

Mostly used for **lab-scale applications**.

---

# 10. Types of Sonication

## Direct Sonication

Probe inserted **directly into sample**.

Advantages:

• high energy  
• fast processing

But contamination is possible.

---

## Indirect Sonication

Probe does **not touch sample**.

Energy transferred through water bath.

Advantages:

• sterile samples  
• reduced contamination.

---

# 11. Osmotic Shock

Cells are exposed to sudden **osmotic pressure changes**.

Process:

1️⃣ Cells placed in **high salt solution**  
2️⃣ Suddenly moved to **low salt solution**

Water rushes into cells → pressure increases → cell bursts.

---

### Limitations

• requires large salt amounts  
• low efficiency

So rarely used industrially.

---

# 12. Chemical Cell Disruption

## Detergents

Detergents destroy cell membranes.

Common examples:

• SDS (anionic detergent)  
• Triton X-100 (nonionic detergent)  
• Ethyl trimethyl ammonium bromide (cationic detergent)

They disrupt:

• protein-protein interactions  
• lipid membranes.

---

### Disadvantages

• proteins may denature  
• purification becomes difficult

So limited industrial use.

---

# 13. Solvent Treatment

Solvents dissolve membrane lipids.

Examples:

• alcohols  
• dimethyl sulfoxide (DMSO)  
• methyl ethyl ketone  
• toluene

Result:

Membrane loses structure → intracellular contents released.

---

### Problems

• expensive  
• proteins may denature

Therefore rarely used at large scale.

---

# 14. Enzymatic Cell Disruption

Very **gentle method**.

Uses enzymes that degrade cell walls.

Examples:

|Organism|Enzyme|
|---|---|
|Gram-positive bacteria|Lysozyme|
|Yeast/fungi|Zymolyase|
|Plant biomass|Cellulases|

Example:

Lysozyme breaks **β-1,4 glycosidic bonds in peptidoglycan**.

---

### Advantages

• gentle  
• preserves protein activity

### Disadvantages

• expensive  
• difficult for large-scale production

---

# Ultimate 1-Minute Summary

Cell disruption is required when the **product is intracellular**.

Two main approaches:

### Mechanical

• homogenization  
• bead mill  
• ultrasonication  
• freeze-thaw

### Chemical / Biological

• detergents  
• solvents  
• enzymes  
• osmotic shock

Industrial processes prefer **mechanical methods**.

---

Professor honesty moment:

This chapter looks scary, but it’s basically:

**“How many ways can we break open a cell?”**

Answer:

1️⃣ smash it  
2️⃣ shake it  
3️⃣ blast it with sound  
4️⃣ dissolve its membrane  
5️⃣ trick it with osmotic pressure  
6️⃣ digest it with enzymes

That’s literally the entire chapter.

---


# Precipitation (Bioprocess Engineering Notes)

---

# 1. What Precipitation Means

Precipitation is a **physicochemical method used to convert a soluble molecule into an insoluble form** so that it can be separated by filtration or centrifugation.

Basic idea:

Soluble protein → add precipitating agent → protein aggregates → **precipitate forms**

Then we separate:

• precipitate (solid)  
• supernatant (liquid)

The diagram on **page 2** shows this sequence clearly: sample + precipitating agent → precipitate formation → separation via centrifugation.

---

# 2. Why Precipitation Is Used

In downstream processing precipitation helps to:

• concentrate proteins  
• partially purify biomolecules  
• remove impurities

Typical targets:

• enzymes  
• antibodies  
• recombinant proteins.

---

# 3. Factors Affecting Protein Solubility

Protein precipitation happens because **solubility changes**.

Main variables:

1️⃣ Temperature  
2️⃣ pH  
3️⃣ Salt concentration  
4️⃣ Organic solvents.

---

# 4. Effect of Temperature

Solubility generally **increases with temperature**.

Reason:

Higher kinetic energy breaks weak protein interactions.

But at very low temperatures:

Proteins may precipitate due to **freezing and concentration effects**.

The graph on **page 3** shows solubility increasing with temperature.

---

# 5. Effect of pH

Protein solubility strongly depends on **pH**.

Most proteins have **isoelectric point (pI)** between:

**pH 4 – 6**.

---

## At Isoelectric Point (pI)

Net charge on protein = **0**

Consequences:

• electrostatic repulsion disappears  
• protein molecules attract each other  
• aggregation occurs

Result:

**minimum solubility → precipitation**

The graph on **page 4** shows solubility minimum at the isoelectric point.

---

## At Extreme pH

Proteins become strongly charged.

Effects:

• strong electrostatic repulsion  
• increased interaction with water

Result:

**higher solubility**.

---

# 6. Intermolecular Forces in Protein Solutions

Proteins interact through:

• electrostatic forces  
• hydrophobic interactions  
• van der Waals forces

When these attractive forces dominate → **precipitation occurs**.

---

# 7. Electrical Double Layer Around Proteins

Proteins in solution often carry **negative charge**.

They attract positive ions forming a **Stern layer**.

Outside this layer is another region called the **electrical double layer**.

When two proteins approach:

• double layers repel each other  
• aggregation is prevented

Water molecules also form a **hydration shell**, which stabilizes proteins.

Precipitation happens when these protective effects are disrupted.

---

# 8. Salting Out of Proteins

One of the most common precipitation methods.

Mechanism:

Increase **ionic strength** by adding salt.

Common salt used:

**Ammonium sulfate**

---

### Cohn Equation

Protein solubility depends on ionic strength:

[  
$\log S = \beta - KI$  
$]$

Where:

|Symbol|Meaning|
|---|---|
|S|protein solubility|
|I|ionic strength|
|β, K|constants|

As ionic strength increases:

Solubility **decreases**.

---

### Ionic Strength Formula

[  
$I = \frac{1}{2} \sum z_i^2 C_i$  
]

Where:

|Symbol|Meaning|
|---|---|
|z|ionic charge|
|C|ion concentration|

---

### Simplified Case (Single Salt)

If only one salt is used:

[  
$\log S = \beta_s - K_s C_s$  
]

Where (C_s) = salt concentration.

---

# 9. Why Salting Out Works

Salt ions compete with proteins for water molecules.

Consequences:

• hydration layer around proteins decreases  
• hydrophobic regions become exposed  
• proteins aggregate

Result:

**protein precipitation**.

---

# 10. Hofmeister Series

Salts have different precipitation strengths.

The diagram on **page 10** lists ions according to their ability to promote salting out.

Example:

Strong salting-out anions:

[  
$PO_4^{3-} > SO_4^{2-} > CH_3COO^- > Cl^-$  
]

---

# 11. Properties of Good Precipitating Salts

A suitable salt should:

• be inexpensive  
• be highly soluble  
• produce minimal heat of dissolution  
• not denature proteins.

After precipitation, the salt must be removed by **dialysis**.

---

# 12. Other Precipitation Methods

## Organic Solvent Precipitation

Examples:

• ethanol  
• acetone

Mechanism:

Solvent reduces the **dielectric constant** of the solution.

This increases electrostatic attraction between proteins → precipitation.

---

## Isoelectric Precipitation

Adjust pH to protein's **pI**.

At this point:

• electrostatic repulsion disappears  
• hydrophobic interactions dominate

Result:

**precipitation occurs**.

---

## Polymer Precipitation

Polymers like:

• PEG  
• Dextran

reduce the amount of water available to proteins.

This forces proteins to aggregate.

---

# Ultimate 30-Second Summary

Precipitation = converting soluble proteins into **insoluble aggregates**.

Main methods:

1️⃣ pH adjustment (isoelectric precipitation)  
2️⃣ salt addition (salting out)  
3️⃣ organic solvents  
4️⃣ polymers

Most industrial processes use:

**ammonium sulfate salting-out**.

---
