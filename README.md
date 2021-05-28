# Kosovo Customs 

Prediction of the import incomes based on tariffs from January 2015 to March 2021 ([Dogana e
Kosovës Statistikat – Open Data](https://dogana.rks-gov.net/en/per-doganen/statistikat-dhe-arritjet/trading-balance-based-on-tariffs/)) using time series forecasting.
---
# Time series forecasting
**“Detecting Timely Patterns in Data”**
Notion of a real world event as an abstraction of a sequence of timely activities
# Table of contents
- Data Preprocessing
- Data Normalization
- Autoregressive (AR) modeling
- ARIMA (Autoregressive integrated moving average)
- Anomaly detection
    - k-Nearest Neighbors (kNN)

# Tools
Kosovo Customs was implemented in [conda env](https://github.com/Anaconda-Platform/anaconda-project) using Jupyter Notebook.
```sh
conda install statsmodels
conda install scikit-learn
conda install pandas
conda install seaborn
```
----
### Data Preprocessing
Extraction of the revenue feature and months using feature engineering.
|   |      revenue      |
|----------|:-------------:|
| **date** |  |
|2021-02-01 |    5.165053e+07   |

- **Index col:** A key idea behind using Pandas for TS data is that the index has to be the variable depicting date-time information. So this argumenttells pandas to use the ‘Month’ column as index.
- **Revenue** : Total incomes calculated by tariffs monthly per year.

<p align="center">
<img src="https://latex.codecogs.com/png.latex?\large&space;\emph{Taksa&space;Doganes}&plus;\emph{TaksaAkcizes}&plus;\emph{TaksaTVSH-se}\Rightarrow&space;\textsl{Revenue}"></p>
<p align="center">
<img src="https://latex.codecogs.com/png.latex?\large&space;\emph{VITI}&plus;\emph{MUAJI}\Rightarrow&space;\textsl{Date}">
</p>

---

### Data Normalization
Normalizing the input features/variables is the Min-Max scaler. All features will be transformed into the range [0,1].
<p align="center"><img src="https://static.packt-cdn.com/products/9781789808452/graphics/c4212323-5a69-4a28-96ef-b503014b7784.png" width=250></p>

---

#### Removing trend
A time series with a trend is called non-stationary.
The trend was removed using **[pandas.DataFrame.diff](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.diff.html)** method.

<p align="center"><img src="https://images4.imagebam.com/0b/33/2e/MELVAD_o.png" width=500></p>

---

### Autoregressive (AR)
Forecasting the variable of interest using alinear combination of past values of the variable:
<p align="center"><img src="https://images4.imagebam.com/10/09/95/MELVBO_o.png" width=500></p>

**ε** is white noise. This is like a multiple regression but with lagged values of y t as predictors. We refer to this as an AR(p) model, an autoregressive model of order p.

---

### ARIMA 
Forecasting is achieved by plugging in time series data for the variable of interest.
An ARIMA model is characterized by 3 terms: **p**,**d**, **q** where:
- **p** is the order of the AR (Autoregression) term
- **q** is the order of the MA (Moving Average) term
- **d** is the number of differencing required to make the time series stationary

<p align="center"><img src="https://images4.imagebam.com/d5/23/7c/MELVC7_o.png" width=500></p>

## Anomaly Detection
Getting the average from April revenues per years besides year 2021.
<p align="center"><img src="https://images4.imagebam.com/f9/c7/f7/MELVCS_o.png" width=500></p>

####  k-Nearest Neighbors (kNN)
Use k-nearest neighbor approach to calculate anomaly score. Specifically, a normal instance is expected to have a small distance to its k-th nearest neighbor whereas an anomaly is likely to have a large distance to its k-th nearest neighbor.
<p align="center"><img src="https://images4.imagebam.com/29/89/12/MELVD6_o.png" width=300></p>

--

### Reducing anomaly

##### AutoRegressive 
<img src="https://images4.imagebam.com/3f/2e/a2/MELVD8_o.png" width=300></p>

##### ARIMA
<p align="center"><img src="https://images4.imagebam.com/0f/43/b2/MELVDN_o.png" width=300></p>
----

MIT
