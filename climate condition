from dotenv import load_dotenv
import requests
import os
load_dotenv()
def get_weather(city_name):
    api_key=os.getenv('OPENWEATHER_API_KEY')
    if not api_key:
        print("API key is not found.please set the 'OPENWEATHER_API_KEY' environment variable")
        return
    # Construct the request URL
    url=f"http://api.openweathermap.org/data/2.5/weather?q={city_name}&appid={api_key}&units=metric"

    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()

        
        city_name=data['name']
        weather_description = data['weather'][0]['description']
        temperature = data['main']['temp']
        humidity = data['main']['humidity']
        wind_speed = data['wind']['speed']

        print(f"\nWeather Information for {city_name.capitalize()}:")
        print(f"Description: {weather_description.capitalize()}")
        print(f"Temperature: {temperature}°C")
        print(f"Humidity: {humidity}%")
        print(f"Wind Speed: {wind_speed} m/s")
    except requests.exceptions.HTTPError:
            print("City not found or an error occurred. Please check the city name.")

    except requests.exceptions.RequestException as e:
        print(f"An error occurred: {e}")


print("Welcome to the Weather Information App")
city_name = input("Enter the city name: ")
get_weather(city_name)
