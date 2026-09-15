# NeuroMaskNet: Explainable Cross-Subject Auditory Attention Decoding

![Conference](https://img.shields.io/badge/Conference-ICASSP%202027-blue)

**Authors:** Tasleem Kausar, Haizhou Li  
**Affiliation:** School of Artificial Intelligence, The Chinese University of Hong Kong, Shenzhen, China

---

## Abstract

Cross-subject Auditory Attention Decoding (AAD) remains challenging due to substantial inter-subject variability and limited model interpretability. We propose **NeuroMaskNet**, an explainable framework that integrates a Structured NeuroMask Module (SNM), a shared spatio-temporal Transformer, NeuroSpatial Attention Fusion (NSAF), and information-bottleneck-guided disentanglement.

SNM generates anatomically isolated EEG views, while NSAF models region-specific neural relevance for interpretable decoding. Meanwhile, the disentanglement module separates task-relevant, subject-invariant information from subject-specific factors to improve generalization to unseen subjects. NeuroMaskNet achieves strong cross-subject performance on the KUL, DTU, and AVED datasets.

---

## Model Architecture

<p align="center">
  <img src="figures/framework.png" width="95%">
</p>

NeuroMaskNet consists of four main components:

1. **Structured NeuroMask Module (SNM)** – generates one full-scalp and ten anatomically isolated EEG views.
2. **Shared Spatio-Temporal Transformer** – extracts complementary temporal and spatial representations.
3. **NeuroSpatial Attention Fusion (NSAF)** – adaptively models regional relevance.
4. **Disentanglement Head** – separates task-relevant and subject-specific representations.

---

## Installation & Prerequisites

The code is implemented in **Python** using **PyTorch**.

### 1. Create environment

```bash
conda create -n neuromask python=3.8
conda activate neuromask
pip install torch numpy pandas scikit-learn tqdm matplotlib
python neuromask-net
## Main Results

### Comparison with State-of-the-Art Methods

| Dataset | Model | 1-second | 2-second |
|---|---|---:|---:|
| **KUL** | SSF-CNN | 59.3 ± 6.7 | 60.8 ± 8.4 |
|  | DBPNet | 61.1 ± 8.3 | 62.3 ± 7.4 |
|  | ListenNet | 63.6 ± 11.1 | 64.2 ± 12.4 |
|  | DARNet | 69.9 ± 11.8 | 71.9 ± 13.0 |
|  | FD-ARL | 74.5 ± 14.73 | 74.6 ± 14.04 |
|  | **NeuroMaskNet (Ours)** | **76.6 ± 13.6** | **77.2 ± 13.3** |
| **DTU** | SSF-CNN | 52.3 ± 3.5 | 53.4 ± 4.2 |
|  | DBPNet | 55.5 ± 6.3 | 55.8 ± 6.1 |
|  | ListenNet | 54.8 ± 4.4 | 55.1 ± 4.2 |
|  | DARNet | 55.6 ± 4.1 | 55.6 ± 4.0 |
|  | FD-ARL | 57.7 ± 4.68 | 58.1 ± 4.42 |
|  | **NeuroMaskNet (Ours)** | **57.8 ± 3.5** | **59.1 ± 3.7** |
| **AVED-Audio** | SSF-CNN | 51.2 ± 3.1 | 51.4 ± 3.9 |
|  | DBPNet | 52.1 ± 4.2 | 52.8 ± 4.3 |
|  | ListenNet | 51.4 ± 4.2 | 52.6 ± 4.1 |
|  | DARNet | 52.3 ± 3.1 | 52.3 ± 3.1 |
|  | FD-ARL | 53.7 ± 3.6 | 54.1 ± 4.2 |
|  | **NeuroMaskNet (Ours)** | **54.9 ± 3.7** | **55.3 ± 3.1** |
| **AVED-Video** | SSF-CNN | 51.4 ± 3.5 | 51.5 ± 3.2 |
|  | DBPNet | 51.8 ± 3.4 | 52.2 ± 3.1 |
|  | ListenNet | 51.6 ± 3.2 | 52.7 ± 3.0 |
|  | DARNet | 52.4 ± 3.1 | 53.4 ± 3.2 |
|  | FD-ARL | 53.9 ± 3.5 | 54.4 ± 3.9 |
|  | **NeuroMaskNet (Ours)** | **56.1 ± 3.5** | **56.3 ± 3.3** |

| Method                   |   Accuracy (%) |
| ------------------------ | -------------: |
| **NeuroMaskNet (Ours)**  | **57.8 ± 3.5** |
| w/o pro, SIB, adv, recon |    56.3 ± 4.42 |
| w/o pro, SIB             |    56.9 ± 4.17 |
| w/o adv, recon           |    56.0 ± 4.21 |
| w/o Spat                 |    55.6 ± 5.56 |
| w/o Temp                 |    51.3 ± 7.66 |
| w/o SNM, NSAF            |    56.2 ± 4.32 |

