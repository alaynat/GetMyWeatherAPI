# GetMyWeather API Documentation

Welcome to the documentation for the **GetMyWeather API**! This API provides highly customizable weather information for web developers to include in their applications or websites. 

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites for Use](#prerequisites-for-use)
- [Parameters](#parameters)
- [How to use GetMyWeather](#how-to-use-GetMyWeather)

## Introduction

The **GetMyWeather API** provides up-to-date and reliable weather information for developers to integrate into their web applications. The API allows developers to retrieve weather information based on their desired location, date and time, and radius. The *getWeather* method returns an HTML package containing the requested weather data.

## Prerequisites for Use

To use the *getWeather* method, you need an API key. You can register for an API key at [https://getmyweather.com](https://getmyweather.com). Cost information is provided on the website.

## Parameters
The getWeather method has the following parameters:
| Input     | Required/Optional | Description                                                     |
|-----------|-------------------|-----------------------------------------------------------------|
|location   | required          | the location to retrieve weather data for (e.g., "New York, NY")|
|radius     | optional          | the radius (in kilometers) around the location to retrieve weather data (in meters. Minimum value is 10; maximum is 100,000.)|
|time       | optional          | the time from now to retrieve weather data for (in hours. Decimals are allowed.)|
|trust      |optional           | a value between 1 and 100 that represents the reliability of the forecast (1 is very unreliable, 100 is absolutely reliable). The default value is 100|

## How to use GetMyWeather

GetMyWeather will replace the following HTML with the retuned results:

```html
<div id="forecast"> </div>
```

## Example JavaScript 
#### Initializing the getWeather method
```html
<script type="text/javascript">
  var weatherForecast; function init() {weatherForecast = new getWeather(document.getElementById('forecast')}
</script>
```

#### Calling the getWeather method
```html
<script async defer
src="https://www.getmyweather.com/getWeather?key=<YOUR_KEY>&callback=init&location=<LATITUDE>:<LONGITUDE>&specificity=<SPECIFICITY>&time=<TIME>">
</script>
```

#### Returning the package
```html
Upon success, the getWeather function returns the following HTML structure (values are samples).
<div class="forecast">
<div class="temperature">78</div>
<div class="windspeed">15</div>
<div class="chanceRain">30</div>
<div class="trust">80</div>
</div>
```


Replace YOUR_KEY with your API key.
The *getWeather* method takes an object as its first parameter, with properties for the parameters listed above. The second parameter is a callback function that takes the returned HTML package as its argument.

The HTML package returned by the *getWeather* method includes the requested weather data, formatted according to the API's specifications. The trust parameter can affect the trust value (the reliability of the forecast), as described below.


### Trust Value

The *trust* parameter is a value between 1 and 100 that represents the reliability of the forecast (1 is very unreliable, 100 is absolutely reliable). The *trust* value can be affected by the specificity of the location, date, and time parameters. A large *radius* value (area of the forecast) and/or a large *time* value (time in the future of the forecast) will decrease the *trust* value (the reliability of the forecast). The trust value can be used by web developers to decide how to present the weather information to their users. 

## Errors
Possible error conditions include invalid API keys and invalid parameter values. If an error occurs, the *getWeather* method will return an error message instead of the HTML package.

