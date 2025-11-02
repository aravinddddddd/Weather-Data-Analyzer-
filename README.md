# Real-Time Weather Data Integration & Analytics Pipeline

## 🚀 Overview
This project implements a *real-time ETL (Extract, Transform, Load) pipeline* in Python using a Google Colab notebook.  
It fetches live weather data for multiple cities from the *OpenWeather API, validates and deduplicates records, stores them in **CSV files*, and generates daily summaries for dashboards.

---

## 📂 Project Contents
- *Colab Notebook*: Contains Python ETL code fetching weather data and generating CSVs.
- *Summary.csv*: Aggregated daily weather data (temperature, humidity, pressure) for Power BI or Excel visualization.

---

## 🛠 Features
- Fetches real-time weather data for multiple cities  
- Data validation and duplicate removal  
- Stores cumulative data in weather_data.csv  
- Generates daily_summary.csv for visualization  
- Compatible with Power BI or Excel dashboards

---

## ⚙ Technology Stack
- Python 3 (in Colab)  
- Libraries: requests, pandas  
- CSV files for data storage  
- Power BI / Excel for visualization

---

## 🔑 Usage Instructions
1. Open this Colab notebook and ensure your *OpenWeather API key* is configured in the notebook.  
2. Run the notebook to fetch and store weather data in CSV files:
   - weather_data.csv – cumulative raw weather data  
   - daily_summary.csv – daily summary for visualization  
3. Open daily_summary.csv in *Power BI* to create dashboards:
   - Line chart: Temperature trend per city  
   - Line chart: Humidity trend per city  
   - Bar chart: Average pressure per city  
   - KPI cards: Current temperature, humidity, pressure  

---

## 💡 Resume / Portfolio Description
> *Real-Time Data Integration & Analytics Pipeline*  
> Developed a Python ETL pipeline in Google Colab using OpenWeather API and CSV storage to fetch and validate weather data for multiple cities. Generated daily summaries and created Power BI dashboards for real-time insights.

---

