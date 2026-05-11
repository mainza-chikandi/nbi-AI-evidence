# nbi-AI-evidence

Explainable AI-powered preliminary bridge form selection using National Bridge Inventory evidence.

This repository contains the source code used for the dissertation:

**Explainable AI-Powered Preliminary Bridge Form and Span Scheme Selection Using Inventory Evidence**

The project develops an explainable machine learning workflow for supporting preliminary bridge form selection using the United States National Bridge Inventory (NBI). The current implementation focuses on **Stage One** of the proposed framework: predicting bridge form family as **girder/beam**, **truss**, **arch**, or **rigid frame**.

---

## 1. Project Overview

Preliminary bridge design involves early decisions about structural form and span arrangement. These decisions strongly influence constructability, cost, durability and long-term performance. Traditionally, such decisions rely on engineering judgement, precedent projects and span-range guidance.

This project explores whether large-scale bridge inventory data can provide empirical evidence for supporting these early decisions. Using the National Bridge Inventory, the workflow:

1. Loads and cleans NBI bridge records.
2. Maps detailed NBI structure-type codes into preliminary bridge form families.
3. Performs exploratory data analysis.
4. Trains machine learning models for bridge form classification.
5. Optimises CatBoost hyperparameters using Optuna.
6. Evaluates the final model using accuracy, macro-F1, weighted F1 and confusion matrices.
7. Applies SHAP explainability to interpret model predictions.
8. Demonstrates an example preliminary bridge form prediction.

---

## 2. Repository Structure

```text
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
├── chapter4_outputs/
│   ├── classification_report_stage1.csv
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
