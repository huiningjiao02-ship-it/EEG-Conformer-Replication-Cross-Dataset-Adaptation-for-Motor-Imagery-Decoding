# EEG Conformer for Motor Imagery on PhysioNet eegmmidb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/你的用户名/仓库名/blob/main/EEG_Conformer_eegmmidb.ipynb)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.13%2B-orange)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](./LICENSE)

> **English** | [中文说明](#chinese-version)

A clean, one-click reproduction of the **EEG Conformer** architecture (Song et al., 2023) on the **PhysioNet EEG Motor Movement/Imagery Dataset (eegmmidb)**.  
Modified to support **64‑channel** input and runs entirely in **Google Colab** with automatic data download.

---

## ✨ Highlights

| Feature | Description |
| :--- | :--- |
| 🧠 **64‑Channel Support** | Extended the original 22‑ch model to handle 64‑channel EEG signals. |
| 📦 **Zero Manual Setup** | Dataset is downloaded automatically via `mne.datasets`. |
| 🔄 **Paper Augmentation** | Re‑implements the `interaug` data augmentation strategy from the paper. |
| ☁️ **Colab Ready** | Click the badge above to run everything in the cloud—no local GPU needed. |
| ⚙️ **Flexible Config** | Easily adjust the number of subjects, epochs, and batch size. |

---

## 🚀 Quick Start

### Run in Google Colab (Recommended)

1. Click the **Open in Colab** badge above.
2. Go to `Runtime` → `Change runtime type` → Select **GPU**.
3. Run all cells (`Runtime` → `Run all`).

That's it! The notebook will download the eegmmidb dataset, train the model, and display results.

### Run Locally

