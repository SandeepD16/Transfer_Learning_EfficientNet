<img width="846" height="547" alt="Train Vs Validation" src="https://github.com/user-attachments/assets/fdd960e0-d98f-4165-b82b-bf35d9d961c2" /><img width="846" height="547" alt="Train Vs Validation" src="https://github.com/user-attachments/assets/e4c10747-9eda-4fbc-8a1a-65a44024bf58" /># Transfer Learning vs Training From Scratch on CIFAR-10

This project presents a **comparative experimental study of image classification** using:
A CNN trained from scratch
Transfer learning with a frozen pre-trained backbone
Transfer learning with full fine-tuning

The goal is to **understand when and why transfer learning works**, rather than just applying it blindly.



# Motivation

Transfer learning is widely used in computer vision, but its effectiveness depends on:
- Dataset characteristics
- Domain similarity
- Fine-tuning strategy

This project investigates:
- Why freezing a pre-trained model may lead to low accuracy
- How fine-tuning improves performance dramatically
- The impact of domain adaptation on learned features

---

# Dataset

- CIFAR-10
- 60,000 RGB images
- Image size: 32 × 32
- 10 classes
- Images resized to **224 × 224** to match EfficientNet input requirements

---

# Model Architectures

# Baseline CNN (Training from Scratch)
- Convolution + Pooling layers
- Fully connected classifier
- Learns all features from random initialization

**Purpose:** Performance reference point

---

# Transfer Learning (Frozen Backbone)
- EfficientNetB0 pre-trained on ImageNet
- Backbone frozen
- Custom classifier layers added on top

**Purpose:** Feature extraction without adaptation

---

# Transfer Learning + Fine-Tuning
- Entire EfficientNet backbone unfrozen
- Very small learning rate
- End-to-end training

**Purpose:** Domain adaptation and feature refinement

---

# Experiments Performed

<img width="761" height="202" alt="image" src="https://github.com/user-attachments/assets/5e1bd13d-c4d2-4d33-a859-f690a01940c4" />




# Key Observations

- Frozen transfer learning performed poorly due to **domain mismatch** between ImageNet and CIFAR-10
- CIFAR-10 images are small and less complex compared to ImageNet
- Fine-tuning allowed the model to adapt both low-level and high-level features
- A small learning rate prevented catastrophic forgetting

These results highlight the **importance of controlled fine-tuning** in real-world applications.

---

# Visualizations

The notebook includes:
- Training vs validation accuracy curves
- Comparison between performance on test data by baseline and transfer learning models
- Confusion Matrix
-<img width="846" height="547" alt="Train Vs Validation" src="https://github.com/user-attachments/assets/d468d650-fef6-4ed1-baae-7903b6cbefa0" />
<img width="536" height="374" alt="test" src="https://github.com/user-attachments/assets/49d2110e-39c1-4ac8-8389-3eea44516d00" />
<img width="507" height="455" alt="baseline_CM" src="https://github.com/user-attachments/assets/1301e3b2-3822-42df-aaee-fe4be0976b6a" />
<img width="507" height="455" alt="TL_model_CM" src="https://github.com/user-attachments/assets/2409c07a-4809-4321-b828-d5dbfd2542fe" />





---

# Tools & Technologies

- Python
- TensorFlow / Keras
- EfficientNetB0
- Google Colab
- Matplotlib
- tf.data API

---

## ▶ How to Run

1. Open the notebook in **Google Colab**
2. Ensure GPU is enabled (`Runtime → Change runtime type → GPU`)
3. Run all cells sequentially

---



