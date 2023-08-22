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

# GizoOrientationSetting

## Overview

In MyTestSDK, the "orientation setting" refers to the configuration that determines how the user interface of an Android application is displayed in terms of screen orientation.

Screen orientation refers to the orientation of the device's screen, which can be either portrait (vertical) or landscape (horizontal). By default, Android devices can automatically change their screen orientation based on how the user holds and rotates the device.

You can add these lines of code in the Application class, onCreate function, inside Gizo.initialize to set the Orientation Settings.

{% tabs %}
{% tab title="kotlin" %}
```kotlin
.orientationSetting(
    GizoOrientationSetting.Builder()
        .allowOrientationSensor(true)
        .build()
)
```
{% endtab %}
{% endtabs %}

The `orientationSetting` builder sets the orientation-related property which is:

<mark style="color:blue;">`allowOrientationSensor`</mark>`(true)`: This method enables the usage of the device's orientation sensor. The orientation sensor provides information about the device's rotation in three dimensions (roll, pitch, and azimuth). By setting this property to `true`, you allow the application to access and utilize the orientation sensor data.

Once the desired orientation settings are configured using the builder, the `build()` method is called to create an instance of `GizoOrientationSetting` with the specified settings.



Here are the available option that can be set in orientationSetting in the Application class:

<table><thead><tr><th width="227">Options</th><th width="141.33333333333331">Default Value</th><th>Descriptions</th></tr></thead><tbody><tr><td><p>allowOrientationSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate orientation sensor or not.</td></tr></tbody></table>
