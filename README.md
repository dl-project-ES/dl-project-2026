# Open-Set RF Signal Discovery Using Machine Learning

## Overview

Modern radio frequency (RF) monitoring and classification systems predominantly rely on supervised machine learning models trained under a closed-set assumption, where all observed signals are assumed to belong to a predefined set of known classes. While effective in controlled environments, this assumption is fundamentally incompatible with real-world wireless spectrum conditions, where new, modified, proprietary, or unauthorized transmitters may appear without prior knowledge.

This project investigates the limitations of closed-set RF classification and proposes an experimental open-set machine learning framework capable of detecting previously unseen RF signals, separating them from known signal classes, and discovering structure within unknown signals using unsupervised analysis. The focus of this work is on reproducible experimentation and analysis rather than real-time deployment.

---

## Problem Statement

Given a stream of raw radio frequency in-phase and quadrature (I/Q) samples and a machine learning model trained only on known signal sources, existing RF classification systems lack the ability to recognize when an observed signal does not belong to any known class. As a result, unknown signals are forcibly misclassified with high confidence, leading to unreliable spectrum awareness and potential security or interference risks.

The objective of this project is to design and evaluate a machine learning pipeline that operates under an open-set RF assumption, enabling reliable detection of unknown signals and analysis of their structural properties under controlled experimental conditions.

---

## Research Objectives

- Analyze the failure modes of closed-set RF classifiers when exposed to unseen signal sources  
- Design a framework to detect unknown RF signals without prior labels  
- Prevent forced misclassification of unknown signals into known classes  
- Discover and analyze structure within unknown RF signals using clustering techniques  
- Establish appropriate evaluation metrics for open-set RF machine learning systems  

---

## System Architecture

The proposed pipeline consists of the following stages:

Raw RF I/Q Samples (SigMF)  
→ Preprocessing and windowing  
→ Feature learning using a convolutional neural network encoder  
→ Closed-set baseline classification  
→ Unknown signal detection  
→ Unsupervised clustering of unknown signals  
→ Evaluation and visualization  

Each component is implemented as a modular and configurable unit to ensure reproducibility and extensibility.

---

## Dataset

This project uses the publicly available ORACLE RF Fingerprinting dataset, which contains:

- Over-the-air raw I/Q samples collected from multiple USRP SDR transmitters  
- Controlled demodulated I/Q samples with intentional hardware impairments  
- SigMF-formatted data with accompanying metadata  

The dataset is approximately 30 GB in size and is intentionally excluded from this repository. All experiments assume that the dataset is stored externally (e.g., on a shared storage device) and accessed via configurable paths.

---

## Experimental Protocol

- A subset of transmitter devices is selected as known classes for training  
- Remaining devices are withheld during training and treated as unknown during evaluation  
- Closed-set classification behavior is evaluated on both known and unknown signals  
- Unknown detection mechanisms are applied to separate known and unknown signals  
- Unsupervised clustering is performed on unknown signals to identify structural groupings  

This protocol simulates an open-set RF environment under controlled experimental conditions.

---

## Evaluation Metrics

Standard classification accuracy is insufficient for open-set evaluation. The following metrics are used instead:

- Area Under the Receiver Operating Characteristic Curve (AUROC) for known vs unknown detection  
- False Acceptance Rate (FAR) to measure forced misclassification of unknown signals  
- Silhouette score to evaluate the quality of clustering among unknown signals  
- Latent space visualizations to analyze feature separability  

---

## Project Structure
├── data_loader/
│   ├── sigmf_loader.py
│   ├── preprocess.py
│
├── models/
│   ├── cnn_encoder.py
│   ├── classifier.py
│
├── open_set/
│   ├── unknown_detection.py
│   ├── clustering.py
│
├── evaluation/
│   ├── metrics.py
│   ├── visualization.py
│
├── experiments/
│   ├── run_baseline.py
│   ├── run_open_set.py
│
├── configs/
│   ├── experiment.yaml
│
├── README.md
└── .gitignore

---

## Team Contribution Model

This project is developed with equal software involvement across all team members. Each contributor is responsible for implementing and integrating a core component of the machine learning pipeline, ensuring that all members actively participate in data processing, modeling, experimentation, and analysis.

---

## Scope and Limitations

- Unknown signals are simulated through held-out transmitter devices  
- No real-time or live SDR capture is performed  
- Results are valid within controlled experimental conditions using public datasets  

These limitations are explicitly acknowledged and discussed as part of the research outcomes.

---

## Intended Contributions

- Empirical evidence highlighting the limitations of closed-set RF classification  
- A reproducible experimental framework for open-set RF signal analysis  
- Insight into the structural properties of unknown RF signals  
- A foundation for future extensions involving real-time spectrum monitoring  

---

## Usage and Licensing

This repository is intended for academic and research purposes only. Users are responsible for complying with the licensing terms of the original datasets and appropriately citing them in any derived work.
