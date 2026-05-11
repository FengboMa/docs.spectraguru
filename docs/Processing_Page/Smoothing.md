---
layout: default
title: Smoothing
parent: Processing Feature
grand_parent: Processing Page
has_children: true
permalink: /docs/Processing_Page/Processing_Feature/Smoothing/
nav_order: 4
---

# Smoothing
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Smoothing parent page groups algorithms that reduce short-scale noise before downstream processing or analytics. SpectraGuru includes Savitzky-Golay filtering for polynomial local smoothing, FFT filtering for low-pass frequency-domain smoothing, Median filter for spike-resistant local smoothing, and Wavelet denoising for coefficient-shrinkage smoothing.

## Behavior

The Smoothing function applies one selected smoothing method to refine spectral data:
- The Savitzky-Golay filter smooths spectra using a polynomial fit within a defined window.
- The 1D FFT filter removes high-frequency noise by filtering spectra in the frequency domain based on a cutoff threshold.
- The Median filter replaces each point with a local median value to reduce isolated spikes.
- Wavelet denoising shrinks wavelet detail coefficients and reconstructs smoother spectra.
