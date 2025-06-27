# 🗽 AMERICAN SIGN LANGUAGE DETECTION SYSTEM

---

## 📖 Introduction

This project aimed to build a Convolutional Neural Network (CNN) model capable of recognizing American Sign Language (ASL) alphabets from hand gesture images. The broader goal is to enable real-time translation of ASL into written or spoken language, reducing communication barriers for the deaf and hard-of-hearing communities.

With the prevalence of depression and isolation in the deaf community, largely due to communication challenges, this project proposes a vision for inclusive communication technology using affordable devices like webcams.

---

## 🧱 Software Architecture

The software system was structured into three main components:

### 1. **Data Processing**
- Scripts: `load_data.py`, `process_data.py`
- Tasks: Load raw images, resize, apply filters, ZCA whitening
- Output: Preprocessed datasets split into training, validation, and test sets

### 2. **Training**
- Script: `train_model.py`
- Framework: PyTorch
- Features: Uses config file to define hyperparameters (learning rate, epochs, etc.)
- Optimizer: Adam (with CrossEntropy Loss)
- Output: Best model checkpoints, training/validation plots

### 3. **Classify Gesture**
- Script: `test_data.py`
- Loads a new image and runs it through the same preprocessing and trained model to classify the ASL letter

---

## 📊 Dataset Information

### 🔹 Source:
- **Kaggle ASL Alphabet Dataset** by Akash (87,000 images, 29 classes including A–Z, space, delete, nothing)

### 🔹 Custom Test Sets:
- Collected using laptop webcams under various conditions (lighting, background, hand orientation)

### 🔹 Preprocessing:
- Image enhancement: contrast, brightness, sharpness
- Edge enhancement for finger distinction
- **ZCA Whitening**: To remove redundancy and expose higher-level image patterns

---

## 🧠 Model Architecture

### 📌 Baseline CNN (from paper):
- 3 convolutional blocks with ReLU, MaxPooling, and Dropout
- Followed by Fully Connected Layers

### 📌 Custom Model:
- Smaller architecture for faster training
- Varied kernel sizes (5x5 to 10x10) to learn both local and abstract features
- Final FC layers to classify into 29 classes

---

## 📈 Model Performance

### 🔧 Optimizer:
- Switched from Adam to SGD initially due to convergence issues
- Later restored Adam with reduced learning rate for better convergence

### 📊 Effect of Dataset Size:
| Samples per Class | Validation Accuracy |
|-------------------|---------------------|
| 25                | 27.3%               |
| 50                | 34.8%               |
| 100               | 46.1%               |
| 200               | 58.2%               |

### 📈 Final Accuracy:
- **Unfiltered Model**: 62.1% (Kaggle Test), 8.03% (Custom Test)
- **Filtered Model**: 76.8% (Kaggle Test), 27.1% (Custom Test)
- Best Validation Accuracy: **77.25% at epoch 24**

---

## 📷 Results

- Plots of training/validation accuracy and loss show filtering and ZCA whitening improved performance.
- Confusion matrix highlighted confusion between visually similar gestures (e.g., V vs W).

---

## ⚖️ Ethical Considerations

- Technology should not shift the burden of communication solely onto the deaf community.
- Importance of a diverse dataset to avoid bias against users of different skin tones or environments.

---

## 🔄 Reflections & Learnings

### ✔️ Key Takeaways:
- Start training early to uncover issues in hyperparameters or architecture
- Optimizer choice critically impacts training efficiency
- Dataset size and quality directly influence generalization
- Preprocessing like ZCA whitening and image enhancement significantly improves results

---

## 🧾 Conclusion

This project was a comprehensive exercise in end-to-end machine learning: from data preprocessing, model design, and tuning to evaluation. The solution is a step forward in making sign language recognition more accessible and practical using everyday hardware. It also offered deep insights into CNN behavior, optimization strategies, and responsible AI design.

