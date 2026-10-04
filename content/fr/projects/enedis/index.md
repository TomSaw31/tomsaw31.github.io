---
weight: 20

title: "Challenge Data Enedis"

# Summary for listing cards
summary: "A team entry to the Enedis Data Challenge reconstructing missing values in synthetic Linky load curves, ranked 13th with a MAE of 79.15 against 104.54 for the linear-interpolation benchmark"

# Tags for filtering
tags:
  - Machine Learning
  - Time Series Imputation
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
    url: https://github.com/TomSaw31/IA-Hackathon-Enedis/blob/main/Hackathon.ipynb
    icon: brands/github
  # - name: Paper
  #   url: https://tomsaw31.github.io/projets_universitaires/transformee_fourier.html
  #   icon: document

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

{{< figure src="featured.png" width="500px" >}}

## Overview

This project was developed as a team of two for the Data Challenge organized by Enedis, based on the Linky smart meters. Metering data can be lost during measurement, transmission or storage, and the missing values must be completed without using real consumers' curves (GDPR). The challenge therefore relies on about 69,000 synthetic load curves generated with DeepCourbogen, 1,000 of which have randomly deleted values.

The goal is to propose replacement values for the missing data in these 1,000 curves. Submissions are evaluated with the Mean Absolute Error (MAE) computed only on the missing values, by comparing the submitted curves with ground-truth values that are hidden from the participants. The reference is a benchmark based on linear interpolation (MAE of 104.54).

Our best solution reaches a MAE of about 79.15, roughly 24% lower than the benchmark, which placed us 13th on the public leaderboard. The notebook is available in the links above.

## Topics

- Time series imputation
- Half-hourly load curves and daily consumption patterns
- Feature engineering from day and time of day
- Polynomial regression
- Denoising autoencoder (1D convolutional)
- Random Forest regression
- Gradient boosting (XGBoost) with MAE objective
- Hyperparameter tuning
- Model evaluation (MAE, R²)

## Data and Preprocessing

The training set contains 20,000 complete curves and 1,000 curves with gaps, sampled every 30 minutes over several weeks (1,057 time steps per curve). Each time step is described by its day index and its half-hour of the day, which makes the daily periodicity of consumption explicit. One curve of the complete set containing missing values was corrected beforehand.

Since the true values of the gaps are known for the training set, each approach could be evaluated locally (MAE and R²) before being submitted.

Several families of models were explored and compared:

- **Polynomial regression**: a first attempt fitted a degree-5 polynomial on the half-hour of the day across all curves, then a second one fitted a separate model per curve using the day, the time and a periodic feature as inputs.
- **Denoising autoencoder**: a 1D convolutional autoencoder trained on the 20,000 complete curves, normalized per household, with artificially masked values, then applied to the incomplete curves to reconstruct the missing points. It is the only approach using the full dataset, since a neural network requires a large training set.
- **Random Forest**: one model per curve, trained only on its known points with the day and the time as features, with a MAE splitting criterion.
- **XGBoost**: the same per-curve setup with gradient-boosted trees optimized for the absolute error, whose hyperparameters (depth, learning rate, regularization, subsampling...) were tuned by hand. This is the model used for the final submission.

An interesting outcome is that the best results came from classical regression models relying on a single curve at a time, rather than from the neural network trained on the whole dataset. Predictions are clipped to non-negative values since they represent energy consumption, and only the missing values are replaced, the known measurements being left untouched.


## Results

On the public leaderboard, the final XGBoost submission reaches a MAE of 79.15, compared with 104.54 for the linear-interpolation benchmark, which corresponds to the 13th place.

## Other contributors
<table>
  <tr>
    <td align="center">
      <a href="https://github.com/s-fraresso">
        <img src="https://github.com/s-fraresso.png" width="100" height="100" alt="s-fraresso"/><br>
        <sub><b>Sylvain Fraresso</b></sub>
      </a>
    </td>
  </tr>
</table>