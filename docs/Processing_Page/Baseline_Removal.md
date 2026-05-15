---
layout: default
title: Baseline Removal
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/
has_children: true
nav_order: 5
---

# Baseline Removal
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Baseline Removal parent page groups algorithms that estimate and subtract broad background trends from spectra. SpectraGuru includes AirPLS for adaptive reweighted smoothing, ModPoly for polynomial baseline fitting, Gaussian-Lorentzian fitting for range-based curve fitting, SNIP for iterative peak clipping, and ALS for asymmetric penalized least-squares smoothing.

## Behavior

This feature should identify and remove unwanted baselines from spectral data using one selected algorithm:
- AirPLS: Iteratively adjusts the baseline using a penalized least squares approach to smooth the background while preserving peaks. 
- ModPoly: Fits a polynomial function to estimate and subtract the baseline from the spectra.
- Gaussian-Lorentzian fitting: Uses a Gaussian-Lorentzian hybrid to fit the data and find a baseline.
- SNIP: Iteratively clips peaks from a transformed spectrum to estimate background.
- ALS: Fits a smooth asymmetric least-squares baseline below peaks.
