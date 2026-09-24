---
layout: default
title: Machine Learning Feature
parent: Analytics Page
has_children: true
nav_order: 7
---

# Machine Learning Feature
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Machine Learning Feature groups algorithms that reduce dimensionality, cluster spectra, or classify labeled spectra. Principal Components Analysis (PCA) and T-SNE Dimensionality Reduction help visualize high-dimensional spectra, Hierarchically-clustered Heatmap groups similar spectra, and Random Forest(RF), K-Nearest Neighbors(KNN), and Support Vector Machine(SVM) perform supervised classification from labels created during upload.

## Label setup

1. Open **Data Upload**.
2. Set **Number of classes**. Use one class for unlabeled exploratory workflows, or two or more classes when you plan to run supervised classification.
3. Load or query data inside each **Class** expander. If you upload more than one class, SpectraGuru interpolates the classes to a shared Raman shift grid before combining them.
4. Use the label editor after upload to review the **Spectrum** and **Label** columns. Labels are stored as the class values used by PCA coloring and by Random Forest, KNN, and SVM classification.
5. Continue to **Processing Page** if preprocessing is needed, then open **Analytics Page** and select a machine learning feature from **Select Analytics Plot**.

Classification pages require every selected spectrum to have a label and require at least two unique classes.

## Included methods

| Method | Use |
| --- | --- |
| [Hierarchically-clustered Heatmap]({{ '/docs/Analytics_Page/Analytics_Features/Clustermap/' | relative_url }}) | Ward-linkage clustering and heatmap/dendrogram display |
| [Principal Components Analysis (PCA)]({{ '/docs/Analytics_Page/Analytics_Features/Principal_Component_Analysis/' | relative_url }}) | Linear dimensionality reduction and loading inspection |
| [T-SNE Dimensionality Reduction]({{ '/docs/Analytics_Page/Analytics_Features/T-SNE/' | relative_url }}) | Nonlinear 2D neighborhood visualization |
| [Random Forest(RF) Classification]({{ '/docs/Analytics_Page/Machine_Learning_Feature/Random_Forest_Classification/' | relative_url }}) | Supervised ensemble classification |
| [K-Nearest Neighbors(KNN) Classification]({{ '/docs/Analytics_Page/Machine_Learning_Feature/KNN_Classification/' | relative_url }}) | Supervised distance-based classification |
| [Support Vector Machine(SVM) Classification]({{ '/docs/Analytics_Page/Machine_Learning_Feature/SVM_Classification/' | relative_url }}) | Supervised margin-based classification |
