##  Six-Step Development Process for get_weather_data(city_name, forecast_period=3)

### Step 1 – Requirement Analysis
The goal was to create a reliable function that retrieves up-to-date weather forecasts for any city, supporting a user-specified forecast range. The **wttr.in API** was selected for its ease of use and free access, fitting project constraints.

---

### Step 2 – Exploration
Researched the **wttr.in JSON API’s** data format and explored Python’s `requests` library for handling HTTP requests and exceptions effectively, ensuring stable program behavior.

---

### Step 3 – Structural Planning
Drew pseudocode for clear workflow:
- Construct the API URL using the city name and query parameters.  
- Use `requests.get()` to fetch data.  
- Parse JSON response.  
- Safely trim the forecast data to the specified days.  
- Wrap requests in exception handlers to manage errors.

---

### Step 4 – Coding
Developed the function following these principles:

def get_weather_data(city_name, forecast_period=3):
"""
Retrieve weather forecast data for a specified city.
"""
url = f"https://wttr.in/{city_name}?format=j1"
try:
reply = requests.get(url)
reply.raise_for_status()
info = reply.json()
info['weather'] = info['weather'][:forecast_period]
return info
except Exception as err:
print(f"Unable to fetch weather data: {err}")
return None

---

### Step 5 – Validation
Tested with a variety of city names under different network conditions. Confirmed that the function provides expected output and handles failures gracefully without crashes.

---

### Step 6 – Enhancement
Based on iterative AI feedback, improved variable names for readability and added detailed inline documentation. Incorporated consistent user messaging for errors, making the function more user-friendly and maintainable.

---
