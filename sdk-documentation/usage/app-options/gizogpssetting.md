---
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# GizoGpsSetting

## Overview

The GPS settings in MyTestSDK allow developers to incorporate GPS functionality into their Android applications. This documentation provides instructions on enabling GPS, accessing location, speed limit, and speed.

Gizo GPS setting is used to customize some behavior and functionality of our library including specifying a loop of time for getting location in 1 second, maximum amount of initial wait time, where to save GPS file, the period of time that a GPS data row is saved in CSV file, the initial delay to save GPS data, the format to save date time and so on...

For this reason, add these lines of code in the Application class, onCreate function, inside Gizo.initialize to set the Gizo GPS Settings.

**Note**: we need to get MAPBOX\_PUBLIC\_KEY from Mapbox SDK.

{% tabs %}
{% tab title="Kotlin" %}
```kts
 .gpsSetting(
       GizoGpsSetting.Builder()
       .allow(true)
       .mapBoxKey("MAPBOX_SECRET_KEY")
       .interval(1000L)
       .maxWaitTime(1000L)
       .withForegroundService(true)
       .saveCsvFile(true)
       .fileLocation(GizoFileLocationPath.CACHE)
       .savePeriod(10L)
       .saveInitialDelay(0L)
       .saveDateTimeFormat("yyyy-MM-dd'T'HH-mm-ss-SSS'Z'")
       .build())
```
{% endtab %}
{% endtabs %}

The GizoGpsSetting builder sets the GPS-related properties, such as:

* <mark style="color:blue;">allow</mark>(true): Enabling GPS.
* <mark style="color:blue;">mapBoxKey</mark>(“MAPBOX\_SECRET\_KEY”): Providing the Mapbox API key for accessing Mapbox services.
* interval(1000L): Setting the GPS update interval to 1000 milliseconds (1 second). &#x20;
* <mark style="color:blue;">maxWaitTime</mark>(1000L): Setting the maximum wait time for GPS updates to 1000 milliseconds (1 second).&#x20;
* &#x20;<mark style="color:blue;">withForegroundService</mark>(true): Indicating that the GPS service should run in the foreground.
* &#x20;<mark style="color:blue;">saveCsvFile</mark>(true): Indicating that the GPS data should be saved to a CSV file.
* &#x20;<mark style="color:blue;">fileLocation</mark>(GizoFileLocationPath.CACHE): Specifying the file location path for storing the GPS data CSV file (in this case, set to the cache directory).
* <mark style="color:blue;">savePeriod</mark>(10L): Setting the period of saving GPS data to 10 milliseconds.&#x20;
* <mark style="color:blue;">saveInitialDelay</mark>(0L): Setting the initial delay of saving GPS data to 0 milliseconds (no delay).
* <mark style="color:blue;">saveDateTimeFormat</mark>(“yyyy-MM-dd’T’HH-mm-ss-SSS’Z’”): Specifying the date and time format for saving the GPS data file.&#x20;

**Note:** saveDateTimeFormat will be changed if It's going to be used locally.&#x20;



Finally, the build() method is called on the GizoAppOptions.Builder() instance to create a GizoAppOptions object with the configured GPS settings.

This code suggests that the GizoAppOptions class specifies various configuration options for the Gizo application, including GPS-related settings. The specific implementation and usage of GizoAppOptions would depend on the details of the Gizo application itself.



&#x20;Here are the available options that can be set in gpsSetting in the Application class:

<table><thead><tr><th width="253.33333333333331">Options</th><th width="196">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>allow(Boolean)</td><td>false</td><td>To allow access to GPS setting.</td></tr><tr><td><p>mapBoxKey</p><p>(String)</p></td><td>_____</td><td>The key was obtained from Mapbox.</td></tr><tr><td>interval(Long)</td><td>1000L</td><td>A loop of time for getting location in 1 second.</td></tr><tr><td>maxWaitTime(Long)</td><td>1000L</td><td>Maximum amount of initial wait time. </td></tr><tr><td><p>withForegroundService</p><p>(Boolean)</p></td><td>true</td><td>To have foreground service or not.</td></tr><tr><td>saveCsvFile(Boolean)</td><td>false</td><td>To save CSV file or not.</td></tr><tr><td><p>fileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>To save GPS file in cache or download.</td></tr><tr><td><p>savePeriod</p><p>(Long)</p></td><td>10L</td><td>The period of time that a GPS data row is saved in CSV file.</td></tr><tr><td><p>saveInitialDelay</p><p>(Long)</p></td><td>0L</td><td>The initial delay to save GPS data.</td></tr><tr><td><p>saveDateTimeFormat</p><p>(String)</p></td><td><p>"yyyy-MM-dd</p><p>'T'HH-mm-ss-SSS'Z'"</p></td><td>The format to save date time.</td></tr></tbody></table>



&#x20;
