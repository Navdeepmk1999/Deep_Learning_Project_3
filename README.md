# Jailbreaking Deep Models

**Spring 2025 | NYU Deep Learning - Final Project**

## Authors

- **Navdeep Mugathihalli Kumaregowda** (nm4686)  
- **Satya Deep Dasarai** (gd2576)  

_New York University_


This project explores adversarial robustness of pretrained image classifiers (ResNet-34 and DenseNet-121) through gradient-based and patch-based attacks. The goal is to “jailbreak” high-performing models by generating adversarial examples that lead to severe misclassification while maintaining visual similarity to the original images.

---

##  Overview

We implemented and evaluated the following adversarial attack strategies:

- **FGSM (Fast Gradient Sign Method)** — L∞ single-step gradient attack.
- **PGD (Projected Gradient Descent)** — L∞ multi-step iterative attack.
- **Patch-based L₀ attack** — 32×32 localized patch attack, optionally targeted.
- **Transferability Testing** — Evaluate generated adversarial examples on a different model (DenseNet-121).

---

##  Experimental Setup

- **Model 1**: ResNet-34 (`torchvision.models.resnet34`)
- **Model 2**: DenseNet-121 (`torchvision.models.densenet121`)
- **Dataset**: Subset of 100 ImageNet-1K classes (500 images)
- **Preprocessing**:
  ```python
  mean = [0.485, 0.456, 0.406]
  std  = [0.229, 0.224, 0.225]

---

##  Results Summary

###  ResNet-34 Accuracy

| Dataset     | Top-1 (%) | Top-5 (%) |
|-------------|-----------|-----------|
| Original    | 76.00     | 94.20     |
| FGSM        | 1.40      | 15.80     |
| PGD         | 0.00      | 1.40      |
| Patch Attack| 1.40      | 42.20     |

###  DenseNet-121 Transferability

| Dataset     | Top-1 (%) | Top-5 (%) |
|-------------|-----------|-----------|
| Original    | 74.80     | 93.60     |
| ADV_set1    | 40.20     | 73.40     |
| ADV_set2    | 43.40     | 78.00     |
| ADV_set3    | 71.80     | 91.60     |

