**Non-max suppression** is a post-processing technique used in object detection to get rid of unnecessary, redundant bounding boxes that predict the exact same object.

When an object detection model (like a CNN) slides across an image, it often detects the same object multiple times at slightly different positions. Non-max suppression cleans up these duplicate predictions through a specific step-by-step process:

1. **Filter by threshold:** First, the system looks at the "objectness score" (the model's estimated probability that an object is actually present) for every bounding box. It deletes all bounding boxes where this score falls below a certain threshold.
2. **Select the maximum:** Next, it identifies the bounding box that has the absolute highest objectness score.
3. **Suppress overlaps:** It then deletes any other bounding boxes that overlap heavily with this "maximum" bounding box (for example, removing boxes that share an Intersection over Union, or IoU, greater than 60%).
4. **Repeat:** It repeats this process for the remaining bounding boxes until there are no more overlapping, redundant boxes left to get rid of.

---

**Concise Answer:** **Non-max suppression** is an algorithm used in computer vision to eliminate duplicate bounding boxes around the same object. It works by deleting boxes with low probability scores, keeping the box with the highest score, and suppressing (deleting) any other boxes that heavily overlap with that top-scoring box. It repeats this until only the most accurate bounding boxes remain.