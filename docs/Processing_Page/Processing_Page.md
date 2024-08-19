---
layout: default
title: Processing Page
nav_order: 5
has_children: true
permalink: /docs/Processing_Page
---

# Processing Page

Use this page to Process and visualize spectra you uploaded. This page designed to process and visualize spectral data, particularly Raman spectroscopy data. The application offers users a comprehensive suite of tools to manipulate their spectral data through a sidebar interface, where they can select various processing steps, such as interpolation, cropping, despiking, smoothening, baseline removal, normalization, and outlier removal. These tools allow users to refine their spectral data, ensuring that it is well-prepared for analysis and visualization.

## Processing Feature

Overview of processing feature on this page,

| Feature             | Sub Functions                                      | More Info |
|---------------------|---------------------------------------------------|-----------|
| Interpolation       |               |           |
| Cropping            |                       |           |
| Despiking           | Despike with Threshold, Zap Length                      |           |
| Smoothening         | Savitzky-Golay Filter, 1D Fast Fourier Transform    |           |
| Baseline Removal    | airPLS, ModPoly                                    |           |
| Normalization       | Normalize by Area, Normalize by Peak, Min Max Normalize |      |
| Outlier Removal     | Single Threshold, Distance Threshold, Correlation Threshold |    |

Please find more useful information in child files.

## Visualization 

The application also provides a flexible and interactive visualization platform using [Altair](https://altair-viz.github.io/index.html). Users can plot their processed spectra, choose specific spectra for visualization, and toggle between a fast plotting mode for large datasets and a more detailed interactive mode for smaller datasets.