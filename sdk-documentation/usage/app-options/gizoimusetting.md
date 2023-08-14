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

# GizoImuSetting

## Overview

The IMU setting in MyTestSDK allows developers to utilize the sensors that make up the device’s IMU. The IMU typically consists of the **accelerometer**, **gyroscope,** and **gravity**.

Gizo IMU setting is used to customize some behavior and functionality of our library including specifying where to save IMU files, the period of time that an IMU data row is saved in a CSV file, the initial delay to save IMU data, the format to save date time and so on...

For this reason, add these lines of code in the Application class, onCreate function, inside Gizo.initialize to set the Gizo GPS Settings.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
  .imuSetting(
      GizoImuSetting.Builder()
          .allowLinearAccelerationSensor(true)
          .allowGravitySensor(true)
          .allowGyroscopeSensor(true)
          .saveCsvFile(true)
          .fileLocation(GizoFileLocationPath.CACHE)
          .imuDataTimerPeriod(5000L)
          .imuDataTimerInitialDelay(0L)
          .saveDataDateTimeFormat("yyyy-MM-dd'T'HH-mm-ss-SSS'Z'")
          .build()
  )
```
{% endtab %}
{% endtabs %}

The `GizoImuSetting` builder sets the IMU-related properties such as:

* <mark style="color:blue;">`allowLinearAccelerationSensor`</mark>`(true)`: Enabling the Linear Acceleration sensor.
* <mark style="color:blue;">`allowGravitySensor`</mark>`(true)`: Enabling the Gravity sensor.
* <mark style="color:blue;">`allowGyroscopeSensor`</mark>`(true)`: Enabling the Gyroscope sensor.
* <mark style="color:blue;">`saveCsvFile`</mark>`(true)`: Indicating that the IMU data should be saved to a CSV file.
* <mark style="color:blue;">`fileLocation`</mark>`(GizoFileLocationPath.CACHE)`: Specifying the file location path for storing the IMU data CSV file (in this case, set to the cache directory).
* <mark style="color:blue;">`imuDataTimerPeriod`</mark>`(5000L)`: Setting the period of the IMU data timer to 5000 milliseconds (5 seconds).
* <mark style="color:blue;">`imuDataTimerInitialDelay`</mark>`(0L)`: Setting the initial delay of the IMU data timer to 0 milliseconds (no delay).
* <mark style="color:blue;">`saveDataDateTimeFormat`</mark>`("yyyy-MM-dd'T'HH-mm-ss-SSS'Z'")`: Specifying the date and time format for saving the IMU data file.

Finally, the `build()` method is called on the `GizoAppOptions.Builder()` instance to create a `GizoAppOptions` object with the configured IMU settings.

This code suggests that the `GizoAppOptions` class specifies various configuration options for the `Gizo` application, including IMU-related settings. The specific implementation and usage of `GizoAppOptions` would depend on the details of the `Gizo` application itself.



* **Linear acceleration sensor:** It is part of the device's sensor array and is used to measure the linear acceleration of the device, excluding the influence of gravity.
* **Gravity sensor:** It is part of the device's sensor array and is used to measure the gravitational force acting on the device.
* **Gyroscope sensor:** It is part of the device's sensor array and is used to measure the device's angular velocity or rotational motion. The gyroscope provides information about the device's orientation and rotation rate.



Here are the available options that can be set in imuSetting in the Application class:

<table><thead><tr><th width="286.3333333333333">Options</th><th width="198">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><p>allowLinearAccelerationSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate linear acceleration sensor or not.</td></tr><tr><td><p>allowGyroscopeSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate gyroscope sensor or not.</td></tr><tr><td><p>allowGravitySensor</p><p>(Boolean)</p></td><td>false</td><td>To activate gravity sensor or not.</td></tr><tr><td><p>saveCsvFile</p><p>(Boolean)</p></td><td>false</td><td>To save CSV file or not.</td></tr><tr><td><p>fileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>To save the imu file in download or cache.</td></tr><tr><td>imuDataTimerPeriod(Long)</td><td>10L</td><td>The period of time that an IMU data row is saved in CSV file.</td></tr><tr><td>imuDataTimerInitialDelay(Long)</td><td>0L</td><td>The initial delay to save IMU data.</td></tr><tr><td><p>saveDateDateTimeFormat</p><p>(String)</p></td><td><p>"yyyy-MM-dd</p><p>'T'HH-mm-ss-SSS'Z'"</p></td><td>The format to save date time.</td></tr></tbody></table>





