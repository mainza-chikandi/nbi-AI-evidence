# nbi-AI-evidence

Source code repository for the dissertation:

**Explainable AI-Powered Preliminary Bridge Form and Span Scheme Selection Using Inventory Evidence**

**Author:** Chikandi Mainza  
**Degree:** Master of Engineering in Structural Engineering  
**Institution:** University of Zambia  
**Location:** Lusaka, Zambia  
**Year:** 2025  
**Supervisor:** Dr. Michael Mulenga  

---

## Dissertation Context

This repository contains the source code used to support the dissertation submitted to the University of Zambia in partial fulfilment of the requirements for the degree of **Master of Engineering in Structural Engineering**.

The dissertation develops an explainable artificial intelligence framework for supporting preliminary bridge form and span scheme selection using inventory-scale bridge data. The current implementation focuses mainly on **Stage One** of the proposed framework: predicting bridge form family using the United States National Bridge Inventory.

The bridge form families considered in the current implementation are:

    girder_beam
    truss
    arch
    rigid_frame

The broader research framework also proposes a second stage for span scheme prediction, including span-count band and maximum-span band selection.

---

## Copyright and Use

Copyright © 2025 Chikandi Mainza.

All rights reserved. No part of the dissertation work, figures, tables, text, models, or associated research outputs may be reproduced, distributed, modified, or used without prior written consent from the author or the University of Zambia.

The code in this repository is provided for academic transparency and reproducibility of the dissertation workflow. It is not intended for commercial use or for direct application as a professional bridge design tool without independent engineering verification.

Users may view the code for educational and research reference purposes. Any reuse, adaptation, redistribution, or citation of this work should acknowledge the author and the dissertation.

---

## Important Disclaimer

This repository supports a research workflow only.

The trained models, scripts, figures, and example outputs are intended for preliminary decision-support demonstration. They must not be used as a substitute for professional engineering judgement, detailed structural analysis, site investigation, hydraulic assessment, geotechnical design, cost analysis, constructability review, environmental assessment, or compliance with applicable bridge design standards.

Final bridge design decisions must be made by qualified engineers using relevant codes, standards, site-specific investigations, and professional judgement.

---

## Project Overview

Preliminary bridge design involves early decisions about structural form and span arrangement. These decisions strongly influence constructability, cost, durability, maintenance, and long-term performance. Traditionally, such decisions rely on engineering judgement, precedent projects, design specifications, and span-range guidance.

This project explores whether large-scale bridge inventory data can provide empirical evidence for supporting these early-stage decisions. Using the National Bridge Inventory, the workflow:

1. Loads and cleans NBI bridge records.
2. Maps detailed NBI structure-type codes into preliminary bridge form families.
3. Performs exploratory data analysis.
4. Defines modelling-ready input variables and target labels.
5. Trains machine learning models for bridge form classification.
6. Optimises CatBoost hyperparameters using Optuna.
7. Evaluates the final model using accuracy, macro-F1, weighted F1-score, confusion matrices, and class-wise metrics.
8. Applies SHAP explainability to interpret model predictions.
9. Demonstrates an example preliminary bridge form prediction using a hypothetical bridge case.

---

## Repository Structure

The repository may be organised as follows:

    nbi-AI-evidence/
    │
    ├── data/
    │   ├── raw/
    │   │   └── NTAD_National_Bridge_Inventory.csv
    │   └── processed/
    │       ├── NBI_preliminary_design_clean.csv
    │       └── NBI_10k_prelim_design.csv
    │
    ├── notebooks/
    │   ├── 01_data_cleaning_and_eda.ipynb
    │   ├── 02_catboost_optuna_training.ipynb
    │   ├── 03_final_model_and_chapter4_figures.ipynb
    │   └── 04_appendix_example_application.ipynb
    │
    ├── scripts/
    │   ├── build_clean_dataset.py
    │   ├── eda_outputs.py
    │   ├── train_catboost_optuna.py
    │   ├── final_model_figures.py
    │   └── appendix_example.py
    │
    ├── eda_outputs/
    │   ├── descriptive_statistics.csv
    │   ├── correlation_matrix.csv
    │   ├── correlation_matrix.png
    │   └── target_distributions_3x3_grid.png
    │
    ├── chapter4_outputs/
    │   ├── classification_report_stage1.csv
    │   ├── catboost_feature_importance_stage1.csv
    │   ├── figure_4_1_class_distribution.png
    │   ├── figure_4_2_confusion_matrix.png
    │   ├── figure_4_3_classwise_metrics.png
    │   ├── figure_4_4_catboost_feature_importance.png
    │   ├── SHAP_stage1_summary_1x2.png
    │   ├── SHAP_dependence_interaction_top9_3x3.png
    │   └── final_catboost_stage1_form_family_model.cbm
    │
    ├── appendix_example_outputs/
    │   ├── example_input_case.csv
    │   ├── example_prediction_probabilities.csv
    │   ├── example_local_shap_explanation.csv
    │   ├── figure_A1_prediction_probabilities.png
    │   ├── figure_A2_local_shap_bar.png
    │   ├── figure_A3_shap_waterfall.png
    │   └── example_prediction_summary.txt
    │
    ├── requirements.txt
    ├── README.md
    └── LICENSE

The exact folder structure may differ depending on whether the workflow is run through scripts, notebooks, or both.

---

## Data Source

The dataset used in this project is the National Bridge Inventory obtained from the Bureau of Transportation Statistics geospatial data portal.

Dataset source:

    https://geodata.bts.gov/datasets/national-bridge-inventory/

The raw NBI file is not necessarily included in this repository because of file size. Users should download the dataset from the official source and place it in:

    data/raw/

Alternatively, the file path in the scripts can be updated to point to the local location of the downloaded NBI CSV file.
