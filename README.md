# Biomass Prediction – CSIRO Biomass Competition

This repository contains my solution for the **CSIRO Biomass Prediction** Kaggle competition, which focuses on predicting biomass values from images of grassland terrain.

🔗 **Competition link:**  
https://www.kaggle.com/competitions/csiro-biomass/data

---

## Project Overview

The goal of this project is to predict multiple biomass-related targets from RGB images of grass terrain using deep learning.  
This repository **does not include the dataset**; the data can be downloaded directly from the Kaggle competition page linked above.

The main objective of this work was **educational and experimental**: to apply PyTorch and deep learning fundamentals in a real computer vision regression problem, and to understand the full modeling pipeline end to end.

---

## Modeling Approach

The solution is implemented using **PyTorch** and focuses on building models **from scratch**, without relying on large pre-trained vision models.

### Key points of the approach:

- A **LeNet-inspired convolutional neural network (CNN)** was adapted for **regression** instead of classification.
- Although LeNet is a very simple architecture, it was intentionally chosen to:
  - Deepen understanding of convolutional neural networks
  - Experiment hands-on with image preprocessing, losses, and training dynamics
  - Maintain full interpretability and control over the architecture

- The final model predicts three fundamental biomass components, from which the remaining targets are derived using known physical relationships.

---

## Baselines and Experiments

Several experiments were conducted:

- **MLP baseline:**  
  A simple multilayer perceptron using only the green channel (which showed the highest variance during exploratory data analysis). Score 0.30
- **CNN with 3 RGB channels:**  
  This model quickly outperformed the MLP baseline, as expected for image-based tasks. (0.32)

Different loss functions and image preprocessing strategies were tested.  
The final model uses **SmoothL1Loss with a high beta value**, which provided more stable training for this regression task.

---

## Evaluation Strategy

- Model performance was evaluated using **cross-validation** across multiple folds.
- The main metric was the **globally weighted R² score**, as defined by the competition.
- This weighted R² was used consistently during cross-validation to compare model iterations and select improvements.

---

## Results

- The best validation score achieved was approximately **0.55 (weighted R²)** on a validation fold.
- This score was submitted to the competition.

While higher scores are achievable using **large pre-trained vision models** (e.g., DINOv2), this project intentionally avoids them due to the lack of a solid theoretical foundation at the time of development. Continuing in that direction without proper understanding would have meant proceeding blindly.

---

## Final Remarks

Although the final score is not competitive for a medal position, this project served as a **valuable learning experience**:

- Practical application of CNNs for regression
- Understanding loss functions and evaluation metrics
- Designing consistent training and validation pipelines
- Gaining intuition about computer vision models beyond theory

This repository reflects a meaningful hands-on exercise and a solid step toward more advanced vision models in the future.
Code and experiments for the Kaggle competition CSIRO – Image2Biomass Prediction. A hands-on project to learn and test computer-vision techniques for biomass estimation from images.
