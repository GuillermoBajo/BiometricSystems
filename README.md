# Development and Design of a Facial Recognition System

---

## Introduction

This project focuses on developing a facial recognition system for Sapienza University to improve access control and security. The system utilizes state-of-the-art deep learning techniques to identify individuals with high accuracy and efficiency.

---

## Model Architecture

I implemented the **InceptionResNetV1** architecture, pre-trained on the **VGGFace2** dataset, to extract 512-dimensional embeddings for each face. These embeddings provide a robust representation of facial features, allowing for reliable recognition even in varying conditions, such as changes in lighting or pose.

---

## Techniques and Optimization

### Pretrained Model

I opted for a pretrained model trained on **VGGFace2** due to computational and dataset limitations. This decision allowed me to leverage a robust, generalized model while saving time and resources.

Key benefits of using VGGFace2:

- **Large dataset**: Over 3 million labeled images with diverse conditions.
- **Better generalization**: Improved performance for varied lighting, angles, and ethnic diversity.

### InceptionResNetV1

The InceptionResNetV1 model proved ideal for our system due to its:

- Stability in Google Colab.
- Pretrained weights that required fewer configurations.
- Robustness in handling real-world image variability.

### CNNs vs. Traditional Methods

Unlike traditional methods like PCA and LDA, **Convolutional Neural Networks (CNNs)** excel in:

- Learning hierarchical features directly from data.
- Scalability through data augmentation and transfer learning.
- Robustness against transformations like rotation, scaling, and noise.

### Triplet Loss

I initially considered training with **Triplet Loss**, which ensures embeddings of the same individual are close, while those of different individuals are far apart. However, I decided against it due to my use of a pretrained model, which already provided well-separated embeddings.

### Normalization

We applied **L2 normalization** to standardize embedding magnitudes. This ensures:

- Consistent comparison of embeddings using metrics like cosine similarity.
- Improved model generalization and reliability.

### Embedding Dimensionality

The model generates **512-dimensional embeddings**, striking a balance between detail and computational efficiency. This dimensionality captures subtle facial features, essential for high accuracy.

---

## Classification

I employed a **Support Vector Machine (SVM)** for classification:

- **Training**: Embeddings were organized into folders by individual, serving as labels.
- **Validation**: Hyperparameters, such as the regularization parameter (C) and kernel, were fine-tuned using validation data.
- **Accuracy**: Achieved 82% on smaller datasets, but scalability issues arose with larger datasets.

---

## Results

1. **Verification**: All 1,020 embeddings adhered to the 512-dimensional structure.
2. **Cosine Similarity**: Self-similarity ranged from 0.1299 to 0.8429, while inter-class similarity ranged from 0.9355 to 1.0342, confirming effective separation of embeddings.
3. **Optimal Threshold**: A threshold of **0.77** provided balanced performance metrics:
   - **Genuine Acceptance Rate (GAR)**: 93.04%
   - **Genuine Rejection Rate (GRR)**: 91.66%
   - **False Acceptance Rate (FAR)**: 8.34%
   - **False Rejection Rate (FRR)**: 6.96%
4. **ROC Curve**: Achieved a score of **0.97**, indicating excellent discriminative power.
5. **Overall Accuracy**: 91.66%, highlighting the system's reliability and robustness.

### Performance Metrics vs. Threshold

- **Genuine Acceptance and Rejection Rates**: High GAR and GRR ensure the system reliably identifies genuine matches and rejects non-matches.
- **False Acceptance and Rejection Rates**: Balanced FAR and FRR minimize errors.

---

## Conclusion

Our facial recognition system achieved an accuracy of **91.66%**, showcasing its effectiveness for access control and security at Sapienza University. Despite challenges such as computational constraints and dependency conflicts, the project highlights the potential of deep learning techniques to streamline processes and enhance security in real-world applications.
