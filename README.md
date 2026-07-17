# Exoplanet Parameter Prediction

Regression models predicting exoplanet mass, radius, temperature, metallicity (log Z), and
C/O ratio from transit-depth photometry (Bessel and Sloan filter sets), built for a SUT/NARIT/
TSRI/PMU-B astronomy data science challenge ("Problem 3: Exoplanet Variable Prediction").

See the full write-up (methodology, results, and conclusions) on my portfolio site's
Research page.

## Contents

- `main_pipeline.ipynb` &mdash; data loading, cleaning (drops rows with nulls), derived features
  (density, Earth-mass/Earth-radius units), and exploratory correlation analysis.
- `predict_mass.ipynb`, `predict_radius.ipynb`, `predict_temperature.ipynb`,
  `predict_logZ.ipynb`, `predict_co_ratio.ipynb` &mdash; one notebook per target variable, each
  fitting a `PolynomialFeatures` &rarr; `StandardScaler` &rarr; `Ridge` pipeline and comparing
  Bessel-only, Sloan-only, and combined filter sets.
- `model_for_mass_input_bessel_n_sloan_Rp.pkl`, `model_for_radius_input_bessel_n_sloan.pkl` &mdash;
  trained model checkpoints for mass and radius prediction.

## Dataset

Expects `Challenge_3_100k_data.csv` (~100,000 rows of simulated transit-depth photometry) in the
working directory &mdash; not included here as it was provided by the challenge organizers, not
collected by this project. `main_pipeline.ipynb` produces `cleaned_Challenge_3_100k_data.csv`
from it, which the five `predict_*.ipynb` notebooks each load directly.

## Usage

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
jupyter notebook main_pipeline.ipynb   # run first, to produce the cleaned dataset
jupyter notebook predict_mass.ipynb    # then any of the predict_*.ipynb notebooks
```
