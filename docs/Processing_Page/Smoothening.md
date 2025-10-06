---
layout: default
title: Smoothening
parent: Processing Feature
grand_parent: Processing Page
has_children: true
permalink: /docs/Processing_Page/Processing_Feature/Smoothening/
nav_order: 4
---

# Smoothening
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The *smoothening* function in SpectraGuru is a crucial tool for reducing noise and enhancing spectral signals. By averaging adjacent data points, it helps produce a clearer representation of spectral data, making trends more discernible and reducing fluctuations caused by noise.

## Behavior

The Smoothening function applies either the Savitzky-Golay filter or the 1D Fast Fourier Transform filter to refine spectral data:
- The Savitzky-Golay filter smooths spectra using a polynomial fit within a defined window.
- The 1D FFT filter removes high-frequency noise by filtering spectra in the frequency domain based on a cutoff threshold.

