## Initial Prompt
"Before/After Example 1: WeatherWise Data Retrieval Function"

author: "Shaa'ista Gazelle"

---------------------


```
Write a function to get weather data from the OpenWeatherMap API for a given city.
```

## Initial AI-Generated Code (Before)

```python
def get_weatherdata(city):
    import requests

    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid=your_api_key&units=metric"
    response = requests.get(url)
    data = response.json()
    return data
```

## My Analysis of the Initial Code

The initial function works but has several limitations:

1. No error handling for issues like network or HTTP in unexpected situations
2. IN case of inputting an invalid city, the data will not ne handled
3. Returns the complete JSON which is difficult to use
4. The request does not support a timeout setting
5. In case of the need for clarity, there are no comments or docstrings

## My Follow-up Prompt

```
Please enhance the function to:
1. Address request errors and invalid responses
2. Incorporate a timeout
3. Extract and return only Important weather data (temperature, humidity, weather description)
4. Add inline comments and docstring
```

## Improved AI-Generated Code (After)

```python
def get_weather_data(city, api_key, timeout=5):
    """
    Retrieves and returns current weather data for a given city using the OpenWeatherMap API.

    Args:
        city (str): Name of the city.
        api_key (str): OpenWeatherMap API key.
        timeout (int): Timeout duration for the request.

    Returns:
        dict: Dictionary containing temperature, humidity, and weather description or an error message.
    """
    import requests

    try:
        url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
        response = requests.get(url, timeout=timeout)
        response.raise_for_status()

        data = response.json()

        # Extract relevant information
        weather_info = {
            "city": city,
            "temperature": data["main"]["temp"],
            "humidity": data["main"]["humidity"],
            "description": data["weather"][0]["description"]
        }
        return weather_info

    except requests.exceptions.RequestException as e:
        return {"error": f"Request failed: {e}"}
    except (KeyError, ValueError, TypeError) as e:
        return {"error": f"Data parsing error: {e}"}
```

## Why My Prompting Strategy Was Effective

My prompting strategy worked well because:

1. **I provided with a detailed feedback on areas of the code that needed improvements.
2. **Prioritising usability was my main concern and I also ask for data parsing which would help makes the function more useful to users.
3. **I added practical needs such as handling timeout and catching error.
4. **I requested documentation**, this resulted in a function with an understable and complete docstring.

Being clear and specific in the follow-up prompt helped the AI understand the extent of the improvements, resulting in a more polished and production-ready function.
