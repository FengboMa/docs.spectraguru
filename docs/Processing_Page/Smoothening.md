---
layout: default
title: Smoothening
parent: Processing Feature
grand_parent: Processing Page
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

## How to Use

To apply smoothening to your spectral data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Smoothening" toggle.
2. Select a smoothening method from the drop-down menu:
    - Savitzky-Golay filter
    - 1D Fast Fourier Transform (FFT) filter
3. Configure parameters based on the selected method:
    - For Savitzky-Golay, set the window length (defaults to `15`) and the polynomial order (defaults to `2`). The polynomial order should be less than the window length.
    - For 1D FFT, set the FFT threshold (defaults to `0.100`) and the padding method (can be "mirror," "edge," or "zero").

## Behavior

The Smoothening function applies either the Savitzky-Golay filter or the 1D Fast Fourier Transform filter to refine spectral data:
- The Savitzky-Golay filter smooths spectra using a polynomial fit within a defined window.
- The 1D FFT filter removes high-frequency noise by filtering spectra in the frequency domain based on a cutoff threshold.

## Method

- If using the Savitzky-Golay filter, the smoothening function applies SciPy's implementation [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) to each spectrum, which works as follows:
    0. For each Ramanshift value $x$, consider the values between $x-\frac{w}{2}$ and $x+\frac{w}{2}$, where $w$ is the window length.
    1. Try to find the polynomial with order $d$ that best fits with the data centered around $x$. Mathematically speaking, this can be thought of as a minimization of the following expression as the coefficients $a_i$ vary:

        $$
        \sum_{j=-w/2}^{w/2} \left(I(x+j)-\sum_{i=0}^d \left(a_i (x+j)^i\right)\right)^2
        $$

        where $I(x)$ is the actual intensity at Ramanshift $x$.
    2. Minimize the above expression using least squares optimization on the coefficients $a_i$. Then use the polynomial fit to find the filtered intensity at Ramanshift $x$.
    3. Repeat this process for all $x$.
- If using the 1D Fast Fourier Transform (FFT) filter, SpectraGuru uses Numpy's [`fft.fft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.fft.html) and [`fft.ifft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.ifft.html) functions to convert your data to and from frequency space, zeroing out high frequencies in the process and removing noise. The process is as follows:
    0. Pad the data based on the specified padding method.
        - "mirror" pads the data by reflecting it at its edges.
        - "edge" pads the data by repeating the data at each edge.
        - "zero" pads the data with zeros.
    1. Convert padded data to frequency space using a Fast Fourier Transform. The frequency space represents your data as a sum of waves of different frequencies.
    2. Remove the waves in this space that are above the threshold frequency.
    3. Convert the new frequency space back into readable data using an Inverse Fast Fourier Transform.

## References

SpectraGuru uses SciPy's [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) function for Savitzky-Golay smoothening, as well as NumPy's [`fft.fft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.fft.html) and [`fft.ifft`](https://numpy.org/doc/stable/reference/generated/numpy.fft.ifft.html) functions for doing FFT and inverse FFT.

1. Harris, C. R., Millman, K. J., van der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., Wieser, E., Taylor, J., Berg, S., Smith, N. J., & others. (2020). Array programming with NumPy. Nature, 585(7825), 357–362. https://doi.org/10.1038/s41586-020-2649-2

2. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2
