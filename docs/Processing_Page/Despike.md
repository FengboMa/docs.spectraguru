---
layout: default
title: Despike
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Despike/
nav_order: 3
---

# Despike
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Despike function, sometimes referred to as spike removal, is an essential tool in the application designed to automatically detect and remove spikes in spectral data, which are often caused by noise or transient artifacts during data acquisition (Cosmic ray spikes can also be removed with this function.) 

## How to Use

To remove spikes in your data:

0. Upload data and select spectra you want to process.
1. Navigate to sidebar and turn on the "Despike" toggle.
    - Set Despike threshold (default to 300)
    - Set Despike zap length / window size (default to 11)
2. Click on Process button on the bottom of the sidebar.

## Behavior

The expected behavior of the Despike function is to scan each spectrum for abrupt increases in intensity, which are indicative of spikes. When such a spike is detected, the function replaces the affected portion of the spectrum with a smooth linear interpolation, effectively "despiking" the data. This process is controlled by two key parameters: 

- Despike threshold: Despike threshold determines the sensitivity of spike detection, a peak higher than the threshold, yet within Despike zap length / window size are being considered as a spike. Thus being removed.
- Despike zap length / window size: The parameter defines the width of the window used to identify and correct spikes.


## Method

For each spectrum in the dataset, the function iterates through the data using a sliding window approach defined by the `zap_length` parameter. Within each window, the function calculates the difference between the observed intensity values and a linearly interpolated line drawn across the window. This difference is known as the residual, denoted as $\text{resid}$. If any residual value exceeds a predefined threshold, it is considered indicative of a spike. The function then corrects the spike by replacing the affected intensity values with the corresponding values from the interpolated line, ensuring a smooth transition across the window. The mathematical formulation for this process is as follows:

$$
I'(x_j) = 
\begin{cases} 
I(x_j) & \text{if } \text{resid}(x_j) < \text{Threshold} \\
\text{Linear Interpolation}(I(x_{j}), I(x_{j+L})) & \text{if } \text{resid}(x_j) \geq \text{Threshold}
\end{cases}
$$

In this equation, $I(x_j)$ represents the original intensity at position $x_j$, $I'(x_j)$ is the corrected intensity after despiking, $\text{resid}(x_j)$ is the residual difference, $\text{Threshold}$ is the spike detection threshold, and $L$ denotes the `zap_length`. The linear interpolation is calculated over the range of the zap length, ensuring that any detected spikes are replaced with a smooth, continuous line that better reflects the underlying spectral data.
