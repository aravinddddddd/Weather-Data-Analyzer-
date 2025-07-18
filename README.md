# Weather-Data-Analyzer-
The Weather Data Analyzer is a Python-based tool designed to help users analyze, visualize, and interpret weather data
starting new project
import requests
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
def fetch_weather(city, api_key):
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    print(f"\nRequesting weather data for: {city}")
    print(f"URL: {url}")
    response = requests.get(url)
    print(f"Status Code: {response.status_code}")
    if response.status_code == 200:
     try:
        data = response.json()
        print(f"Response JSON: {data}")
        return {
                "City": city,
                "Temperature (°C)": data['main']['temp'],
                "Humidity (%)": data['main']['humidity'],
                "Weather": data['weather'][0]['description'].capitalize()
            }
        except (ValueError, KeyError) as e:
            print(f"Error parsing response JSON: {e}")
            return None
    else:
        try:
            error_data = response.json()
            print(f"Failed to fetch weather data. Reason: {error_data.get('message', 'Unknown error')}")
        except ValueError:
            print("Invalid response format received.")
        return None

def main():
    weather_data = []
    while True:
        city = input("\nEnter city name (or type 'exit' to finish): ").strip()
        if city.lower() == 'exit':
            break
        result = fetch_weather(city, API_KEY)
        if result:
            weather_data.append(result)
    df = pd.DataFrame(weather_data)
    if not df.empty:
        df.to_csv("weather_report.csv", index=False)
        print("\nWeather data saved to 'weather_report.csv'\n")
        print(df.to_string(index=False))
        sns.set_style("whitegrid")
        plt.figure(figsize=(10, 5))
        colors = sns.color_palette("Blues", len(df))
        bars = plt.bar(df['City'], df['Temperature (°C)'], color=colors)
        plt.title("City-wise Temperature Comparison", fontsize=14)
        plt.xlabel("City", fontsize=12)
        plt.ylabel("Temperature (°C)", fontsize=12)
        plt.xticks(rotation=45)
        for bar in bars:
            plt.text(bar.get_x() + bar.get_width() / 2, bar.get_height() + 0.5,
                     f"{bar.get_height():.1f}°C", ha='center', va='bottom', fontsize=10)
        plt.tight_layout()
        plt.show(block=True)
    else:
        print("\nNo weather data collected.")

if __name__ == "__main__":
    main()

