# Project-5-Weather-App
# 🌤️ Weather App

This project is a simple **Weather Application built with Python and PyQt5**. The application allows the user to enter a city name and get the current weather information using the **OpenWeather API**.

I created this project to practice working with **Python GUI development, APIs, HTTP requests, JSON data, and exception handling** in a practical application.

## ✨ Features

* Enter any city name through a graphical interface.
* Get the current temperature of the selected city.
* Display the weather description.
* Show a weather emoji based on the current weather condition.
* Handle common API and connection errors.
* Simple and clean graphical interface using PyQt5.

## 🛠️ Technologies Used

* **Python** – Main programming language.
* **PyQt5** – Used to create the graphical user interface.
* **Requests** – Used to send HTTP requests to the weather API.
* **OpenWeather API** – Provides the current weather data.

## 🔍 How the Application Works

When the application starts, it creates a window containing:

1. A label asking the user to enter a city.
2. A text field where the city name can be entered.
3. A **Get Weather** button.
4. A section showing the temperature.
5. An emoji representing the weather.
6. A description of the current weather.

When the user clicks **Get Weather**, the application takes the city name from the input field and sends a request to the OpenWeather API.

The API returns weather information in **JSON format**. The application then extracts the required information, such as the temperature, weather ID, and weather description, and displays them in the window.

## 🌡️ Temperature Conversion

The OpenWeather API returns the temperature in Kelvin in the original version of the project.

The application converts Kelvin to Celsius using:

```python
temperature_c = temperature_k - 273.15
```

It then displays the result in Celsius, for example:

```text
25°C
```

## ☁️ Weather Emoji

The application uses the weather ID returned by OpenWeather to determine which emoji should be displayed.

For example:

* 🌩️ IDs from `200–232` → Thunderstorm
* 🌦️ IDs from `300–321` → Drizzle
* 🌧️ IDs from `500–531` → Rain
* ❄️ IDs from `600–622` → Snow
* 🌫️ IDs from `701–741` → Fog/Mist
* ☀️ ID `800` → Clear sky
* ☁️ IDs from `801–804` → Clouds

This is handled by the `get_weather_emoji()` function.

## 🖥️ PyQt5 GUI

The main application is based on the `WeatherApp` class:

```python
class WeatherApp(QWidget):
```

The class inherits from `QWidget`, which provides the basic window for the application.

Several PyQt5 widgets are used:

* `QLabel` – Displays text such as the temperature and weather description.
* `QLineEdit` – Allows the user to enter a city name.
* `QPushButton` – Allows the user to request the weather.
* `QVBoxLayout` – Arranges the widgets vertically.

The button is connected to the weather function using:

```python
self.get_weather_button.clicked.connect(self.get_weather)
```

This means that whenever the user clicks the button, the `get_weather()` function is called.

## 🌐 Getting Data from the API

The application uses the `requests` library to communicate with OpenWeather:

```python
response = requests.get(url)
```

The response is then converted into Python data using:

```python
data = response.json()
```

The program can then access information such as:

```python
data["main"]["temp"]
data["weather"][0]["id"]
data["weather"][0]["description"]
```

## ⚠️ Error Handling

The application also includes error handling so that it doesn't simply stop when something goes wrong.

It handles situations such as:

* Invalid API key
* City not found
* Bad request
* Server errors
* No internet connection
* Request timeout
* Too many redirects

For example, if the user enters a city that cannot be found, the application displays an appropriate error message instead of crashing.

## 🎨 Styling

The interface is customized using **Qt Style Sheets (QSS)**.

For example, different font sizes are applied to the city label, temperature, weather emoji, and description to make the interface easier to read.

```python
self.setStyleSheet("""
    QLabel, QPushButton {
        font-family: calibri;
    }
""")
```

This gives the application a more organized and user-friendly appearance.

## ▶️ How to Run the Project

First, install the required packages:

```bash
pip install PyQt5 requests
```

Then run the Python file:

```bash
python Weather_App.py
```

Make sure you have a valid **OpenWeather API key** and place it in the code before running the application.

> **Security Note:** API keys should not be uploaded to GitHub. It is better to keep the API key in an environment variable or a separate configuration file that is included in `.gitignore`.

## 📚 What I Learned

Through this project, I practiced several important Python concepts:

* Building desktop GUI applications with PyQt5.
* Working with classes and objects.
* Connecting buttons to functions.
* Sending HTTP requests using the Requests library.
* Working with APIs and JSON data.
* Handling exceptions and HTTP errors.
* Converting temperature units.
* Using conditional statements to categorize weather conditions.
* Styling a GUI application with Qt Style Sheets.

## 🚀 Future Improvements

Some possible improvements for the project are:

* Add a 5-day weather forecast.
* Display humidity and wind speed.
* Add weather icons or animated backgrounds.
* Add support for different temperature units such as Fahrenheit and Celsius.
* Improve the GUI design.
* Store the API key securely using environment variables.
* Add automatic location detection.

## 👨‍💻 Project

This project is a small practical Python application designed to demonstrate how a graphical interface can communicate with an external API and display real-time information to the user.
