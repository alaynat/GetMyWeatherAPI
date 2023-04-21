# GetMyWeather API Documentation

Welcome to the **GetMyWeather API**! This API provides highly customizable weather information for web developers to include in their applications or websites. 

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites for Use](#prerequisites-for-use)
- [Parameters](#parameters)
- [How to use GetMyWeather](#how-to-use-getmyweather)
- [Example JavaScript](#example-javascript)
  - [Initializing the getWeather method](#initializing-the-getweather-method)
  - [Calling the getWeather method](#calling-the-getweather-method)
  - [Returning the package](#returning-the-package)
- [Trust Value](#trust-value)
- [Errors](#errors)

## Introduction

The **GetMyWeather API** provides up-to-date and reliable weather information for developers to integrate into their web applications. The API allows developers to retrieve weather information based on their desired location, date and time, and radius. The *getWeather* method returns an HTML package containing the requested weather data.

## Prerequisites for Use

To use the *getWeather* method, you need an API key. You can register for an API key at [https://getmyweather.com](https://getmyweather.com). Cost information is provided on the website. A no-cost key is available for application development.

## Parameters
The getWeather method has the following parameters:
| Input      | Required/Optional | Description                                                     |
|------------|-------------------|-----------------------------------------------------------------|
|Location    | Required          | The location to retrieve weather data for (as lattitude/longitude, in ISO 6709 format).|
|Specificity | Required          | The radius around the location to retrieve weather data (in meters. Minimum value is 10; maximum is 100,000.)|
|Time        | Required          | The time from now to retrieve weather data for (in hours. Decimals are allowed.)|
|Key         | Required          | The API key is provided by GetMyWeather upon registration to use the API.|

## How to use GetMyWeather

**GetMyWeather** replaces the following HTML with the retuned results:

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
The **GetMyWeather API** must be initalized once per web session to establish a connection between the host server and the GetMyWeather server.

#### Calling the getWeather method
```html
<script async defer
src="https://www.getmyweather.com/getWeather?key=<YOUR_KEY>&callback=init&location=<LATITUDE>:
     <LONGITUDE>&specificity=<SPECIFICITY>&time=<TIME>">
</script>
```
Replace YOUR_KEY with your API key. Each forcase must have a separate call using the getWeather method.

#### Returning the package
Upon success, the *getWeather* method returns the following HTML structure (values are samples).
```html
<div class="forecast">
  <div class="temperature">78</div>
  <div class="windspeed">15</div>
  <div class="chanceRain">30</div>
  <div class="trust">80</div>
</div>
```

The *getWeather* method takes an object as its first parameter, with properties for the parameters listed above. The second parameter is a callback function that takes the returned HTML package as its argument.

The HTML package returned by the *getWeather* method includes the requested weather data, formatted according to the API's specifications. The return package includes temperature in Fahrenheit, windspeed in miles per hour, chance of rain as a percentage, and the reliability of the focast defined as trust. 


### Trust Value

The *trust* value is a number between 1 and 100 that represents the reliability of the forecast (1 is very unreliable, 100 is absolutely reliable). The *trust* value can be affected by the *specificity* and *time* parameters. A large *specificity* value and/or a large *time* value will decrease the *trust* value. The *trust* value can be used by web developers to decide how to present the weather information to their users. There will be a generally unreliable forcast if the *time* value is over 240 hours or 10 days. 

**GetMyWeather API** returns the historical average if the forecast is more than two weeks in the future and has a *trust* value of 10 or less.

## Errors
Possible error conditions include invalid API keys, invalid parameter values, parameter out of range, and server unavailable. If an error occurs, the *getWeather* method will return an error message instead of the HTML package. 

**GetMyWeather API** is supported by all modern browers that enable Javascript.

