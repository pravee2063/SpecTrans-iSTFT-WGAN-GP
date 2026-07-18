# SpecTrans-iSTFT-WGAN-GP

> **Transformer-Based WGAN-GP for Synthetic Biomedical and Environmental Time-Series Generation Using Multi-Scale Spectrograms**


---

# Overview

**SpecTrans-iSTFT-WGAN-GP** is an M.Tech group project developed as part of the Computer Science (AI & ML) program at **South Asian University**.

The project explores Transformer-based generative models for synthetic time-series generation using **multi-scale spectrogram representations**. Instead of generating raw signals directly, the framework transforms time-series data into spectrograms, learns their representations using a **Vision Transformer (ViT)-based WGAN-GP**, and reconstructs realistic signals through **inverse Short-Time Fourier Transform (iSTFT)**.

The proposed framework is evaluated on two publicly available datasets:

- **MIT-BIH Arrhythmia Database** (Biomedical ECG)
- **ESC-50 Environmental Sound Dataset**

The performance is evaluated using signal quality metrics and downstream classification accuracy.

---

# Features

- Vision Transformer (ViT) based Generator
- Wasserstein GAN with Gradient Penalty (WGAN-GP)
- Multi-scale STFT preprocessing
- Direct iSTFT reconstruction
- Spectral Normalization in the Critic
- Two-channel (Magnitude + Phase) spectrogram generation
- Evaluation on biomedical and environmental datasets
- Ablation study comparing Transformer and CNN architectures

---

# Repository Structure

```text
SpecTrans-iSTFT-WGAN-GP/
│
├── notebooks/
│   ├── SpecTrans_Ablation_MITBIH.ipynb
│   └── SpecTrans_Ablation_ESC50.ipynb
│
├── docs/
│   ├── Poster.pdf
│   └── Reference_Paper.pdf
│
├── data/
│   └── README.md
│
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

---

# Project Workflow

```text
Raw Signal
      │
      ▼
Segmentation
      │
      ▼
Multi-scale STFT
      │
      ▼
Magnitude + Phase Extraction
      │
      ▼
Transformer Generator
      │
      ▼
Synthetic Spectrogram
      │
      ▼
Direct iSTFT Reconstruction
      │
      ▼
Synthetic Signal
      │
      ▼
Evaluation
```

> **Insert your workflow diagram here.**

---

# Model Architecture

The framework consists of two main components:

## Generator

- Vision Transformer (ViT)
- Latent Dimension: **50**
- Four Transformer Encoder Blocks
- Generates two-channel spectrograms:
  - Magnitude
  - Phase

## Critic

- CNN-based architecture
- Spectral Normalization
- Wasserstein Loss with Gradient Penalty

## Reconstruction

Unlike conventional approaches that rely on iterative Griffin-Lim reconstruction, this project directly reconstructs the generated magnitude and phase using **inverse Short-Time Fourier Transform (iSTFT)**.

> **Insert your architecture diagram here.**

---

# Datasets

| Dataset | Domain | Classes |
|----------|--------|----------|
| MIT-BIH Arrhythmia | Biomedical ECG | Normal, LBBB, RBBB |
| ESC-50 | Environmental Audio | Rain, Engine, Siren |

---

# Experimental Setup

| Parameter | Value |
|-----------|------:|
| GAN Framework | WGAN-GP |
| Generator | Vision Transformer |
| Critic | CNN + Spectral Normalization |
| Latent Dimension | 50 |
| Optimizer | Adam |
| Gradient Penalty | 10 |
| Critic Updates | 3 |

---

# Results

## MIT-BIH Classification Accuracy

| Model | Accuracy |
|-------|---------:|
| Baseline | 92.78% |
| Transformer + Griffin-Lim | **95.44%** |
| Transformer + Direct iSTFT | 94.72% |
| CNN + Griffin-Lim | 94.33% |
| CNN + Direct iSTFT | 95.06% |

---

## ESC-50 Classification Accuracy

| Model | Accuracy |
|-------|---------:|
| Baseline | 76.06% |
| Transformer + Direct iSTFT | **76.44%** |
| Transformer + Griffin-Lim | 75.83% |
| CNN + Griffin-Lim | 75.72% |
| CNN + Direct iSTFT | 75.50% |

---

### Evaluation Metrics

- Root Mean Square (RMS)
- Kurtosis
- Fast Fourier Transform (FFT)
- Power Spectral Density (PSD)

> **Insert waveform, spectrogram, FFT, or PSD comparison figures here.**

---

# Installation

## Clone the Repository

```bash
git clone https://github.com/<your-username>/SpecTrans-iSTFT-WGAN-GP.git
cd SpecTrans-iSTFT-WGAN-GP
```

## Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

# Usage

Run either notebook from the `notebooks/` directory:

- `SpecTrans_Ablation_MITBIH.ipynb`
- `SpecTrans_Ablation_ESC50.ipynb`

Execute all notebook cells sequentially to:

- Download and preprocess the dataset
- Train the model
- Generate synthetic signals
- Evaluate model performance

---

# Team

This project was developed as part of the **M.Tech Computer Science (AI & ML)** program at **South Asian University**.

| Team Members |
|--------------|
| Awantika Krishna |
| Binwant Kaur |
| Praveena P. |

---

# References

1. Vaswani et al., *Attention Is All You Need*, NeurIPS (2017).
2. Arjovsky et al., *Wasserstein GAN*, ICML (2017).
3. Gulrajani et al., *Improved Training of Wasserstein GANs*, NeurIPS (2017).
4. Dosovitskiy et al., *An Image is Worth 16×16 Words: Vision Transformer*, ICLR (2021).
5. PhysioNet MIT-BIH Arrhythmia Database.
6. ESC-50 Environmental Sound Dataset.

---

# License

This project is licensed under the **Creative Commons Zero v1.0 Universal (CC0 1.0)** License.

The CC0 1.0 license dedicates this work to the public domain to the fullest extent permitted by law. You are free to copy, modify, distribute, and use this project for any purpose, including commercial applications, without asking for permission or providing attribution.

For the full license text, see the [`LICENSE`](LICENSE) file.
