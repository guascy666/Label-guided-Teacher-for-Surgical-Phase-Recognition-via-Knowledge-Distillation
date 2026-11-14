# Label-guided-teacher-for-surgical-phase-recognition
# Introduction
Hi, this is the code repository for "Label-guided Teacher for Surgical Phase
Recognition via Knowledge Distillation" (Accepted by MICCAI 2024) in PyTorch.

![avatar](https://github.com/guascy666/Label-guided-teacher-for-surgical-phase-recognition/blob/main/model.png)

In this paper, we propose a novel label-guided teacher network for knowledge
distillation. Specifically, our teacher network takes both video frames and
ground-truth labels as input. Instead of only using labels to supervise the
final predictions, we additionally introduce two types of label guidance
to learn a better teacher: 1) we propose label embedding-frame feature
cross-attention transformer blocks for feature enhancement; and 2) we
propose to use label information to sample positive (from same phase)
and negative features (from different phases) in a supervised contrastive
learning framework to learn better feature embeddings. Then, by minimizing feature similarity, the knowledge learnt by our teacher network
is effectively distilled into a student network. At inference stage, the dis
tilled student network can perform accurate surgical phase recognition
taking only video frames as input.

# Model Training
## Data processing
Please downsample the original video data to 1fps and runing get_path_labels.py and get_path_labels40_40.py
## Training feature extractor
Run train_swin_backbone.py to train the feature extractor. After training, run extract_swin_spatial_feature_1024_40_40.py to extract features.

## Training teacher and student model
First, run Teacher_trainer.py to train a teacher model. Then, run the Student_trainer.py to train a student model. We provide Trainer_total_Abalation.sh for the complete training process.
# Citation
@InProceedings{10.1007/978-3-031-72089-5_33,
author="Guan, Jiale
and Zou, Xiaoyang
and Tao, Rong
and Zheng, Guoyan",
editor="Linguraru, Marius George
and Dou, Qi
and Feragen, Aasa
and Giannarou, Stamatia
and Glocker, Ben
and Lekadir, Karim
and Schnabel, Julia A.",
title="Label-Guided Teacher for Surgical Phase Recognition via Knowledge Distillation",
booktitle="Medical Image Computing and Computer Assisted Intervention -- MICCAI 2024",
year="2024",
publisher="Springer Nature Switzerland",
address="Cham",
pages="349--358",
abstract="Automatic surgical phase recognition plays an essential role in developing advanced, context-aware, computer-assisted intervention systems. Knowledge distillation is an effective framework to transfer knowledge from a teacher network to a student network, which has been used to solve the challenging surgical phase recognition task. A key to a successful knowledge distillation is to learn a better teacher network. To this end, we propose a novel label-guided teacher network for knowledge distillation. Specifically, our teacher network takes both video frames and ground-truth labels as input. Instead of only using labels to supervise the final predictions, we additionally introduce two types of label guidance to learn a better teacher: 1) we propose label embedding-frame feature cross-attention transformer blocks for feature enhancement; and 2) we propose to use label information to sample positive (from same phase) and negative features (from different phases) in a supervised contrastive learning framework to learn better feature embeddings. Then, by minimizing feature similarity, the knowledge learnt by our teacher network is effectively distilled into a student network. At inference stage, the distilled student network can perform accurate surgical phase recognition taking only video frames as input. Comprehensive experiments are conducted on two laparoscopic cholecystectomy video datasets to validate the proposed method, offering an accuracy of 93.3{\$}{\$}{\backslash},{\backslash}pm {\backslash},{\$}{\$}{\textpm}5.8{\%} on the Cholec80 dataset and an accuracy of 91.6{\$}{\$}{\backslash},{\backslash}pm {\backslash},{\$}{\$}{\textpm}9.1{\%} on the M2cai16 dataset.",
isbn="978-3-031-72089-5"
}

