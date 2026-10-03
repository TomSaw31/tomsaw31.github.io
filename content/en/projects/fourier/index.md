---
weight: 40

title: "Fourier transform for image compression"

# Summary for listing cards
summary: "Study and implementation of the Discrete Fourier Transform with applications to image spectrum analysis and JPEG compression."

# Tags for filtering
tags:
  - Signal Processing
  - Image Compression
  - Python

# Featured image
image:
  filename: featured.png
  focal_point: Smart
  preview_only: true

# Links displayed as buttons
links:
#   - name: Demo
#     url: https://demo.example.com
#     icon: globe
  - name: Code
    url: https://github.com/TomSaw31/TER-Transformation-de-Fourier-discrete/blob/main/code/TER.ipynb
    icon: brands/github
  - name: Paper
    url: https://tomsaw31.github.io/projets_universitaires/transformee_fourier.html
    icon: document

# External link (clicking project card opens this URL)
external_link: ""

# Shorthand link fields
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Pin to top of listings
featured: true

# Draft
draft: false
---

{{< figure src="image.png" width="1500px" >}}

## Overview

This project explores the Discrete Fourier Transform (DFT) and its applications to digital signal and image processing. 
It covers the mathematical foundations of Fourier analysis, efficient computation through the Fast Fourier Transform (FFT) and the use of frequency-domain representation for image compression.

The project was carried out as a team under the supervision of Philippe Monnier, from the [Institut de Mathématiques de Toulouse](https://www.math.univ-toulouse.fr/fr/). A complementary Python notebook is provided in the links above and contains practical implementations and experiments related to the concepts studied in the project.

## Topics

- Continuous and Discrete Fourier Transforms
- Signal sampling and frequency-domain representation
- Image spectrum analysis
- Fast Fourier Transform (FFT)
- Cooley–Tukey algorithm
- Iterative FFT implementation and algorithmic complexity
- Discrete Cosine Transform (DCT)
- JPEG image compression
- Image quality evaluation (MAE, PSNR, SSIM)

## Fourier Transform and FFT

The project studies the transition from the continuous Fourier transform to its discrete counterpart and examines how the frequency spectrum can be used to analyze digital signals and images.

The Fast Fourier Transform is then studied through the Cooley-Tukey algorithm, including its recursive and iterative formulations and its reduction of the computational complexity from $O(n^2)$ for the direct DFT to $O(n \cdot log(n))$.

## Image Compression

The project applies frequency-domain techniques to image compression, with a particular focus on the Discrete Cosine Transform used in the JPEG compression pipeline.

Images are divided into blocks and transformed into the frequency domain. High-frequency components can then be selectively discarded or quantized, reducing the amount of information required while controlling the resulting loss in image quality.

## Evaluation
Several metrics are studied to evaluate the quality of compressed images:
- Mean Squared Error (MSE)
- Peak Signal-to-Noise Ratio (PSNR)
- Structural Similarity Index Measure (SSIM)

These metrics provide complementary measures of the distortion introduced by compression.

## Other contributors
<table>
  <tr>
    <td align="center">
      <a href="https://github.com/s-fraresso">
        <img src="https://github.com/s-fraresso.png" width="100" height="100" alt="s-fraresso"/><br>
        <sub><b>Sylvain Fraresso</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/fanzelda">
        <img src="https://github.com/fanzelda.png" width="100" height="100" alt="fanzelda"/><br>
        <sub><b>Gaël Jean-Albert</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/JPYasashii">
        <img src="https://github.com/JPYasashii.png" width="100" height="100" alt="JPYasashii"/><br>
        <sub><b>Titouan Martineau</b></sub>
      </a>
    </td>
  </tr>
</table>
