
# Anomaly Detection on Industrial Bottles using Deep One-Class Classification


## Project Overview
This project aims to detect anomalies in industrial settings using deep one-class classification (OCC). We focused on the MVTec AD dataset, specifically the bottle category. [cite_start]This approach is suitable for real-world manufacturing where there are many examples of normal defect-free products but very few or none of the defective ones[cite: 8, 9, 10].

## Hypothesis
* [cite_start]**Primary Hypothesis:** Our prior hypothesis is that Deep Support Vector Data Description (Deep SVDD) achieves better anomaly detection performance than the classical One-Class SVM[cite: 17].
* [cite_start]**Latent Space:** By learning compact representations of normal data in a latent space, we expect the clustering of normal samples around the center point in the Deep OCC approach to be tight, with anomalies positioned farther away[cite: 18, 19].

## Dataset
This project utilizes the bottle category from the MVTec AD dataset. [cite_start]All images are high-resolution, with a size of 900x900 pixels[cite: 32, 40].

* [cite_start]**Train Set:** 209 images of good (non-defective) bottles[cite: 35].
* [cite_start]**Test Set:** A mix of normal and anomalous samples, consisting of[cite: 36, 37, 38]:
    * 22 images of broken_small bottles.
    * 20 images of broken_large bottles.
    * 21 images of contamination bottles.
    * 20 images of good bottles.

## Methodology

### Feature Extraction
We utilize pre-trained models to extract latent features from the bottle images:
* [cite_start]**ResNet18:** A convolutional neural network used to extract useful representations from the bottle images[cite: 13, 57].
* [cite_start]**Vision Transformers (ViT):** Tested as an alternative feature extractor for comparison in experiments[cite: 72].

### Classification Models
[cite_start]Extracted features are passed to two one-class classification methods[cite: 59]:
* **Deep SVDD:** A deep learning-based method that maps normal data points close to a central reference point in feature space. [cite_start]Points far from this center are likely anomalies[cite: 60, 61].
* [cite_start]**One-Class SVM:** A classical method that defines a boundary around the normal data in the feature space, treating anything outside this boundary as an anomaly[cite: 62].

## Results and Analysis

### Performance Comparison
* [cite_start]Deep SVDD outperformed the classical One-Class SVM in detecting anomalies[cite: 67].
* [cite_start]The One-Class SVM still achieved relatively high accuracy because the anomalies were visually distinct and easy to differentiate from normal samples[cite: 69].

### Feature Extractor Impact (ResNet vs. ViT)
[cite_start]We conducted experiments on SVM to see the impact of feature extractors[cite: 71]:
* [cite_start]**ResNet18:** Consistently outperformed ViT-based features across Recall, F1-score, Accuracy, and AUC-ROC[cite: 73].
* **ViT:** Achieved the highest precision score of 1.0. [cite_start]While the ViT-based model made fewer predictions, the anomalies it identified were always correct (zero false positives)[cite: 75, 76, 77].

### Latent Space Visualization
* [cite_start]**Deep SVDD:** Learned a compact representation with most good samples clustered tightly around the center (Silhouette Score: 0.1963)[cite: 98].
* [cite_start]**One-Class SVM:** Representations were more scattered, showing less cohesion among normal samples (Silhouette Score: 0.1485)[cite: 99].

### Confusion Matrix Example
(For SVM with ResNet Features) [cite_start][cite: 90]

| Category | Normal Prediction | Anomaly Prediction |
| :--- | :--- | :--- |
| **Good** | 20 | 0 |
| **Small Break** | 0 | 21 |
| **Large Break** | 0 | 21 |
| **Contamination** | 1 | 19 |

## Conclusion
[cite_start]The project confirms that while classical methods like One-Class SVM can be sufficient in controlled tasks, deep learning-based approaches like Deep SVDD offer superior performance and more robust feature representations[cite: 135]. [cite_start]The results also highlight the importance of selecting suitable feature extractors, as demonstrated by the trade-off between the general effectiveness of ResNet18 and the high precision of ViT[cite: 136].

## References
1. L. Ruff et al., "Deep one-class classification," ICML, 2018.
2. Schölkopf et al., "Estimating the support of a high-dimensional distribution," Neural Computation, 2001.
3. P. Bergmann et al., "MVTec AD A Comprehensive Real-World Dataset," CVPR, 2019.
4. C.-H. Li et al., "Improved Deep Support Vector Data Description Model Using Feature Patching," Sensors, 2024.
