---
layout: default
title: Spectrum Simulation
parent: Toolbox Page
permalink: /docs/Toolbox_Page/Spectra_Simulation/
nav_order: 1
---

# Spectrum Simulation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Spectrum Simulation generates synthetic Raman-like spectra with configurable peak structure, optional baseline, optional noise, and downloadable output.

## How to use

1. Open **Toolbox Page**.
2. In **Select Tool**, choose **Spectrum Simulation**.
3. Set **Number of Spectra to Generate**, **Scale**, and **Select Spectra Structure**.
4. Configure the structure-specific controls for **Distinct**, **Joint**, or **Consecutive** peaks.
5. Optionally enable **Use Baseline** and choose **Polynomial**, **Exponential**, **Gaussian**, or **Sigmoidal** baseline controls.
6. Optionally enable **Use Noise** and set **Noise Amplifier**.
7. Click **Generate Spectra** and download the result with **Download Simulated data as CSV**.

## Behavior

Spectrum Simulation creates synthetic Raman-like spectra over the default Raman shift range. Peaks are generated as random Gaussian peaks, optionally arranged as separated peaks, paired regions, or consecutive overlapping regions. The output page shows an interactive line chart and a downloadable CSV.

## Method

Each simulated peak is Gaussian:

$$g(x)=a\exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$

After peak generation, SpectraGuru normalizes and scales the spectra:

$$y_{\text{out}} = s\frac{y-\min(y)}{\max(y)-\min(y)}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Number of Spectra to Generate | Tunable | Default `1`, range `1`-`50` |
| Scale | Tunable | Default `1.0`, range `0.01`-`10000.0` |
| Select Spectra Structure | Tunable | `Distinct`, `Joint`, or `Consecutive` |
| Distinct controls | Tunable | Average Number of Peaks, Peak Number Variance, Separation Factor |
| Joint controls | Tunable | Average Number of Regions, Region Number Variance, Clustering Factor |
| Consecutive controls | Tunable | Average Peaks per Region, Per Region Peak Variance, Clustering Factor |
| Baseline | Tunable | Optional Polynomial, Exponential, Gaussian, or Sigmoidal baseline |
| Noise | Tunable | Optional Gaussian noise with Noise Amplifier |
| Raman shift range | Fixed | `400` to `2000` |
| Resolution | Fixed | `1601` points |
| Peak amplitude range | Fixed | `5` to `100` before normalization |
| Peak width range | Fixed | `10` to `40` |

## References

1. SpectraGuru implementation, `generate_spectra`, self-implemented synthetic Gaussian spectra generator.
2. NumPy Developers. Random sampling routines. https://numpy.org/doc/stable/reference/random/index.html
