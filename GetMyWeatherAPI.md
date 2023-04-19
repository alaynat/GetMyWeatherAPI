# GetMyWeather API Documentation

Welcome to the documentation for the GetMyWeather API! This API provides highly customizable weather information for web developers to include in their applications or websites. 


## Introduction

The GetMyWeather API provides up-to-date and reliable weather information for developers to integrate into their web applications. The API allows developers to retrieve weather information based on their desired location, date and time, and radius. The getWeather method returns an HTML package containing the requested weather data.

## Prerequisites for use

To use the getWeather method, you need an API key. You can register for an API key at https://getmyweather.com. Cost information is provided on the website.

## How to use GetMyWeather

To initialize the API in an HTML page, include the following code in the head section of the HTML document:
<script src="https://api.getmyweather.com/js?key=YOUR_API_KEY"></script>
Replace YOUR_API_KEY with your API key.
To call the getWeather method with parameters, use the following code:
javascript
Copy code
getWeather({ location: "New York, NY", radius: 10, date: "2023-04-15", time: "12:00:00", trust: 80 }, function(html) { // Use the returned HTML package });

The getWeather method takes an object as its first parameter, with properties for the parameters listed above. The second parameter is a callback function that takes the returned HTML package as its argument.

The HTML package returned by the getWeather method includes the requested weather data, formatted according to the API's specifications. The trust parameter can affect the trust value (the reliability of the forecast), as described below.

## Parameters
The getWeather method has the following parameters:
| Input     | Required/Optional | Description                                                     |
|-----------|-------------------|-----------------------------------------------------------------|
|location   | required          | the location to retrieve weather data for (e.g., "New York, NY")|
|radius     | optional          | the radius (in kilometers) around the location to retrieve weather data for (e.g., "10" for a 10-kilometer radius)|
|date       | optional          |the date to retrieve weather data for (in the format "YYYY-MM-DD")|
|time       | optional          |the time to retrieve weather data for (in the format "HH:MM:SS")|
|trust      |optional           |a value between 1 and 100 that represents the reliability of the forecast (1 is very unreliable, 100 is absolutely reliable). The default value is 100|


