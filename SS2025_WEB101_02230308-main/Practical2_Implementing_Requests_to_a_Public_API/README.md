# Practical 2: Implementing Requests to a Public API ( RESTful API Weather Application ) 

# Weather API Application

A simple weather app demonstrating REST API operations (GET, POST, PUT, DELETE).

## Key Features
- Get current weather for any city
- Save favorite locations
- Edit or delete saved locations
- Works on all devices

## Technologies
- HTML, CSS, JavaScript
- OpenWeatherMap API
- JSONPlaceholder API (for demo)
- localStorage

## Quick Setup

1. **Get API Key**  
   - Sign up at [OpenWeatherMap](https://openweathermap.org/api)
   - Get your free API key

2. **Configure**  
   - Open `script.js`
   - Add your API key:
   ```javascript
   const WEATHER_API_KEY = 'your_api_key_here';

3. **Run**
   - Open index.html in any browser


 
## How to Use
### Check Weather (GET)
1. Enter city name

2. Click "Get Weather"

3. See temperature, humidity, etc.

### Save Locations (POST)
1. Fill location details

2. Click "Save"

### Manage Locations
1. Edit (PUT): Update saved locations

2. Delete: Remove locations


## Code Examples

- // GET weather
- fetch(`${API_URL}?q=${city}&appid=${API_KEY}`);

- // POST new location
- fetch(API_URL, { method: 'POST', body: JSON.stringify(data) });

## Troubleshooting
- If the weather is not loading? We should Check:

1. Correct API key

2. Internet connection

3. Valid city name

## What I've Learned
- Working with APIs

- HTTP methods (GET/POST/PUT/DELETE)

- Handling async operations

- Error management


