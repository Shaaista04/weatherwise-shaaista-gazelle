title: "Before/After Examples: WeatherWise Enhancements"
author: "Shaa'ista Gazelle"

---------------------

## Example 2: Forecast Visualisation Function

### Initial Prompt

```
Create a function to plot a simple line chart of daily temperatures by using Matplotlib.
```

### Initial AI-Generated Code (Before)

```python
import matplotlib.pyplot as plt

def plot_forecastdata(temps):
    plt.plot(temps)
    plt.show()
```

### My Analysis of the Initial Code

1. It is difficult to read the chart as it lacks a title or label.
2. There are no axis for the date or doesn't have appropriate x-ticks.
3. It does not accept forecast structured data.
4. There's a lack of personalisation or style
5. It is not reusable or expandable

### My Follow-up Prompt

```
Please improve the plot_forecast function to:
1. Acknowledge a list of dictionaries including date and temperature
2. Add the tittle along with the x and y axes
3. Enhance the styling format (e.g., markers, grid, color)
4. Rotate x-axis labels to make it easier to read
5. Include a docstring to explain how to use it
```

### Improved AI-Generated Code (After)

```python
import matplotlib.pyplot as plt

def plot_forecastdata(forecast_data):
    """
    Plots temperature forecast using Matplotlib.

    Args:
        forecast_data (list): List of dicts with 'date' and 'temperature' keys.
    """
    dates = [day['date'] for day in forecast_data]
    temps = [day['temperature'] for day in forecast_data]

    plt.figure(figsize=(10, 5))
    plt.plot(dates, temps, marker='o', linestyle='-', color='grey')
    plt.xlabel('Date')
    plt.ylabel('Temperature (°C)')
    plt.title('5-Day Temperature Forecastdata')
    plt.grid(True)
    plt.xticks(rotation=45°)
    plt.tight_layout()
    plt.show()
```

### Why This Prompting Strategy Was far more Effective

I was explicit about problems while using it in the previous plot and asked for common best practices in data visualization. This enable the AI to make the function better by creating a more professional, readable, and reusable chart.

---

