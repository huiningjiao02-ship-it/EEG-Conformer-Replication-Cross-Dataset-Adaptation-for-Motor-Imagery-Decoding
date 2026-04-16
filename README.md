# EEG-Conformer for Motor Imagery on PhysioNet eegmmidb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_5OjmRb-AIt7KSR5zOXs8lNSYDNrqqce)

## Introduction

This project reproduces the **EEG-Conformer** architecture (Song et al., 2023) on the **PhysioNet EEG Motor Movement/Imagery Dataset (eegmmidb)**. EEG-Conformer combines convolutional layers for local temporal feature extraction with a transformer encoder to capture global dependencies across time windows.

I adapted the original 22‑channel model to support **64‑channel** EEG input and implemented a one‑click Colab pipeline with automatic data download and preprocessing. The project runs four‑class motor imagery classification (left fist / right fist / both fists / both feet) under a within‑subject training setting.

## 项目介绍

本项目在 **PhysioNet EEG 运动想象数据集（eegmmidb）** 上复现了 **EEG-Conformer** 架构（Song et al., 2023）。EEG-Conformer 结合卷积层提取局部时序特征，并利用 Transformer 编码器捕捉跨时间窗的全局依赖关系。

我将原模型从 22 通道扩展至 **64 通道** 以适配 eegmmidb 数据集，并实现了一键运行的 Colab 流程，包含数据自动下载与预处理。项目在受试者内训练设置下进行四分类运动想象任务（左手 / 右手 / 双手 / 双脚）。

---

## Key Features

- Reproduces the EEG-Conformer architecture for motor imagery decoding
- Extended from 22 to **64 channels** to match the eegmmidb dataset
- Implements the original `interaug` data augmentation strategy
- Automatic dataset download via `mne.datasets`
- One‑click Colab execution with GPU support
- Flexible configuration for number of subjects and training epochs

## 核心特性

- 复现 EEG-Conformer 架构用于运动想象解码
- 将原模型从 22 通道扩展至 **64 通道**，适配 eegmmidb 数据集
- 实现原论文的 `interaug` 数据增强策略
- 通过 `mne.datasets` 自动下载数据集
- Colab 一键运行，支持 GPU 加速
- 可灵活配置受试者数量与训练轮数

---

## Quick Start

1. Click the **Open In Colab** badge above
2. Set runtime to **GPU** (`Runtime` → `Change runtime type`)
3. Run all cells (`Runtime` → `Run all`)

The notebook will download the eegmmidb dataset, train the model, and display results.

## 快速开始

1. 点击上方的 **Open In Colab** 徽章
2. 将运行时类型设置为 **GPU**（`Runtime` → `Change runtime type`）
3. 运行所有单元格（`Runtime` → `Run all`）

Notebook 将自动下载 eegmmidb 数据集、训练模型并展示结果。

---

## Results

| Metric | Value |
| :--- | :--- |
| Average Peak Accuracy (7 subjects) | **98.81%** |
| Subjects Achieving 100% | 6 / 7 |
| Lowest Subject Accuracy | 91.67% |

**Important Note**: These results are obtained under **within‑subject (subject‑dependent) evaluation**, where training and test splits are drawn from the same subject's trials. While this validates the model's capability to decode motor imagery patterns for a given individual, it **does not measure cross‑subject generalization**. The original EEG-Conformer paper reports 78.66% on BCI Competition IV 2a under a fixed hold‑out protocol; the higher accuracy here reflects both the within‑subject setting and differences in dataset characteristics (eegmmidb has longer trials and higher signal quality). Direct comparison across datasets and evaluation protocols is not meaningful.

## 实验结果

| 指标 | 数值 |
| :--- | :--- |
| 平均峰值准确率（7 名受试者） | **98.81%** |
| 达到 100% 的受试者数 | 6 / 7 |
| 最低单受试者准确率 | 91.67% |

**重要说明**：这些结果是在 **受试者内（受试者依赖）评估** 下获得的，即训练集和测试集来自同一受试者的不同试次。这验证了模型对特定个体的运动想象模式解码能力，但 **并不能衡量跨被试泛化能力**。原 EEG-Conformer 论文在 BCI Competition IV 2a 数据集上报告了 78.66% 的准确率；此处更高的准确率既反映了受试者内训练设置的特性，也源于数据集差异（eegmmidb 试次更长、信号质量更高）。跨数据集和跨评估协议的直接比较不具备参考意义。

---

## Limitations

1. **Evaluation Protocol** – Only within‑subject (subject‑dependent) validation is performed. Cross‑subject generalization ability has not been evaluated.
2. **Dataset Scope** – Validated only on eegmmidb; performance on other motor imagery datasets (e.g., BCI IV 2a, OpenBMI) remains untested.
3. **Offline Processing** – The pipeline is designed for offline batch analysis; real‑time decoding is not implemented.

## 局限性

1. **评估协议** – 仅进行了受试者内（受试者依赖）验证，跨被试泛化能力未评估。
2. **数据集范围** – 仅在 eegmmidb 上验证，其他运动想象数据集（如 BCI IV 2a、OpenBMI）上的性能未知。
3. **离线处理** – 流程设计为离线批处理分析，未实现实时解码。

---

## Future Improvements

- Implement **Leave‑One‑Subject‑Out (LOSO)** cross‑validation to assess true cross‑subject generalization
- Evaluate on additional public datasets (BCI Competition IV 2a, SEED‑VIG) to benchmark robustness
- Explore lightweight model variants for potential real‑time BCI applications
- Add support for **subject‑adaptive fine‑tuning** to reduce calibration time

## 未来改进方向

- 实现 **留一被试交叉验证（LOSO）**，评估真实跨被试泛化能力
- 在更多公开数据集（BCI Competition IV 2a、SEED‑VIG）上进行评估，检验鲁棒性
- 探索轻量化模型变体，用于潜在实时 BCI 应用
- 增加 **受试者自适应微调** 功能，减少校准时间

---

## Project Structure
.
├── EEG_Conformer_eegmmidb.ipynb # Main Colab notebook
├── models/
│ └── eeg_conformer.py # Model definition
├── utils/
│ ├── data_loader.py # Data loading and preprocessing
│ └── augmentation.py # interaug implementation
├── requirements.txt
└── README.md

## 项目结构

├── EEG_Conformer_eegmmidb.ipynb # 主 Colab Notebook
├── models/
│ └── eeg_conformer.py # 模型定义
├── utils/
│ ├── data_loader.py # 数据加载与预处理
│ └── augmentation.py # interaug 数据增强实现
├── requirements.txt
└── README.md

---

## Reference

- **EEG-Conformer**: *EEG Conformer: Convolutional Transformer for EEG Decoding and Visualization*  
  Song et al., IEEE Transactions on Neural Systems and Rehabilitation Engineering, 2023  
  [DOI: 10.1109/TNSRE.2023.3239848](https://doi.org/10.1109/TNSRE.2023.3239848)
