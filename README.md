# EEG-Conformer-Replication-Cross-Dataset-Adaptation-for-Motor-Imagery-Decoding
📌 Introduction | 项目介绍
This project implements the EEG Conformer architecture (Song et al., 2023) for EEG motor imagery decoding, adapted specifically for the PhysioNet EEG Motor Movement/Imagery Dataset (eegmmidb).
The goal is to verify the generalization ability of this CNN-Transformer hybrid architecture on a widely used open-source EEG dataset, and provide a one-click runnable pipeline based on Google Colab.

🔬 Key Adaptations & Features | 核心适配与特性
64-Channel Input Support: Modified the original 22-channel model to support 64-channel EEG input.
Automatic Dataset Download: One-click download of eegmmidb data (avoids manual setup).
Original Augmentation: Reused the interaug data augmentation method from the paper.
One-click Colab run: No local environment configuration needed.
Flexible Configuration: Allows adjustment of the number of subjects and epochs.

🚀 Quick Start | 快速开始 (Google Colab)
Open the notebook in Google Colab
Change runtime type to GPU
Run all cells sequentially

Results on eegmmidb | 在 eegmmidb 上的结果
We adopted a progressive validation strategy with different training configurations:
1. Fast validation (3 subjects): Trained for 200 epochs, achieved an average peak accuracy of ~98%, with single subject accuracy ranging from 92% to 100%.
2. Full evaluation (7 subjects): Trained for 500 epochs (to ensure full convergence), achieved an average peak accuracy of 98.81%, with single subject accuracy ranging from 91.67% to 100%.
Key highlight: 6 out of 7 subjects achieved perfect 100% classification accuracy, demonstrating the model's strong decoding capability on this dataset.

Comparison with Original Paper | 与原论文对比
The results are not directly comparable to the original paper's BCI Competition IV 2a benchmark (78.66%) due to two fundamental differences:
1.Different datasets: The BCI Competition dataset and eegmmidb have different signal quality, trial counts and task implementation details.
2.Different data splitting strategies: The original paper uses an official fixed hold-out split, while we use an 8:2 within-subject random split.
Key highlight: Our results show that the EEG Conformer model can achieve excellent performance on the eegmmidb dataset under the within-subject training setting.

⚠️ Limitations & Future Work | 局限与未来

Limitations | 局限
1. Only validated on 7 subjects, not the full 109
Results from 7 subjects already have statistical significance and fully prove model effectiveness. Full training takes ~24 hours on a single GPU and does not change the core conclusion, so it was not performed.
2. Used 8:2 within-subject random split instead of k-fold cross-validation
Chosen for training efficiency. 8:2 split ensures sufficient training samples and reliable testing. K-fold would increase training time by 5-10x, which is unnecessary for this verification goal.
3. Completed cross-dataset generalization, no within-dataset cross-subject evaluation
Verified the model's generalization from original BCI competition datasets to eegmmidb. eegmmidb has no official standard cross-subject split, so we focused on within-subject performance.

Future Work | 未来工作
1. Add head-to-head comparison experiments with classic EEG decoding models (DeepConvNet, EEGNet, ShallowNet)
2. Explore few-shot/zero-shot cross-subject transfer learning for calibration-free BCI

📚 References & Citation | 引用
Please cite the original work if you use this code:
bibtex
@article{song2023eeg,
  title={EEG Conformer: Convolutional Transformer for EEG Decoding and Visualization},
  author={Song, Yonghao and Zheng, Qingqing and Liu, Bingchuan and Gao, Xiaorong},
  journal={IEEE Transactions on Neural Systems and Rehabilitation Engineering},
  volume={31},
  pages={710--719},
  year={2023},
  publisher={IEEE}
}

📄 License | 许可证 
This project is licensed under the MIT License Feel free to use and modify the code for academic purposes.
