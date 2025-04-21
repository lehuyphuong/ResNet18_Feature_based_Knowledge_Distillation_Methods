# ResNet18_Feature_based_Knowledge_Distillation_Methods

## 📘 Overview
This project demonstrates feature-based knowledge distillation applied to an image classification task on a custom weather dataset, with the ResNet architecture.

The goal is to transfer intermediate feature representations from a strong teacher model (ResNet34) to a lightweight student model (ResNet18), enabling the student to learn more effectively and generalize better with fewer parameters.

> This article emphasizes conceptual understanding and experimental strategy, not code-level implementation.

## 🎯 Motivation
Feature-based knowledge distillation offers a compelling solution by transferring hidden feature maps—rather than just final predictions—enabling student models to learn from the internal behavior of their teachers.

## 🧪 Dataset
We use a weather classification dataset organized into categories (e.g., sunny, cloudy, foggy, etc.). The data is split as follows: Training: 70%, Validation: 20%, Testing: 10%. Plus, each image is resized to (224x224) and normalized before training.

## 🧱 Model Architecture
Teacher Model: ResNet34 (Pretrained via timm)
- Pretrained on ImageNet.
- Modified to return feature maps from the last convolutional layer.

Student Model: ResNet18
- Custom implementation using basic residual blocks.
- Includes a regressor branch to mimic the feature maps from the teacher model.

## 🔥Strategy
This project employs intermediate feature mimicking, also known as hint-based learning. The student is guided by two objectives:
- Match predicted labels (classification task)
- Match internal feature maps from the teacher (distillation task)

## 🔧 Loss Function
The total loss is a weighted sum of:
- CrossEntropyLoss: for classification accuracy.
- MSELoss: for aligning the student’s feature maps with the teacher's:

## 📈 Evaluation Metrics
- Validation Accuracy & Loss (per epoch)
- Test Accuracy & Loss

## 📌 Final Remarks
Feature-based knowledge distillation is a powerful extension of classic KD, offering deeper guidance through internal representations. This method is particularly effective for tasks where spatial feature alignment is crucial.