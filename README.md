# Video-Based Variability Analysis and Feature Extraction

This repository provides a complete pipeline for extracting and analyzing intensity-based variability signals from `.mp4` videos. The workflow consists of two stages:

---

## 1. Clean and Detrend Time Series from Video

The first stage processes a raw video to generate a time series of grayscale intensity values. This series is normalized, detrended using a 2nd-order polynomial, and smoothed with a rolling mean.

**Steps include:**
- Reading grayscale mean intensity per video frame  
- Skipping a specified number of frames from the beginning and end  
- Normalizing intensity values using z-score or min-max methods  
- Removing global trends via 2nd-order polynomial fitting  
- Generating a detrended, smoothed signal  

**Outputs:**
- `<video_id>.csv`: per-frame data with intensity, normalized values, polynomial trend, raw detrended signal, and smoothed residuals  
- `<video_id>_plot_original_and_detrended.png`: plots of the normalized signal with trend and the detrended time series  

---

## 2. Feature Extraction from Detrended Signal

In the second stage, statistical features are extracted from the smoothed residual signal. These features support applications such as classification, process monitoring, anomaly detection, or downstream ML models.

**Extracted Features:**
- **Trend Shape:** Linear, quadratic, and cubic polynomial coefficients  
- **Frequency Analysis:** Dominant frequency and spectral entropy from the periodogram  
- **Variance Dynamics:** Range of rolling standard deviation  
- **Randomness Measures:** Sample entropy and lag-1 autocorrelation  
- **Basic Statistics:** Mean, median, min, max, and standard deviation  

**Output:**
- `<video_id>_features.csv`: one-row summary of extracted features  

---

## Installation

Make sure the following Python packages are installed:

```bash
pip install numpy pandas matplotlib opencv-python scikit-learn scipy statsmodels antropy
