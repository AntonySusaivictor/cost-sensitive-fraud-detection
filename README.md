# Cost-Sensitive Fraud Detection with Threshold Optimization

## Motivation

Financial fraud detection is characterized by extreme class imbalance and asymmetric misclassification costs. Standard machine learning models optimize statistical accuracy, leading to poor decision quality in real-world deployment. This project reframes fraud detection as a cost-minimization and decision calibration problem.

## Research Objective

The goal of this project is to develop a cost-sensitive fraud detection framework that explicitly optimizes decision thresholds under realistic financial constraints, while maintaining model interpretability.

## Methodology

The proposed framework follows five key stages:

1. Transaction stream ingestion
2. Behavioral and temporal feature extraction
3. Cost-sensitive machine learning model
4. Decision threshold optimization
5. Explainable risk decision output

## Dataset

This study uses the publicly available Credit Card Fraud Detection dataset (European cardholders). Due to licensing restrictions, the dataset is not included in this repository.

Instructions for access: see data/README.md

## Key Results

- Cost-sensitive learning improves fraud recall under extreme imbalance
- Threshold optimization significantly reduces expected cost compared to fixed thresholds
- Transaction amount is the dominant feature with temporal behavior providing signal

## Reproducibility

1. Install dependencies: pip install -r requirements.txt
2. Run the notebook: notebook/fraud_cost_sensitive.ipynb

## Repository Structure

cost-sensitive-fraud-detection/
|-- notebook/
|   -- fraud_cost_sensitive.ipynb
|-- data/
|   -- README.md
|-- paper/
|   -- phd_proposal.pdf
|-- README.md
-- requirements.txt

## Relation to PhD Research

This project represents an initial exploration of imbalanced learning and risk-optimized decision thresholds, serving as a foundation for a broader PhD research agenda on behavior-aware fraud detection systems.
