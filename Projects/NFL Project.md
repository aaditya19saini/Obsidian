Based on my exploration, here's the recommended reading order:

---

## Recommended Learning Path

### 1. **`main.ipynb`** (START HERE)
**Purpose**: Initial exploration with two approaches
- **YOLOv3 pretrained**: Uses standard COCO weights to detect "person" class
- **Color matching**: Manual LAB color space approach to detect players by team colors
- **Why read first**: Shows the evolution from naive approaches

### 2. **`field_filter.ipynb`**
**Purpose**: Image preprocessing
- Filters out NFL logos, end zones, yard numbers
- Uses HSV color thresholding to isolate green field
- **Why read second**: Shows preprocessing techniques before feeding to model

### 3. **`test_vis.ipynb`**
**Purpose**: YOLOv8 training pipeline
- Downloads dataset from Roboflow
- Trains YOLOv8 on custom labeled NFL positions
- Uses `data.yaml` for class configuration
- **Why read third**: Core training workflow

### 4. **`WRYOLOCUSTOM.ipynb`**
**Purpose**: Alternative/custom training approach
- Similar training but different configurations
- **Why read fourth**: Compare different training setups

### 5. **`player_detection.ipynb`**
**Purpose**: Training with different dataset path (`NewWRData`)
- May have different split or labeling approach
- **Why read fifth**: Understand variations in training

### 6. **`newwr_test_vis.ipynb`**
**Purpose**: Inference/testing
- Loads trained model and runs predictions
- Visualizes results with bounding boxes
- **Why read last**: How to use the trained model

---

## Project Structure Summary

```
WR/
├── notebooks/         # All experimentation
├── scripts/           # Python scripts (e.g., filter_field.py)
├── images/            # Sample test images
└── docs/              # Documentation
```

**Dataset is NOT in repo** - You'll need to:
1. Create a Roboflow account
2. Download labeled dataset (YOLOv8 format)
3. Or label your own images using Roboflow

---

Would you like me to explain any specific notebook in detail, or do you want to start reproducing the project now?