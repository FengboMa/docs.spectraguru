---
layout: default
title: Fast Fourier Transform
parent: Smoothening
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Smoothening/Fast_Fourier_Transform/
nav_order: 2
---

# 1D Fast Fourier Transform (FFT) Filter
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To apply 1D FFT smoothening to your data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Smoothening" toggle.
2. Select "1D Fast Fourier Transform filter" from the drop-down menu.
3. Configure parameters:
    - FFT threshold (defaults to `0.100`) - The maximum frequency to keep in your data.
    - Padding method (can be "mirror," "edge," or "zero").

## Behavior

If using the 1D Fast Fourier Transform (FFT) filter, SpectraGuru uses Numpy's [`fft.fft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.fft.html) and [`fft.ifft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.ifft.html) functions to convert your data to and from frequency space, zeroing out high frequencies in the process and removing noise. The process is as follows:
0. Pad the data based on the specified padding method.
    - "mirror" pads the data by reflecting it at its edges.
    - "edge" pads the data by repeating the data at each edge.
    - "zero" pads the data with zeros.
1. Convert padded data to frequency space using a Fast Fourier Transform. The frequency space represents your data as a sum of waves of different frequencies.
2. Remove the waves in this space that are above the threshold frequency.
3. Convert the new frequency space back into readable data using an Inverse Fast Fourier Transform.

## References

SpectraGuru uses NumPy's [`fft.fft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.fft.html) and [`fft.ifft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.ifft.html) functions for doing FFT and inverse FFT.

1. Harris, C. R., Millman, K. J., van der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., Wieser, E., Taylor, J., Berg, S., Smith, N. J., & others. (2020). Array programming with NumPy. Nature, 585(7825), 357–362. https://doi.org/10.1038/s41586-020-2649-2
