---
layout: default
title: Fast Fourier Transform (FFT) analysis
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Fast_Fourier_Transform/
nav_order: 4
---

# Fast Fourier Transform (FFT) analysis
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Fast Fourier Transform (FFT) analysis converts a selected spectrum from the Raman shift domain into the frequency domain so periodic or high-frequency structure can be inspected.

## How to use

1. Upload data and finish preprocessing if needed.
2. Open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Fast Fourier Transform (FFT) analysis**.
4. Use **Select spectrum for FFT** to choose **Average** or an individual spectrum.
5. Optionally enable **Subtract average value before FFT**.
6. Review the FFT plots and use **Download FFT analysis data as CSV** if you need the transformed data.

## Behavior

Analytics FFT converts the selected spectrum from the Raman shift domain into the frequency domain. The page shows six FFT views in this order: Amplitude and Phase, Power and Real + Imaginary, then Real and Imaginary. It also exports a CSV containing the FFT data. If **Subtract average value before FFT** is enabled, the selected intensity trace is mean-centered before the transform.

## Method

SpectraGuru computes the discrete Fourier transform of the selected intensity values:

$$X_k = \sum_{n=0}^{N-1} x_n e^{-2\pi i kn/N}$$

When mean subtraction is enabled, the signal becomes:

$$x'_n = x_n - \bar{x}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Select spectrum for FFT | Tunable | `Average` or any selected sample column |
| Subtract average value before FFT | Tunable | Boolean toggle, default `False` |
| Input x-axis | Fixed | Raman shift column from the current Analytics dataset |
| Output | Fixed | Six FFT plots plus downloadable CSV |

## References

1. Cooley, J. W., & Tukey, J. W. (1965). An algorithm for the machine calculation of complex Fourier series. *Mathematics of Computation*, 19(90), 297-301. https://doi.org/10.1090/S0025-5718-1965-0178586-1
2. NumPy Developers. Discrete Fourier Transform. https://numpy.org/doc/stable/reference/routines.fft.html
