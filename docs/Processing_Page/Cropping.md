---
layout: default
title: Cropping
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Cropping/
nav_order: 2
---

# Cropping
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The *crop* function in SpectraGuru is an essential tool designed to allow users to select a specific spectral range for analysis. This feature helps to exclude irrelevant data and focus on a targeted region of interest. By adjusting the crop range, users can refine their spectral data before performing further analysis.

## How to Use

To crop your data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Crop" toggle.
2. Adjust the crop range by defining the minimum and maximum wavenumber values. You can use either the slider or the textboxes to set these values.
3. Click "Process" to update the spectral range.

## Behavior

The expected behavior of the crop function is to remove spectral data not in the range of interest. The range is set using either:
- A slider with two parameters (min and max) between the original range.
- A pair of textboxes: one to set the minimum Ramanshift value, and another to set the maximum.
