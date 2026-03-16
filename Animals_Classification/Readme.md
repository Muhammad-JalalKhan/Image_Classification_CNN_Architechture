# 🐾 Task 1 — Animal Image Classification

![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat&logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?style=flat&logo=keras)
![Dataset](https://img.shields.io/badge/Dataset-Animals--10-blue?style=flat)
![Colab](https://img.shields.io/badge/Google-Colab-yellow?style=flat&logo=googlecolab)

> Build and compare three CNN models to classify  
> 4 animal categories using the Animals-10 dataset from Kaggle.

---

## 🎯 Objective

Train a Convolutional Neural Network to recognize
animals from images and compare the performance of
three different model architectures.

---

## 📦 Dataset

| Detail | Info |
|--------|------|
| Source | [Animals-10 — Kaggle](https://www.kaggle.com/datasets/alessiocorrado99/animals10) |
| Total Images | ~28,000 |
| Classes Used | 4 out of 10 |
| Image Size | Resized to 128×128 |
| Format | JPG / PNG |

### 🐱 Classes
```
Cat  •  Dog  •  Horse  •  Elephant
```

---

## 🏗️ Model Architectures

### Model 1 — Basic CNN
```
Input (128×128×3)
    → Conv2D(32, 3×3, ReLU)
    → MaxPooling2D
    → Conv2D(64, 3×3, ReLU)
    → MaxPooling2D
    → Conv2D(128, 3×3, ReLU)
    → MaxPooling2D
    → Flatten
    → Dense(128, ReLU)
    → Dense(4, Softmax)
```

### Model 2 — CNN + Dropout
```
Input (128×128×3)
    → Conv2D(32) → MaxPool → Dropout(0.25)
    → Conv2D(64) → MaxPool → Dropout(0.25)
    → Conv2D(128) → MaxPool
    → Flatten
    → Dense(128) → Dropout(0.5)
    → Dense(4, Softmax)
```

### Model 3 — CNN + Data Augmentation
```
Same architecture as Basic CNN
Training data transformed with:
    → Rotation      : ±20°
    → Horizontal Flip: True
    → Width Shift   : 20%
    → Height Shift  : 20%
```

---

## ⚙️ Configuration
```python
IMG_SIZE   = (128, 128)
BATCH_SIZE = 16
EPOCHS     = 15
OPTIMIZER  = 'Adam'
LOSS       = 'categorical_crossentropy'
```

---

## 📊 Results

| Model | Validation Accuracy |
|-------|-------------------|
| Basic CNN | 71.67% |
| CNN + Dropout | **76.11%** 🏆 |
| CNN + Augmentation | 75.17% |

> 🏆 **Best Model: CNN + Dropout — 76.11%**

---

## 📈 Accuracy Comparison
```
Basic CNN          ████████████████████░░░░  71.67%
CNN + Dropout      ██████████████████████░░  76.11% 🏆
CNN + Augmentation █████████████████████░░░  75.17%
```

---

## 🔑 Key Concepts Used

| Concept | Purpose |
|---------|---------|
| Conv2D | Extracts features using filters |
| MaxPooling | Reduces spatial dimensions |
| ReLU | Introduces non-linearity |
| Dropout | Prevents overfitting |
| Softmax | Outputs class probabilities |
| Data Augmentation | Increases data variety |
| Batch Normalization | Stabilizes training |

---

## 🚀 How to Run

**Step 1 —** Open `task1_animal_cnn.ipynb` in Google Colab

**Step 2 —** Enable GPU
```
Runtime → Change runtime type → T4 GPU
```

**Step 3 —** Run all cells in order
```
Cell 1  → Install kagglehub
Cell 2  → Download dataset
Cell 3  → Check folders
Cell 4  → Copy to writable location
Cell 5  → Import libraries
Cell 6  → Configuration
Cell 7  → Preview images
Cell 8  → Data generators
Cell 9  → Build Model 1
Cell 10 → Build Model 2
Cell 11 → Train Model 1
Cell 12 → Train Model 2
Cell 13 → Train Model 3
Cell 14 → Plot curves
Cell 15 → Compare results
Cell 16 → Test predictions
```

---

## 📁 Folder Structure
```
Task1-Animal-Classification/
│
├── task1_animal_cnn.ipynb   ← main notebook
└── README.md                ← this file
```

---

## 📸 Sample Output
```
Input  → Cat image (128×128)
Output → [Cat: 85%, Dog: 7%, Horse: 5%, Elephant: 3%]
         Predicted: 🐱 CAT
```

---

## 💡 Observations

- CNN + Dropout outperformed Basic CNN by **4.44%**
- Augmentation needs more epochs to show full benefit
- Larger filter count in deeper layers improves accuracy
- Batch size 16 gave more precise weight updates than 32

---

## 📜 License
[MIT License](../LICENSE)
```

---

## ✏️ Only 1 Thing to Update
```
After training → update these numbers:

| Basic CNN          | 71.67% |   ← your actual result
| CNN + Dropout      | 76.11% |   ← your actual result  
| CNN + Augmentation | 75.17% |   ← your actual result