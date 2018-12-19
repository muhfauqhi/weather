# weather
This package uses the [OpenWeatherMAP API](https://openweathermap.org/) to get the current weather status as well as weather forecasts.

[![pub package](https://img.shields.io/pub/v/weather.svg)](https://pub.dartlang.org/packages/weather)

## Install (Flutter)
Add ```weather``` as a dependency in  `pubspec.yaml`.
For help on adding as a dependency, view the [pubspec documenation](https://flutter.io/using-packages/).

## Permissions
The package uses your location to fetch weather data, therefore location tracking must be enabled.

### Android
Add the following entry to your `manifest.xml` file, in the Android project of your application:

```xml
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

In addition, it is recommended to set your __minimum SDK version to 21__.

### iOS
1. Open the XCode project of your app, named `Runner.xcodeproj`
2. Locate the `info.plist` file in the `Runner` directory.
3. Right click `info.plist` and choose `Open as > Source Code`.
4. Add the following entries inside the `<dict></dict>` tags`:

```xml
<key>NSLocationWhenInUseUsageDescription</key>
<string>This app uses location to forecast the weather.</string>
<key>NSLocationAlwaysUsageDescription</key>
<string>This app uses location to forecast the weather.</string>
```

#### Known issues
There is an issue with the `location` plugin which this package depends on, where an error with the following message 

`The use of Swift 3 @objc inference in Swift 4 mode is deprecated` 

may be thrown. For a solution, check the following stack overflow question:
https://stackoverflow.com/questions/44379348/the-use-of-swift-3-objc-inference-in-swift-4-mode-is-deprecated


## Usage
First and foremost you need an API key from OpenWeatherMap, which can be acquired for free [here](https://openweathermap.org/price).

```dart
WeatherStation weatherStation = new WeatherStation("YOUR_API_KEY");
```
### Query current weather
For api documentation on the current weather API, see the [OpenWeatherMap weather API docs](https://openweathermap.org/current).

```dart
Weather weather = await weatherStation.getCurrentWeather();
```
For a complete list of all the properties of the [Weather](https://pub.dartlang.org/documentation/weather/latest/weather/Weather-class.html) class, check the [documentation](https://pub.dartlang.org/documentation/weather/latest/weather/Weather-class.html)

#### Get current temperature
The [Temperature](https://pub.dartlang.org/documentation/weather/latest/weather/Temperature-class.html) class holds a temperature and can output the temperature in Celsius, Fahrenheit, and Kelvin:
```dart
double celsius = weather.temperature.celsius;
double fahrenheit = weather.temperature.celsius;
double kelvin = weather.temperature.kelvin;
```

### Query 5 day forecast
For API documentation on the forecast API, see the [OpenWeatherMap forecast API docs](https://openweathermap.org/forecast5).

```dart
List<Weather> forecasts = await weatherStation.getFiveDayForecast();
```


