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

The GPS settings in MyTestSDK allow developers to incorporate GPS functionality into their Android applications. This documentation provides instructions on enabling GPS, accessing location, speed limit and speed.

For this reason, add these lines of code in Application class, onCreate function, inside Gizo.initialize to set the Gizo GPS Settings.

**Note**: we need to get MAPBOX\_PUBLIC\_KEY from [mapbox SDK](https://docs.mapbox.com/android/maps/guides/install/).

{% tabs %}
{% tab title="Kotlin" %}
```kts
 .gpsSetting(
       GizoGpsSetting.Builder()
       .allow(true)
       .mapBoxKey("MAPBOX_PUBLIC_KEY")
       .saveCsvFile(true)
       .build())
```
{% endtab %}
{% endtabs %}



&#x20;Here are the available options that can be set in gpsSetting in the Application class:

<table><thead><tr><th width="253.33333333333331">Options</th><th width="196">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>allow(Boolean)</td><td>false</td><td>To allow access to GPS setting</td></tr><tr><td><p>mapBoxKey</p><p>(String)</p></td><td>_____</td><td>The key obtained from mapbox</td></tr><tr><td>interval(Long)</td><td>1000L</td><td>A loop of time for getting location in 1 second</td></tr><tr><td>maxWaitTime(Long)</td><td>1000L</td><td>Maximum amount of initial wait time </td></tr><tr><td><p>withForegroundService</p><p>(Boolean)</p></td><td>true</td><td>To have foreground service or not</td></tr><tr><td>saveCsvFile(Boolean)</td><td>false</td><td>To save CSV file or not</td></tr><tr><td><p>fileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>To save GPS file in cache or download</td></tr><tr><td><p>savePeriod</p><p>(Long)</p></td><td>10L</td><td>The period of time that a GPS data row is saved in CSV file</td></tr><tr><td><p>saveInitialDelay</p><p>(Long)</p></td><td>0L</td><td>The initial delay to save GPS data</td></tr><tr><td><p>saveDateTimeFormat</p><p>(String)</p></td><td><p>"yyyy-MM-dd</p><p>'T'HH-mm-ss-SSS'Z'"</p></td><td>The format to save date time</td></tr></tbody></table>
