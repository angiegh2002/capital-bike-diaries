# Capital Bike Share Diaries: Data Analysis Project

A comprehensive data analysis of bike-sharing systems in Washington, D.C., using Capital Bike Share trip data. This project explores usage patterns, weather impacts, station distribution, user behavior, and builds a time series forecasting model for daily revenue.

## 📌 Objectives

- Understand usage patterns of the bike-sharing service.
- Assess the impact of weather conditions on trip volume.
- Identify high-traffic stations and spatial hotspots.
- Analyze trip duration and distance to understand rider behavior.
- Compare usage between members (subscribers) and casual riders.
- Build a time series forecasting model for daily revenue prediction.

## 📂 Data Sources

The following datasets were used:

| File | Description |
|------|-------------|
| `daily-trip-data-sampled.parquet` | Sampled daily trip records (start/end location, bike type, duration, etc.). |
| `daily-rent-sampled.parquet` | Sampled daily financial data (daily revenue). |
| `stations_table.csv` | Station metadata including name, capacity, latitude, longitude. |
| `weather_daily_avgs_costs.csv` | Daily weather metrics (temperature, humidity, wind speed). |
| `cbd_polygon.geojson` | GeoJSON defining the Central Business District (CBD) boundary. |
| `metro_bus_stops.geojson`, `shuttle_bus_stops.geojson` | Locations of public transit stops near bike stations. |

## 🛠 Tools & Libraries

- **Pandas & NumPy**: Data cleaning and statistical analysis.
- **Geopandas, Shapely, Pygeohash**: Geospatial operations and proximity analysis.
- **Plotly & Folium**: Interactive visualizations and maps.
- **Missingno**: Missing data visualization.
- **Prophet (by Meta)**: Time series forecasting.
- **SciPy & Statsmodels**: Statistical testing (e.g., Chi-square test).
- **Scikit-Learn**: Nearest neighbors for coordinate correction.

## 📊 Key Findings

### 🔍 Usage Patterns
- **Electric bikes** are more frequently used than classic bikes across all user types.
- **Members (subscribers)** dominate overall trip volume compared to casual users.
- Most trips start and end at stations with **medium capacity (15–25 docks)**.

### 🌦 Weather Impact
- Trip counts increase significantly with **higher temperatures**.
- **Rainy or cloudy days** see reduced usage.
- No strong correlation between temperature and trip cost was found.

### 📍 Spatial Distribution
- High-activity zones are concentrated in **Northwest D.C.**, particularly around:
  - **18th St & Wyoming Ave NW**
  - **Lamont & Mt Pleasant NW**
  - **Columbus Circle / Union Station**
- These areas have high population density and commercial activity.
- Trips **within the CBD** are common; many long-duration trips originate in central urban areas.

### 💳 Financial Insights
- The majority of trips have **low costs (< $5)**, reflecting short durations.
- A small number of **high-cost outliers** exist (up to ~$80), likely due to very long rides.
- Trip cost is **strongly correlated with duration**, confirming a time-based pricing model.
- **Peak revenues occur in fall (September–October)**, while winter sees significant drops.

### 🧪 Statistical Tests
- **Chi-square test** confirmed a statistically significant association between:
  - **Weather condition and bike type**
  - **Distance from CBD and subscription type**
- Casual users are more likely to take longer trips from non-CBD areas.

### 📈 Revenue Forecasting
- A **Prophet time series model** was trained to predict daily revenue.
- Model tuned via hyperparameter optimization (`changepoint_prior_scale`, `seasonality_prior_scale`).
- Outperformed naive forecasts with lower RMSE and MAE.
- Captured weekly seasonality and annual trends effectively.

