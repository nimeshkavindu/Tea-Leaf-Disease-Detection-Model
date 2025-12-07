# 🍃 Tea Leaf Disease Detection

An end-to-end Deep Learning application that classifies tea leaf diseases with **86% accuracy**. 
Built using **EfficientNetB0**, optimized with transfer learning.

<img width="663" height="798" alt="image" src="https://github.com/user-attachments/assets/68f97651-26ef-4029-ac99-df8b95251250" />
<img width="759" height="608" alt="image" src="https://github.com/user-attachments/assets/ccc53efd-9a6a-4b1a-838c-c6040fa8dbfb" />

## 📋 Project Overview

Tea cultivation is susceptible to various diseases that are difficult to distinguish visually. This project automates the detection of **7 distinct classes** of tea leaf conditions, helping to prevent crop loss through early diagnosis.

I initially experimented with **MobileNetV2** but found it struggled to distinguish between textured diseases like *Brown Blight* and *Tea Algal Leaf Spot* (79% accuracy ceiling). 

Migrating to **EfficientNetB0** and implementing aggressive **Class Weighting** resolved these ambiguity issues, boosting recall on minority classes and raising overall accuracy to **86%**.

## 📊 Performance & Results

* **Final Accuracy:** 85.49% (Validation)
* **Loss:** 0.41 (Converged)
* **Overfitting:** None (< 0.3% gap between Train/Val accuracy)

<img width="514" height="247" alt="image" src="https://github.com/user-attachments/assets/015a7149-574c-43da-8674-bc2a83978050" />


### Confusion Matrix
The model successfully distinguishes between visually similar classes (Brown Blight vs. Algal Spot).

<img width="918" height="831" alt="image" src="https://github.com/user-attachments/assets/af670388-caa8-4b78-bbe9-f69bd0e6f4a7" />

### Training Curves
Training and Validation loss converged perfectly over 100 epochs.

<img width="671" height="682" alt="image" src="https://github.com/user-attachments/assets/60187495-b132-41c8-ab0d-abe95da9e6ab" />


## 🛠️ Tech Stack

* **Core:** Python 3.10+, TensorFlow/Keras
* **Model:** EfficientNetB0 (Transfer Learning)
* **Data Processing:** NumPy, Pandas, Pillow
* **Visualization:** Matplotlib, Seaborn
* **Deployment:** Streamlit

## 📂 Dataset Details

* **Source:** [TeaLeafBD Dataset](https://www.kaggle.com/datasets/bmshahriaalam/tealeafbd-tea-leaf-disease-detection)
* **Total Images:** ~5,200 images
* **Classes (7):**
    1.  Red Spider
    2.  Brown Blight
    3.  Gray Blight
    4.  Tea Algal Leaf Spot
    5.  Helopeltis
    6.  Green Mirid Bug
    7.  Healthy Leaf

## ⚙️ Training Configuration

The model was trained in a two-stage process to ensure feature retention while adapting to fine-grained textures.

| Parameter | Value |
| :--- | :--- |
| **Base Model** | EfficientNetB0 (ImageNet weights) |
| **Input Shape** | (224, 224, 3) |
| **Batch Size** | 32 |
| **Total Epochs** | 100 (20 Frozen + 80 Fine-Tuning) |
| **Optimizer** | Adam |
| **Learning Rate** | 1e-5 (Fine-Tuning Phase) |
| **Regularization** | Dropout (0.3), Data Augmentation |
| **Loss Function** | Sparse Categorical Crossentropy |

## 🧠 Key Optimization Techniques

1.  **Class Weights:** Calculated and applied class weights during training to penalize the model heavily for missing minority classes (e.g., Algal Leaf Spot).
2.  **Data Augmentation:** Applied Random Rotation, Zoom, and Contrast adjustments to make the model robust against lighting and orientation changes.
3.  **Fine-Tuning:** Unfroze the top 30 layers of EfficientNetB0 to allow the model to learn specific tea-leaf texture features.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📜 License

[MIT](https://choosealicense.com/licenses/mit/)
