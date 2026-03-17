# 🚗 Task 3 — Everyday Object Recognition

![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat&logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?style=flat&logo=keras)
![Dataset](https://img.shields.io/badge/Dataset-Natural--Images-green?style=flat)
![Colab](https://img.shields.io/badge/Google-Colab-yellow?style=flat&logo=googlecolab)

> Develop a CNN model to recognize everyday objects  
> and compare performance with and without data augmentation.

---

## 🎯 Objective

Build a CNN model capable of recognizing multiple
everyday object categories and experiment with
data augmentation, epoch count, and batch sizes
to achieve the highest possible accuracy.

---

## 📦 Dataset

| Detail | Info |
|--------|------|
| Source | [Natural Images — Kaggle](https://www.kaggle.com/datasets/prasunroy/natural-images) |
| Total Images | ~4,500 (5 classes) |
| Image Size | Resized to 128×128 |
| Format | JPG / PNG |
| Download | kagglehub |

### 🚗 Classes
```
Car  •  Motorbike  •  Airplane  •  Person  •  Dog
```

---

## 🏗️ Model Architecture
```
Input (128×128×3)
    → Conv2D(32,  3×3, ReLU)
    → MaxPooling2D
    → Conv2D(64,  3×3, ReLU)
    → MaxPooling2D
    → Conv2D(128, 3×3, ReLU)
    → MaxPooling2D
    → Flatten
    → Dense(256, ReLU)
    → Dropout(0.5)
    → Dense(5, Softmax)
```

---

## ⚙️ Configuration
```python
IMG_SIZE    = (128, 128)
NUM_CLASSES = 5
BATCH_SIZE  = 32
EPOCHS_LOW  = 10
EPOCHS_HIGH = 30
OPTIMIZER   = 'Adam'
LOSS        = 'categorical_crossentropy'
```

---

## 🧪 Experiments

### Experiment 1 — Without Augmentation (10 Epochs)
```
No image transformation
Batch Size : 32
Epochs     : 10
```

### Experiment 2 — Without Augmentation (30 Epochs)
```
No image transformation
Batch Size : 32
Epochs     : 30
```

### Experiment 3 — With Augmentation (30 Epochs)
```
Augmentation Settings:
    → Rotation      : ±30°
    → Horizontal Flip: True
    → Zoom          : 20%
    → Width Shift   : 20%
    → Height Shift  : 20%
    → Shear         : 20%
Batch Size : 32
Epochs     : 30
```

### Experiment 4 — Batch Size Comparison
```
Augmentation : ON
Epochs       : 15
Batch Sizes  : 16  →  32  →  64
```

---

## 📊 Results

### Main Experiments
| Experiment | Accuracy |
|------------|----------|
| No Augmentation (10 Epochs) | ~75% |
| No Augmentation (30 Epochs) | ~82% |
| With Augmentation (30 Epochs) | **~90%** 🏆 |

### Batch Size Comparison
| Batch Size | Accuracy |
|------------|----------|
| 16 | ~88% |
| 32 | ~86% |
| 64 | ~83% |

> 🏆 **Best Setup: With Augmentation + 30 Epochs (~90%)**

---

## 📈 Accuracy Comparison
```
No Aug  10 Epochs   ████████████████░░░░░░░░  ~75%
No Aug  30 Epochs   ████████████████████░░░░  ~82%
With Aug 30 Epochs  ██████████████████████░░  ~90% 🏆
```

---

## 🔑 Key Concepts Used

| Concept | Purpose |
|---------|---------|
| Conv2D | Extracts object features |
| MaxPooling | Reduces spatial dimensions |
| ReLU | Introduces non-linearity |
| Dropout | Prevents overfitting |
| Data Augmentation | Increases data variety |
| Softmax | Outputs 5 class probabilities |

---

## 🔄 Augmentation Effect
```
Without Augmentation:
Model sees same images every epoch
→ Memorizes training data
→ Poor on new images ❌

With Augmentation:
Model sees different versions each epoch
→ Learns robust features
→ Better on new images ✅

Improvement: ~15% accuracy gain
```

---

## 🚀 How to Run

**Step 1 —** Open `task3_object_cnn.ipynb` in Google Colab

**Step 2 —** Enable GPU
```
Runtime → Change runtime type → T4 GPU
```

**Step 3 —** Run all cells in order
```
Cell 1  → Install & import libraries
Cell 2  → Download dataset
Cell 3  → Check folder names
Cell 4  → Copy to writable location
Cell 5  → Count images per class
Cell 6  → Preview sample images
Cell 7  → Configuration
Cell 8  → Data generator function
Cell 9  → Visualize augmentation
Cell 10 → Build CNN model
Cell 11 → Experiment 1 (No Aug 10 Epochs)
Cell 12 → Experiment 2 (No Aug 30 Epochs)
Cell 13 → Experiment 3 (With Aug 30 Epochs)
Cell 14 → Experiment 4 (Batch comparison)
Cell 15 → Plot training curves
Cell 16 → Final comparison table
Cell 17 → Test predictions
```

---

## 📁 Folder Structure
```
Task3-Object-Recognition/
│
├── task3_object_cnn.ipynb   ← main notebook
└── README.md                ← this file
```

---

## 📸 Sample Output
```
Input  → Car image (128×128)
Output → [Car: 91%, Motorbike: 4%,
          Airplane: 2%, Person: 2%, Dog: 1%]
         Predicted: 🚗 CAR
```

---

## 💡 Observations

- Augmentation improved accuracy by ~15%
- More epochs consistently improved results
- Smaller batch size (16) gave better accuracy
- Objects are visually distinct → high accuracy
- 30 epochs was optimal before overfitting

---

## ⚡ Comparison With Other Tasks
```
Task 1 → 4 classes  (animals)    → ~76%
Task 2 → 10 classes (clothing)   → ~93%
Task 3 → 5 classes  (objects)    → ~90%

Task 3 key difference:
Focus on EXPERIMENTS not just architectures
Augmentation vs No Augmentation
Different Epochs & Batch Sizes compared
```

---

## 📜 License
[MIT License](../LICENSE)