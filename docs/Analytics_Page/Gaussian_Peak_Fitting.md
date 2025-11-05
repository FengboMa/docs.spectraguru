---
layout: default
title: Gaussian Peak Fitting
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Gaussian_Peak_Fitting/
nav_order: 6
---

# Gaussian Peak Fitting
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

SpectraGuru offers a Gaussian Peak Fitting feature, which fits Gaussian curves (normal distributions) to your data around the most prominent peaks. This feature is useful for decompsing important peaks into simplified components that can be used for further analysis, including AI training. Users can also introduce a constant baseline, which is helpful for peaks whose bases are highly raised above the `intensity=0` axis.

## How to Use

0. In the analytics page, after processing your data, select "Gaussian Peak Fitting" from the dropdown menu on the left sidebar.
1. Use the upper textbox to specify the number of peaks in your data to analyze (defaults to `1`, maximum is `20`).
2. Use the lower textbox to specify the number of total Gaussian curves to fit to these peaks (defaults to `1`, maximum is `30`)
3. If you would like to introduce a constant baseline, turn on the toggle labeled "Use constant model" and input the baseline intensity into the textbox that appears.

## Behavior

- Overview: The goal of this feature is to generate Gaussian curves which match closely to your data (specifically, the average spectrum of the data you selected) around the most prominent peaks. The number of peaks $k$ and the number of total Gaussian curves $n$ is specified by the user prior to calculating the optimal fit. Gaussian curves are described by the following mathematical expression:

    $$
    A e^{-\frac{(x-\mu)^2}{2\sigma^2}}
    $$

    where $A$ is the amplitude of the curve, $\mu$ is the center, and $\sigma$ is the standard deviation.
- Partitioning: Before finding the optimal fit, the $n$ Gaussian curves are partitioned into $k$ subsets, where each subset corresponds to one of the $k$ most prominent peaks in your data, such that:
    0. The size of each subset is at least $1$ if $n \ge k$ (i.e. each peak gets at least one Gaussian curve).
    1. The number of Gaussian curves assigned to a peak is roughly proportional to that peak's prominence.
    2. Leftover curves from rounding are distributed as evenly as possible, with priority going to the most prominent peaks.
    For more about peak prominence, see our [Peak Identification docs](/docs.spectraguru/docs/Analytics_Page/Analytics_Features/Peak_Identification/).
- Optimization method: To find the optimal fitting of $n_P$ Gaussian curves to a given peak $P$, SpectraGuru defines a cost function and uses SciPy's [`optimize.least_squares`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.least_squares.html) to minimize the cost function. The inputs of this function are the respective amplitudes ($A$), center points ($\mu$), and standard deviations ($\sigma$) of each Gaussian curve. This means that there are $3 n_P$ parameters to tweak to optimize the fitting for $P$.
    The cost function $C$ is defined as follows:

    $$
    C=\sum_x S(x)\lvert I(x)-\sum_{i=0}^{n_P}\left(A_i e^{-\frac{(x-\mu_i)^2}{2{\sigma_i}^2}}\right)\rvert
    $$

    where $I(x)$ is the intensity at Ramanshift $x$, and $S(x)$ is the following modified sigmoid function:

    $$
    S(x)=\frac{1}{1+e^{\lvert x-c_P\rvert-\frac{w_P}{2}}}
    $$

    where $c_P$ is the center of the peak and $w_P$ is the width of the peak. The purpose of the modified sigmoid is to prevent the Gaussian curves from trying to fit to data far from the peak itself ($S(x)$ is close to $0$ when $\lvert x-c_P\rvert$ is far from $0$). This ensures that irrelevant data does not interfere with the fit around the peak.
- Display: After calculating the optimal fit for each peak, the final results are displayed on a plot alongside the original data. The sum of all Gaussian curves is also plotted with the label `GSUM`. Underneath the plot is a table containing the resulting fit data, where Gaussian curve intensities are rounded to four decimal places. You can download this data as a CSV file by clicking the button labeled "Download Gaussian Fit data as CSV."

## References

SpectraGuru uses SciPy's [`optimize.least_squares`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.least_squares.html) function to find the optimal Gaussian curves for your data.

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2
    