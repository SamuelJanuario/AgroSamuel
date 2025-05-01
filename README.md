# AgroSmart Supply

Final project for the Building AI course

## Summary

AgroSmart Supply is an AI-powered solution that predicts the weekly and monthly consumption of critical insumos (inputs) in corn-based processing plants. It helps avoid excess inventory and production delays by optimizing supply planning using historical and contextual data.

## Background

Corn-based plants, especially in ethanol, rations, and starch production, depend heavily on accurate planning of raw material usage. Inadequate forecasting leads to:

* Overstock and expiration of chemical or enzymatic inputs
* Emergency purchases at higher costs
* Production bottlenecks due to missing items

This problem is widespread across the agribusiness sector and especially relevant in Brazil, where industrial corn processing capacity is rapidly expanding.

Motivation:
* Reduce waste and cost with smarter planning
* Improve working capital and inventory rotation
* Increase production stability

## How is it used?

The plant's operations team provides a production forecast. The system uses historical consumption data, current climate and crop expectations, and planned downtime to generate:

* Input consumption forecasts (e.g. enzymes, acids, ammonia, yeast, etc.)
* Replenishment suggestions per input
* Alerts for low-stock scenarios

The system is used by procurement and production planners. Reports are generated in Excel, or integrated into the ERP system.

## Data sources and AI methods

**Data Sources:**
* Internal ERP: production batches, historical input consumption
* Climate data: INMET API or ClimaTempo
* Regional crop data: CONAB
* Scheduled maintenance or downtime logs

**AI Techniques:**
* Time series forecasting (Prophet / LSTM / ARIMA)
* Regression models (XGBoost / Random Forest)
* Anomaly detection for abnormal consumption

```python
# Simplified example of regression-based prediction
import pandas as pd
from sklearn.linear_model import LinearRegression

# Features: production volume, temperature, crop volume index
X = df[['tons_processed', 'avg_temperature', 'regional_crop_index']]
y = df['liters_of_enzyme_used']

model = LinearRegression()
model.fit(X, y)

future_prediction = model.predict(new_input_data)
```

## Challenges

* Cannot account for operational failures (e.g. contamination or blockages)
* Relies on data hygiene – ERP inconsistencies harm model reliability
* Requires customization per plant due to unique process setups
* Ethical use of data and privacy in sourcing third-party APIs

## What next?

* Build prototype with real (anonymized) data from one corn plant
* Expand to other bio-industrial inputs (urea, chemicals, etc.)
* Integrate dashboard using Streamlit or Power BI
* Build prescriptive layer to recommend ideal lot sizes and timing

## Acknowledgments

* Inspired by logistics planning systems at Cargill and Raízen
* Forecasting methods adapted from open-source Prophet library by Meta
* Weather data provided by INMET (Brazilian National Meteorological Institute)

---

[Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
