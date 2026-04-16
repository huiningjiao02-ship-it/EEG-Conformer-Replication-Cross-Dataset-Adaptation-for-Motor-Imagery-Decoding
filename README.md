# EEG-Conformer for Motor Imagery on PhysioNet eegmmidb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_5OjmRb-AIt7KSR5zOXs8lNSYDNrqqce)

> **English** | [中文说明](#-中文说明)

本项目是对 **EEG-Conformer** 架构 (Song et al., 2023) 的完整复现，在 **PhysioNet EEG Motor Movement/Imagery Dataset (eegmmidb)** 数据集上进行了适配和验证。项目已修改为支持 **64 通道输入**，并在 **Google Colab** 中提供一键运行的环境，包含自动数据下载功能。

---

## ✨ 项目亮点

| 特性 | 说明 |
| :--- | :--- |
| 🧠 **64 通道支持** | 将原始 22 通道模型扩展，以处理 64 通道的 EEG 信号。 |
| 📦 **零手动配置** | 通过 `mne.datasets` 自动下载数据集，无需手动下载和配置。 |
| 🔄 **论文数据增强** | 完整复用了原论文的 `interaug` 数据增强策略。 |
| ☁️ **Colab 一键运行** | 点击上方的徽章即可在云端运行，无需本地 GPU 环境。 |
| ⚙️ **灵活配置** | 可轻松调整受试者数量、训练轮数 (epochs) 和批次大小 (batch size)。 |

---

## 🚀 快速开始

### 在 Google Colab 中运行 (推荐)

1.  点击上方的 **Open In Colab** 徽章。
2.  在 Colab 中，点击 `Runtime` → `Change runtime type`，选择 **T4 GPU** 作为硬件加速器。
3.  顺序运行所有单元格 (`Runtime` → `Run all`)。

代码将自动下载数据集、训练模型并展示结果。

### 本地运行

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
pip install -r requirements.txt
jupyter notebook EEG_Conformer_eegmmidb.ipynb

