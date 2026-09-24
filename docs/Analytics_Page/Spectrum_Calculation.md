---
layout: default
title: Spectrum Calculation
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Spectrum_Calculation/
nav_order: 5
---

# Spectrum Calculation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Spectrum Calculation applies arithmetic to spectral intensities or shifts a spectrum along the wavenumber axis. It can use a constant or another spectrum as the intensity operand, with a preview before applying the same calculation to all spectra.

## How to use

1. Upload data, complete any preprocessing, and open **Analytics Page**.
2. Select **Spectrum Calculation** from **Select analytics plot**, then choose a target spectrum. **Average** is the default target.
3. Choose **Y-axis with constant**, **Y-axis with another spectrum**, or **X-axis shift**.
4. For a Y-axis calculation, select **Add**, **Subtract**, **Multiply**, or **Divide** and supply the constant or reference spectrum. For an X-axis shift, select **Add** or **Subtract** and enter the shift value.
5. Review the preview plot. Download its CSV, or click **Apply calculation to all spectra** to create and download a separate calculated dataset.

## Behavior

The preview shows the original target, the reference spectrum when one is used, and the calculated result. Previewing does not change the uploaded or preprocessed session data. **Apply calculation to all spectra** creates a separate dataframe; its CSV is available alongside the preview CSV.

Constant intensity inputs range from `0` to `1,000,000`; a subtraction can still produce negative output intensities. A reference spectrum is combined point by point on the same wavenumber axis, without interpolation. Division by zero is not allowed. An X-axis shift changes wavenumbers but leaves intensities unchanged; shift values may be negative.

## Method

For target intensity $I(x)$, constant $c$, and reference intensity $R(x)$, the Y-axis result is $I(x)\mathbin{\circ}c$ or $I(x)\mathbin{\circ}R(x)$, where $\circ$ is addition, subtraction, multiplication, or division. An X-axis shift instead gives $x'=x+\Delta$ or $x'=x-\Delta$ while retaining $I(x)$. Applying the operation to all spectra repeats the chosen operation for each spectrum column and returns a new dataframe.

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Target spectrum | Tunable | Average or an individual spectrum; defaults to Average |
| Calculation type | Tunable | Y-axis with constant, Y-axis with another spectrum, or X-axis shift |
| Y-axis operator | Tunable | Add, Subtract, Multiply, or Divide |
| Constant value | Tunable | `0`–`1,000,000`; defaults to `1` for multiplication/division |
| Reference spectrum | Tunable | Another available spectrum on the same wavenumber axis |
| X-axis operator and shift | Tunable | Add or Subtract a wavenumber shift; default shift `0` |
| Data export | Fixed | Preview and apply-to-all CSV files use four decimal places |

## References

1. SpectraGuru developers. [Spectrum calculation implementation](https://github.com/FengboMa/SpectraGuru_beta/blob/dev/function.py).
