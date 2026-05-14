# Coffee-Leaf-Rust-Generalization

Repository dedicated to DL 2026 project

Group Members: Nicholas Drew and Joesph Schaak

## Data

Datasets used can be found at the following locations:

[RoCoLe Data](https://data.mendeley.com/datasets/c5yvn32dzg/2)

[Cyber Physical Data Collection System CLR Dataset](https://ieee-dataport.org/documents/coffee-leaf-rust-dataset)

## Project Goals

The aim of this work is to research methods for generalizing deep learning models to classify Coffee Leaf Rust, (*Hemileia vastatrix*). More details on the methods and motivations can be found in the associated [Report](FinalReport.pdf). 

## Code Overview

The code for this project was run in Jupyter Notebooks on Google Colab. The function of each is listed here.

[data_examination](notebooks/data_examination.ipynb): Examining different candidate datasets for our project.

[baseline_model](notebooks/baseline_model.ipynb): Comparing the performance of the two datasets with no additional augmentation or segmentation.

[augmentation_comparisons](notebooks/augmentation_comparisons.ipynb): Benchmarking the performance of several candidate augmentations and their combinations on the model.

[segmentation_two_models](notebooks/segmentation_two_models.ipynb): Benchmarking the performance of the segmeneted RoCoLe data on the baseline architecture.

[augmented_model](notebooks/augmented_model.ipynb): Training model with final augmentation combination on RoCoLe. Weights from this model are stored in [densenet_finetuned](models/densenet_finetuned.pth).

[combined_performance](notebooks/combined_performance.ipynb): Benchmarking the performance of the augmented model on the segmented external datasets.

[complete_model](notebooks/complete_model.ipynb): Final model training, which combines the augmentations from the augmented model and **both** datasets to attempt the most "deployable" version of the model. Weights are stored in [completemodelparameters](models/completemodelparameters.pth).

## Architectures

This project heavily relies on two major deep learning architectures for the classification task:

DenseNet201: The main architecture used for classification. Intially trained only the classification layer, but eventually expanded to the top normalization and dense layer.

YOLOv8: Used to build a segmentation pipeline for the RoCoLe leaf images.

## Tools

[Albumentations](https://www.mdpi.com/2078-2489/11/2/125): Heavily used for augmentation pipeline. Allows for fast and flexible use of a large variety of augmentation techniques.

[CVAT](github.com/opencv/cvat) (Computer Vision Annotation Tool): Used to annotate external dataset for training segmentation model.

[Ultralytics](https://github.com/ultralytics/ultralytics): Used to train YOLOv8 image segmentation model.

## Key Results

Baseline: Densenet201 architecture gets an internal validation accuracy of **90.68%** on the RoCoLe dataset, but falls to **69.19%** on the external dataset. Performance results as a consequence of the domain shift between the two datasets.

Augmentation: Aggressive augmentations mixed with increased image sizes increased external accruacy to **82.92%** (an approximately 13% increase from the baseline).

Segmentation: Segmentation did not improve external accuracy, dropping the accuracy to **66.23%**. Suggesting key contextual information is lost during segmentation.





