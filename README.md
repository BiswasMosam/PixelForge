# PixelForge
Synthetic Data Generation using GANs for Privacy-Preserving and Data Augmentation (C-NMC Leukemia Dataset)
# PixelForge 🧬
Synthetic Data Generation using GANs for Privacy-Preserving and Data Augmentation  

## 📌 Overview
PixelForge is a deep learning project that leverages Convolutional Neural Networks (CNNs) and Generative Adversarial Networks (GANs) for medical image classification and augmentation.  
The project is tested on the **C-NMC Leukemia Dataset (ALL vs Normal cells)**.

### 🔹 Stage 1
- Built a baseline CNN classifier.
- Achieved **84% accuracy** and **0.89 ROC-AUC** on 706 held out cells.
- High recall for Leukemia cases (95%) – critical for medical diagnosis.

### 🔹 Stage 2
- Use GANs to generate synthetic cell images.
- Retrain CNN with augmented dataset.
- Evaluate performance improvement.

---

## 🚀 How to Run

### 1. Install dependencies
```bash
pip install torch torchvision numpy scikit-learn matplotlib seaborn pillow tqdm
```

### 2. Get the data
Download the C-NMC Leukemia dataset and unpack it so the folds sit under `./archive/fold_0`, `fold_1` and `fold_2`, each with `all/` (leukemia) and `hem/` (normal) cells.

### 3. Run
- **Stage 1, the CNN classifier:** open [`PixelForge.ipynb`](PixelForge.ipynb) and run it top to bottom. It trains, then prints the classification report, the confusion matrix and the ROC-AUC.
- **Stage 2, the GAN:** `python pixelforge_gan.py` trains the custom spectral-norm GAN on the normal (`hem`) cells and saves samples and checkpoints to `PixelForge_PFGAN/`.

## 📊 Results (Stage 1)

| Metric | Value |
|---|---|
| Accuracy | 84% |
| ROC-AUC | 0.89 |
| Leukemia recall | 95% (457 of 480) |

From the run plotted in [`Roc.pdf`](Roc.pdf) (AUC = 0.89) and [`Confusion.pdf`](Confusion.pdf) (137, 89 / 23, 457 on 706 validation cells).

Training is not seeded, so reruns land close to this but not on it. The run saved in the notebook, for example, reads 85% accuracy, 0.885 ROC-AUC and 93% leukemia recall.
