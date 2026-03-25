# ✈️ SARIMA Forecasting — Australian Airlines Passenger Data

A time series analysis and forecasting project using the **SARIMA** (Seasonal AutoRegressive Integrated Moving Average) model on the classic Australian Airlines monthly passenger dataset.

---

## 📌 Project Overview

This project applies the **Box-Jenkins methodology** to identify and fit a SARIMA model to monthly airline passenger counts. The goal is to model both the non-seasonal and seasonal structure of the series and produce a 12-month ahead forecast.

---

## 📁 Repository Structure

```
├── sarima-australian-airlines.ipynb   # Main analysis notebook
├── 02_Airline.csv                     # Dataset (semicolon-delimited)
└── README.md
```

---

## 🔢 Dataset

| Property | Value |
|---|---|
| Source | Australian Airlines monthly passenger records |
| Frequency | Monthly |
| Format | CSV (semicolon-separated) |
| Target column | `Observation` |

---

## 🧪 Methodology

The analysis follows the classical **Box-Jenkins** workflow:

### 1. Exploratory Analysis
- Visual inspection of the raw time series to identify trend and seasonality
- ACF and PACF plots on the original series

### 2. Stationarity & Differencing
- **First-order differencing** (`d=1`) to remove the linear trend
- **Seasonal differencing** (`D=1, s=12`) to remove the annual seasonal pattern
- ACF/PACF plots after each differencing step to guide parameter selection

### 3. Stationarity Test
- **Augmented Dickey-Fuller (ADF)** test applied to the doubly-differenced series to confirm stationarity

### 4. Model Fitting
- **SARIMA(1,1,0)(1,1,2)[12]** fitted via maximum likelihood using `statsmodels`
- Model summary inspected for coefficient significance and information criteria

### 5. Forecasting
- 12-step ahead (one year) forecast generated
- Forecast overlaid on historical data for visual validation

---

## 📦 Requirements

```bash
pip install pandas numpy matplotlib statsmodels scipy
```

| Library | Purpose |
|---|---|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical operations |
| `matplotlib` | Plotting |
| `statsmodels` | SARIMA model and diagnostic plots |
| `scipy` | Statistical utilities |

---

## 🚀 Usage

1. Clone the repository and ensure `02_Airline.csv` is in the same directory as the notebook.
2. Install dependencies (see above).
3. Run all cells in `sarima-australian-airlines.ipynb` sequentially.

---

## 📊 Results

The fitted SARIMA(1,1,0)(1,1,2)[12] model captures both the upward trend and the 12-month seasonal cycle present in the data. A 12-month forecast is produced and visualised against the historical series.

---

## ⚠️ Known Limitations & Future Work

- No train/test split — the model is evaluated visually, not quantitatively
- No confidence intervals displayed in the forecast plot
- Model order was selected manually via ACF/PACF inspection; **auto-ARIMA** could automate and improve this
- No forecast error metrics (MAE, RMSE, MAPE)

---

## 📚 References

- Box, G.E.P., Jenkins, G.M., Reinsel, G.C. (1994). *Time Series Analysis: Forecasting and Control*
- [statsmodels SARIMAX documentation](https://www.statsmodels.org/stable/generated/statsmodels.tsa.statespace.SARIMAX.html)
- Hyndman, R.J. & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice* (3rd ed.)
