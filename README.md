# Design and Development of a Facial Recognition System

This project develops a facial recognition system aimed at improving access control and security at Sapienza University. The system utilizes deep learning techniques for accurate and efficient identification of individuals based on facial features.

## Key Features:

- **InceptionResNetV1** architecture pre-trained on the **VGGFace2** dataset.
- **512-dimensional embeddings** for reliable facial recognition, even under varying conditions like lighting and pose changes.
- **Support Vector Machine (SVM)** for classification and matching embeddings to individuals.
- Achieved **91.66% accuracy** for identification and verification tasks.

## Approach:

1. **Pretrained Model**: We used VGGFace2 for robust facial feature extraction, leveraging over 3 million labeled images from diverse conditions.
2. **Embedding**: The model generates 512-dimensional embeddings that capture key facial features.
3. **Normalization**: L2 normalization ensures consistent and reliable embedding comparison using cosine similarity.
4. **Classification**: The system applies SVM to classify individuals based on their embeddings, with performance optimized through hyperparameter tuning.

## Results:

- **Verification Accuracy**: 91.66%
- **Performance Metrics**:
  - **Genuine Acceptance Rate (GAR)**: 93.04%
  - **Genuine Rejection Rate (GRR)**: 91.66%
  - **False Acceptance Rate (FAR)**: 8.34%
  - **False Rejection Rate (FRR)**: 6.96%
- **ROC Curve Score**: 0.97, demonstrating excellent discriminative power.

### Notes on Metrics:

While it is possible to further optimize the system to maximize all metrics, the focus of this project was to prioritize the **Genuine Acceptance Rate (GAR)** over other metrics. This decision was based on the context of the system's application: the cost of a **false rejection** (i.e., a legitimate user being denied access) was deemed much higher than the cost of a **false acceptance** (i.e., an unauthorized user being granted access). In this context, it was more important to ensure legitimate users could access the system reliably, even at the slight expense of accepting a few false positives.

This system showcases the potential of deep learning in improving security and operational efficiency in real-world applications, despite some challenges related to computational limitations.
