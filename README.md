# ⚡ EV Charging Demand Forecasting using Prophet

This project forecasts electric vehicle (EV) charging demand is continuation of EV dashboard and i am using time series analysis and machine learning prophet. It simulates EV charging behavior based on traffic and temperature data, providing interactive visualizations to understand daily, weekly, and seasonal trends in EV usage.

---

## 📌 Project Overview

The goal of this project is to:

- Simulate and forecast EV charging demand using environmental and traffic features.
- Visualize charging demand trends over time.
- Analyze daily and weekly seasonality for better infrastructure planning.

---

## 🛠️ Tools & Technologies

- **Python 3.11**
- **Pandas** – Data handling
- **NumPy** – Numerical computations
- **Prophet** – Time series forecasting
- **Matplotlib** – Data visualization
- **VS Code** – Development environment

---

## 📁 Dataset

The merged dataset includes:

- `Date`: Timestamp
- `Avg Traffic Volume`: Simulated traffic levels
- `Temp_C`: Temperature in Celsius
- Output: `Estimated_Demand_kWh` – Simulated EV charging energy

The dataset is preprocessed using `pandas` and fed into the forecasting model.

---

## 📈 Forecasting Approach

### ✔️ Data Simulation
```python
df['Estimated_Demand_kWh'] = (
    df['Avg Traffic Volume'] * 0.05 +
    df['Temp_C'] * 2 +
    np.random.normal(0, 5, size=len(df))  # Add noise
)

### ✔️ Model Training with Prophet 
```python
demand_df = df[['Date', 'Estimated_Demand_kWh']].rename(columns={
    'Date': 'ds',
    'Estimated_Demand_kWh': 'y'
})
model = Prophet(daily_seasonality=True)
model.fit(demand_df)

### ✔️ Forecast Generation
```python
future = model.make_future_dataframe(periods=30)
forecast = model.predict(future)

## 🖼️ Visualizations
### 🔮 Forecast Plot
Forecast for 30 days ahead with uncertainty intervals:


### 📅 Seasonal Components
Trend: General decrease in demand over time

Weekly Pattern: Peaks on Tuesdays and Mondays

Daily Pattern: Peaks at midnight and low activity mid-day


### 🧠 Key Insights
Weekdays, especially Tuesdays, exhibit the highest charging demand.

Weekends show significantly lower demand.

The daily pattern reflects morning and late evening peaks.

Forecast confidence intervals highlight the variability and seasonality in usage.

### 📌 How to Run
Clone the repository:

bash
Copy
Edit
git clone https://github.com/your-username/ev-charging-forecast.git
cd ev-charging-forecast
Install requirements:

bash
Copy
Edit
pip install pandas numpy matplotlib prophet
Run the notebook: Open Forecasting.ipynb in Jupyter or VS Code and execute all cells.

## 📄 Author
Harsh • @yourhandle

## 📃 License
This project is licensed under the MIT License - see the LICENSE file for details.

