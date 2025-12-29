# Rock Fabric Classification with Interpretables

This project explores **rock fabric classification** using machine learning, with a focus not only on prediction accuracy, but also on **interpretability and similarity analysis**.

Classifying rocks from rock fabric images is a time-consuming task for geologists, especially when dealing with large datasets. This work investigates how convolutional neural networks (CNNs) can be used to automate the process, and how learned feature embeddings can be reused for visualization, interpretation, and classical classification.

---

## Dataset

The dataset consists of **28 × 28 pixel rock-fabric images** sourced from Kaggle, grouped into **six rock classes**:

- Andesite  
- Quartzite  
- Marble  
- Rhyolite  
- Schist  
- Gneiss  

Each image represents a cropped view of a rock thin section, where visual differences can be subtle and class boundaries are often ambiguous.

---

## Methodology

### Convolutional Neural Network (CNN)

A compact CNN architecture is used, consisting of:
- Three convolutional layers  
- Batch normalization  
- Max pooling  
- A linear head split into:
  - an **embedding layer** (256-dimensional)
  - a **classifier layer** producing logits for six classes

The CNN achieves a **test accuracy of ~97.5%**. Performance is strong overall, but certain visually similar class pairs (e.g. andesite vs rhyolite, schist vs gneiss) remain challenging.

---

### Saliency Maps

To understand model decisions, **saliency maps** are used to highlight which pixels contribute most to each prediction.

- Correct predictions often emphasize **mineral boundaries and grain shapes**
- Incorrect predictions tend to produce **noisy or less informative saliency patterns**

This helps explain why certain samples are harder for the model to classify.

---

### Embedding Space Analysis

The output of the embedding layer is visualized using **Principal Component Analysis (PCA)**.

- Most classes are reasonably separable in the projected space
- Overlapping regions correspond closely to known misclassification pairs
- Marble forms a more isolated cluster, matching its strong classification performance

---

### Similarity Retrieval with KNN

To improve interpretability and explore alternatives to end-to-end deep learning, **Nearest Neighbours** is applied directly to the learned embeddings.

- Nearest-neighbour retrieval allows manual comparison of visually similar samples
- Replacing the CNN’s linear classifier with **KNN on the embedding space** improves accuracy to **~98%**
- Confusion between difficult class pairs is reduced

This demonstrates that classical methods can sometimes outperform neural network heads when combined with learned features.

---

## Citation

- Dataset: [Kaggle](https://www.kaggle.com/datasets/tanyadayanand/geological-image-similarity/data)
- Grammar Correcting [Open AI ChatGPT 5.2](https://chatgpt.com/)

---

## Repository Structure

