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

Screen orientation refers to the orientation of the device's screen, which can be either portrait (vertical) or landscape (horizontal). In this part, we are checking the orientation of the device's screen, which should be in a proper position, landscape (horizontal) with a 90 angle.

You can add these lines of code in the Application class, onCreate function, inside Gizo.initialize to set the Orientation Settings.

{% tabs %}
{% tab title="kotlin" %}
```kotlin
.orientationSetting(
    GizoOrientationSetting.Builder()
        .allowGravitySensor(true)
        .build()
)
```
{% endtab %}
{% endtabs %}

The `orientationSetting` builder sets the orientation-related property which is:

* <mark style="color:blue;">`allowGravitySensor`</mark>`(true)`: Enabling the Gravity sensor.

Once the desired orientation settings are configured using the builder, the `build()` method is called to create an instance of `GizoOrientationSetting` with the specified settings.

* **Gravity sensor:** It refers to an accelerometer sensor that provides measurements of both linear acceleration and the force of gravity acting on the device. It combines the data from the accelerometer sensor with information from other sensors such as the gyroscope and magnetometer to estimate the device's orientation in relation to the Earth's gravitational field.



Here is the available option that can be set in orientationSetting in the Application class:

<table><thead><tr><th width="227">Options</th><th width="141.33333333333331">Default Value</th><th>Descriptions</th></tr></thead><tbody><tr><td><p>allowGravitySensor</p><p>(Boolean)</p></td><td>false</td><td>To activate gravity sensor or not.</td></tr></tbody></table>
