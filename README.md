# Weather-Data-Analyzer-
The Weather Data Analyzer is a Python-based tool designed to help users analyze, visualize, and interpret weather data
starting new project
import requests
import pandas as pd
import matplotlib.pyplot as plt
def fetch_weather(city, api_key):
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    print(f"\nRequesting weather data for: {city}")
    print(f"URL: {url}")
    response = requests.get(url)
    print(f"Status Code: {response.status_code}")
    try:
        data = response.json()
        print(f"Response JSON: {data}")
    except ValueError:
        print("Error: Response is not valid JSON")
        return None
        if response.status_code == 200:
        try:
            return {
                "City": city,
                "Temperature (°C)": data['main']['temp'],
                "Humidity (%)": data['main']['humidity'],
                "Weather": data['weather'][0]['description']
            }
        except KeyError as e:
            print(f"Key error while parsing JSON: {e}")
            return None
    else:
        print(f"Failed to fetch weather data for '{city}'. Reason: {data.get('message', 'Unknown error')}")
        return None
API_KEY = "5e1b250446765426815156d433a8081c"
weather_data = []
while True:
    city = input("\nEnter city name (or type 'exit' to finish): ")
    if city.lower() == 'exit':
        break
    result = fetch_weather(city, API_KEY)
    if result:
        weather_data.append(result)
df = pd.DataFrame(weather_data)
if not df.empty:
    df.to_csv("weather_report.csv", index=False)
    print("\nWeather data saved to 'weather_report.csv'")
    print(df)
else:
    print("\nNo weather data collected.")
if not df.empty:
    plt.figure(figsize=(10, 5))

   
