# Astrophysics Lab 2 – Exoplanet Transit Analysis of WASP-135b

This repository contains the analysis performed during an astrophysics research project focused on modeling the exoplanet transit of **WASP-135b**, a hot Jupiter orbiting a sun-like star. The study uses photometric data from two sources:  
- **TESS** (Transiting Exoplanet Survey Satellite)  
- **TASTE** (The Asiago Search for Transit Timing Variation of Exoplanets)

The project was conducted as part of a laboratory course and includes both observational and computational components. The analysis was divided into two main phases: TASTE and TESS.

---

## TASTE Analysis

TASTE is a ground-based observational program carried out using the Copernico telescope at the Asiago Astrophysical Observatory. During the lab course, we participated in a night observation session at Asiago, where we recorded transit events. For our group, the assigned target was **WASP-135b**.

The dataset used in this section originates from previous TASTE observations. The analysis includes standard image calibration steps:
- **Bias and flat-field correction** using median-combined frames  
- **Aperture photometry** for flux extraction  
- **Barycentric Julian Date (BJD)** correction to account for light-travel time

The provided Python scripts, including the use of the `PyORBIT` (Malavolta 2016) package, were developed and guided by Prof. Luca Malavolta. This part of the project was carried out in collaboration with **Valerio Campobasso** and **Alex Fahlman**. Their contributions, along with the support from Prof. Malavolta, are gratefully acknowledged.

---

## TESS Analysis

The TESS data analysis was conducted in three major steps:

### 1. Light Curve Extraction and Cleaning
- Retrieved SAP and PDCSAP light curves from three TESS sectors  
- Applied quality flag filtering to isolate the most reliable data points  
- Visualized raw and corrected fluxes, marking expected transit times

### 2. Detrending Stellar and Instrumental Variability
- Applied time-series detrending using the `wotan` package  
- Tested two filtering methods: `biweight` (robust median-like estimator) and `hspline` (Huber spline)  
- Compared the effectiveness of both methods through visual inspection

### 3. Transit Detection and Modeling
- Detected transit signals using Box Least Squares (BLS) and Transit Least Squares (TLS) algorithms  
- Performed detailed fitting with TLS, which provided higher accuracy  
- Estimated the orbital period, which could not be determined from TASTE due to its single-transit observation  
- Calculated limb darkening coefficients using stellar parameters from the Exoplanet Archive  
- Used results as priors in a Bayesian MCMC analysis with `PyORBIT` to fit both TESS and TASTE light curves  

The final fit includes residual plots and corner plots (see Figures 9 and 10 in the report). The orbital parameters derived from our fit are compared with literature values (Spake et al. 2016) in Table 1.

---

## Repository Contents

- **TESS analysis notebooks**: Code for light curve extraction, filtering, detrending, and transit modeling  
- **TASTE reduction scripts**: Includes calibration steps and photometry  
- **PyORBIT setup**: Configuration and results from MCMC sampling and orbital fitting  
- **Final report**: A full written summary with figures and tables is available in the main branch
