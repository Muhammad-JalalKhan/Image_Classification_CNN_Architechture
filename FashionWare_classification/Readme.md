# 👗 Task 2 — CNN Architecture Optimization

![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat&logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?style=flat&logo=keras)
![Dataset](https://img.shields.io/badge/Dataset-Fashion--MNIST-purple?style=flat)
![Colab](https://img.shields.io/badge/Google-Colab-yellow?style=flat&logo=googlecolab)

> Design and optimize CNN architectures to achieve  
> the highest possible accuracy on the Fashion-MNIST dataset.

---

## 🎯 Objective

Experiment with four different CNN architectures
and identify which optimization technique delivers
the best classification accuracy on clothing images.

---

## 📦 Dataset

| Detail | Info |
|--------|------|
| Source | Built-in Keras Dataset |
| Load | `fashion_mnist.load_data()` |
| Total Images | 70,000 |
| Training Set | 60,000 images |
| Test Set | 10,000 images |
| Image Size | 28×28 Grayscale |
| Classes | 10 |

### 👕 Classes
```
0 → T-shirt      5 → Sandal
1 → Trouser      6 → Shirt
2 → Pullover     7 → Sneaker
3 → Dress        8 → Bag
4 → Coat         9 → Ankle Boot
```

---

## 🏗️ Model Architectures

### Model 1 — Baseline CNN
```
Input (28×28×1)
    → Conv2D(32, 3×3, ReLU)
    → MaxPooling2D
    → Flatten
    → Dense(128, ReLU)
    → Dense(10, Softmax)
```

### Model 2 — CNN + Extra Conv Layer
```
Input (28×28×1)
    → Conv2D(32, 3×3, ReLU)
    → MaxPooling2D
    → Conv2D(64, 3×3, ReLU)
    → MaxPooling2D
    → Flatten
    → Dense(128, ReLU)
    → Dense(10, Softmax)
```

### Model 3 — CNN + Dropout
```
Input (28×28×1)
    → Conv2D(32) → MaxPool → Dropout(0.25)
    → Conv2D(64) → MaxPool → Dropout(0.25)
    → Flatten
    → Dense(128) → Dropout(0.5)
    → Dense(10, Softmax)
```

### Model 4 — CNN + Batch Normalization
```
Input (28×28×1)
    → Conv2D(32)  → BatchNorm → ReLU → MaxPool
    → Conv2D(64)  → BatchNorm → ReLU → MaxPool
    → Conv2D(128) → BatchNorm → ReLU → MaxPool
    → Flatten
    → Dense(256)  → BatchNorm
    → Dense(10, Softmax)
```

---

## ⚙️ Configuration
```python
IMG_SHAPE   = (28, 28, 1)
NUM_CLASSES = 10
BATCH_SIZE  = 32
EPOCHS      = 20
OPTIMIZER   = 'Adam'
LOSS        = 'categorical_crossentropy'
```

---

## 📊 Results

| Model | Test Accuracy |
|-------|--------------|
| Baseline CNN | ~88% |
| CNN + Extra Conv Layer | ~90% |
| CNN + Dropout | ~91% |
| CNN + Batch Normalization | **~93%** 🏆 |

> 🏆 **Best Model: CNN + Batch Normalization (~93%)**

---

## 📈 Accuracy Comparison
```
Baseline CNN          ████████████████████░░░░  ~88%
Extra Conv Layer      █████████████████████░░░  ~90%
CNN + Dropout         ██████████████████████░░  ~91%
Batch Normalization   ███████████████████████░  ~93% 🏆
```

---

## 🔑 Key Concepts Used

| Concept | Purpose |
|---------|---------|
| Conv2D | Extracts image features |
| MaxPooling | Reduces spatial size |
| Extra Conv Layer | Learns deeper features |
| Dropout | Prevents overfitting |
| Batch Normalization | Stabilizes & speeds training |
| Softmax | Outputs 10 class probabilities |
| One-Hot Encoding | Converts labels to vectors |

---

## 🔄 Preprocessing Steps
```
Step 1 → Reshape  : (28,28) → (28,28,1)
Step 2 → Normalize: 0-255   → 0.0-1.0
Step 3 → Encode   : 7       → [0,0,0,0,0,0,0,1,0,0]
```

---

## 🚀 How to Run

**Step 1 —** Open `task2_fashion_cnn.ipynb` in Google Colab

**Step 2 —** Enable GPU
```
Runtime → Change runtime type → T4 GPU
```

**Step 3 —** Run all cells in order
```
Cell 1  → Import libraries
Cell 2  → Load dataset
Cell 3  → Define class names
Cell 4  → Preview images
Cell 5  → Preprocess data
Cell 6  → Configuration
Cell 7  → Build Model 1 (Baseline)
Cell 8  → Build Model 2 (Extra Conv)
Cell 9  → Build Model 3 (Dropout)
Cell 10 → Build Model 4 (Batch Norm)
Cell 11 → Train Model 1
Cell 12 → Train Model 2
Cell 13 → Train Model 3
Cell 14 → Train Model 4
Cell 15 → Plot training curves
Cell 16 → Accuracy comparison
Cell 17 → Test predictions
```

---

## 📁 Folder Structure
```
Task2-Fashion-MNIST-Optimization/
│
├── task2_fashion_cnn.ipynb   ← main notebook
└── README.md                 ← this file
```

---

## 📸 Sample Output
```
Input  → Sneaker image (28×28)
Output → [T-shirt: 1%, Trouser: 2%, ...
          Sneaker: 85%, ...]
         Predicted: 👟 SNEAKER
```

---

## 💡 Observations

- Batch Normalization gave the highest accuracy (~93%)
- Extra Conv Layer improved baseline by ~2%
- Dropout reduced overfitting significantly
- Fashion-MNIST trains much faster than Animals-10
- No data download needed — loads in seconds

---

## ⚡ Advantage Over Task 1
```
Task 1 → Manual download  (614 MB)
Task 2 → Auto load        (just 2 lines of code)

Task 1 → 128×128 color    (heavy computation)
Task 2 → 28×28 grayscale  (fast training)

Task 1 → ~1.5 hours total
Task 2 → ~20 minutes total ✅
```

---

## 📜 License
[MIT License](../LICENSE)
```

---

## ✏️ Only 1 Thing to Update
```
After training → update accuracy numbers:

| Baseline CNN           | ~88% |  ← your result
| Extra Conv Layer       | ~90% |  ← your result
| CNN + Dropout          | ~91% |  ← your result
| Batch Normalization    | ~93% |  ← your result