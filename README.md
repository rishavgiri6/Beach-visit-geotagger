# Weather-Predictor
A location based (geo-tagging) data analyzer to build a weather forecasting model in the NASA Hackathon '18 to suggest best times to visit the nearest beach(input as searchbar query for the user).

We have used a correlation matrix classifier backed by weather data from DarkSky API.

The following attributes were put into the matrix as coefficients:
time
summary
icon
sunriseTime
sunsetTime
moonPhase
precipIntensity
precipIntensityMax
precipIntensityMaxTime
precipProbability
precipType
temperatureHigh
temperatureHighTime
temperatureLow
temperatureLowTime
apparentTemperatureHigh
apparentTemperatureHighTime
apparentTemperatureLow
apparentTemperatureLowTime
dewPoint
humidity
pressure
windSpeed
windGust
windGustTime
windBearing
cloudCover
uvIndex
uvIndexTime
visibility
ozone
temperatureMin
temperatureMinTime
temperatureMax
temperatureMaxTime
apparentTemperatureMin
apparentTemperatureMinTime
apparentTemperatureMax
apparentTemperatureMaxTime

There are two endpoints supported by this API.

GET Forecast
The “Forecast” endpoint fetches the latest weather prediction for a given geographical location pointed by a latitude and longitude coordinate.

Let’s find out the current prediction for New York. The approximate coordinates of New York is 40.7 (latitude) and -74 (longitude).

Dark Sky API Weather Forecast Request

After triggering the API, here is the format in which you will get the result.

Dark Sky API Weather Forecast Response
Dark Sky Weather API response contains the prediction for November 17, 2019, 03: 58 AM (GMT). If you call this API on some other day, then the values will change. From a layman’s point of view, you can see that the data contains the usual weather condition indicators such as temperature, pressure, wind speed, etc.

Dark Sky Weather API also returns a prediction for the upcoming hour and the day.

Dark Sky API Weather Forecast Response Details
Note that the timestamp for this prediction response is in the Unix time format. That means the value ‘1573963131’   for ‘currently’ > ‘time’ key translates to Sunday, November 17, 2019, 3:58:51 AM (GMT).

GET Time Machine
This “Time Machine” endpoint is similar to the “Forecast” endpoint. Apart from the latitude and longitude, it accepts a timestamp in the past and retrieves the historical prediction.

Dark Sky API Time Machine Request

In this case, Dark Sky Weather API retrieves the weather information of New York on Friday, November 1, 2019, at 4:10:36 AM. The value ‘1572581436’ for the ‘time’ parameter translates to this time.

Dark Sky API Time Machine Response
Connect to API

Optional Parameters
Both the endpoints support optional parameters to finetune the prediction responses  from the Dark Sky Weather API.

Dark Sky API Forecast Optional Parameters
The ‘lang’ parameters returns the data in your preferred language. You can check out the supported languages under the “API Details” tab.

Dark Sky Details Supported Languages

The ‘extend’ parameter is used to return extended results for the interval forecasts. In the case of a value ‘hourly’, the API returns the  forecast with extended prediction for the next 168 hours (7 days).

Dark Sky Details Extended Hours
This parameter is not available for the “Time Machine” endpoint.

The ‘units’ parameter is used to select a specific unit for the weather parameters. The “API Details” tab has more information on the supported units and their interpretation in the returned response of the API.

Dark Sky Details Units
Finally, the ‘exclude’ parameter is used to omit one of the data blocks from the API response, either “currently,” “minutely,” “hourly,” or “daily.” It also accepts a comma-delimited string containing more than one data block.

Historical Weather Data API

Dark Sky offers Historical Weather Data API. The “GET Time Machine” REST API method returns the observed hour-by-hour weather and daily weather condition for a particular date. The API returns weather data such as temperature, cloud cover, humidity, precipitation (rainfall), wind speed etc.
