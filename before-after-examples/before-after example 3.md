title: "Before/After Examples 3: natural language response generator"

author: "Shaa'ista Gazelle"


### Initial Prompt

```
Write a function that generates a simple weather response based on the forecast data.
```

### Initial AI-Generated Code (Before)

```python
def respond_to_weather(data):
    return "Weather is good."
```

### My Analysis of the Initial Code

1. The initial code is very basic — it doesn't really use any data
2. There are no personalisation according to the weather condition or temperature
3. Absence of dynamic format
4. Unhelpful in a conversation context

### My Prompt for follow-up

```
Please update the function to:
1. Acknowledge a dictionary with temperature, condition, and humidity
2. Send back a conversational message containing a summary of the weather
3. modufy the message for cold, hot, or rainy weather
4. Format via f-strings
5. Include error checking
```

### Improved AI-Generated Code (After)

```python
def generate_weather_response(data):
    """
    Generates a conversational weather summary based on the current data.

    Args:
        data (dict): Must contain 'temperature', 'weather condition', 'humidity'

    Returns:
        str: Conversational weather summary.
    """
    try:
        temp = data['temperature']
        condition = data['condition']
        humidity = data['humidity']

        if temp < 20:
            temp_feel = "cold"
        elif temp > 25:
            temp_feel = "hot"
        else:
            temp_feel = "moderate"

        return (f"It's currently {temp} °C and {condition.lower()}. "
                f"It feels {temp_feel} with a humidity of {humidity}%. Have a great day!")

    except KeyError:
        return "Weather data incomplete."
```

### Why This Prompting Strategy Was Effective

I helped the AI to turn an unclear placeholder into a useful conversational tool, which can be used for a chatbot or assistant. I preciselydefined the structure, tone, and format the data clearly so that it leads to useful, human-friendly output.
