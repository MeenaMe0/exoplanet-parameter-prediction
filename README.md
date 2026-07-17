# Exoplanet Parameter Prediction

Regression models predicting exoplanet mass, radius, temperature, metallicity (log Z), and
C/O ratio from transit-depth photometry (Bessel and Sloan filter sets), built for a SUT/NARIT/
TSRI/PMU-B astronomy data science challenge ("Problem 3: Exoplanet Variable Prediction").

See the full write-up (methodology, results, and conclusions) on my portfolio site's
Research page.

## Structure

```
notebooks/
  01_data_cleaning.ipynb      -- load, clean (drop nulls), derive features (density,
                                  Earth-mass/Earth-radius units), exploratory correlation analysis
  02_predict_mass.ipynb       -- Mp: PolynomialFeatures -> StandardScaler -> Ridge pipeline
  03_predict_radius.ipynb     -- Rp: same pipeline
  04_predict_temperature.ipynb -- Tp: same pipeline
  05_predict_logZ.ipynb       -- log Z: same pipeline
  06_predict_co_ratio.ipynb   -- C/O: same pipeline
models/
  mass_model.pkl              -- trained checkpoint for mass prediction
  radius_model.pkl            -- trained checkpoint for radius prediction
figures/
  filterresponse.png, output_rp*.png  -- filter response curves, results, feature importance,
                                          and learning curve plots referenced in the write-up
```

Each `predict_*` notebook independently compares Bessel-only, Sloan-only, and combined filter
sets as input features for its target variable.

## Dataset

Expects `Challenge_3_100k_data.csv` (~100,000 rows of simulated transit-depth photometry) in
`notebooks/` &mdash; not included here as it was provided by the challenge organizers, not
collected by this project. `01_data_cleaning.ipynb` produces `cleaned_Challenge_3_100k_data.csv`
from it, which notebooks 02&ndash;06 each load directly.

## Usage

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
cd notebooks
jupyter notebook 01_data_cleaning.ipynb   # run first, to produce the cleaned dataset
jupyter notebook 02_predict_mass.ipynb    # then any of the numbered notebooks
```
