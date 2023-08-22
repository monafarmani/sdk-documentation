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

The IMU setting in MyTestSDK allows developers to utilize the sensors that make up the device’s IMU. The IMU typically consists of the **accelerometer**, **gyroscope,** and **magnetometer**.

Gizo IMU setting is used to customize some behavior and functionality of our library including specifying where to save IMU files, the period of time that an IMU data row is saved in a CSV file, the initial delay to save IMU data, the format to save date time and so on...

For this reason, add these lines of code in the Application class, onCreate function, inside Gizo.initialize to set the Gizo IMU Settings.



{% tabs %}
{% tab title="kotlin" %}
```kotlin
.imuSetting(
      GizoImuSetting.Builder()
          .allowAccelerationSensor(true)
          .allowMagneticSensor(true)
          .allowGyroscopeSensor(true)
          .saveCsvFile(true)
          .useAccelerationRawType(false)
          .fileLocation(GizoFileLocationPath.CACHE)
          .imuDataTimerPeriod(10L)
          .imuDataTimerInitialDelay(0L)
          .saveDataDateTimeFormat("yyyy-MM-dd'T'HH-mm-ss-SSS'Z'")
          .build()
  )
```
{% endtab %}
{% endtabs %}

* <mark style="color:blue;">`allowAccelerationSensor`</mark>`(true)`: Enabling the Acceleration sensor.
* <mark style="color:blue;">`allowMagneticSensor`</mark>`(true)`: Enabling the Magnetic sensor.
* <mark style="color:blue;">`allowGyroscopeSensor`</mark>`(true)`: Enabling the Gyroscope sensor.
* <mark style="color:blue;">`saveCsvFile`</mark>`(true)`: Indicating that the IMU data should be saved to a CSV file.
* <mark style="color:blue;">`useAccelerationRawType`</mark>`(true)`: indicating the type of the Acceleration sensor.
* <mark style="color:blue;">`fileLocation`</mark>`(GizoFileLocationPath.CACHE)`: Specifying the file location path for storing the IMU data CSV file (in this case, set to the cache directory).
* <mark style="color:blue;">`imuDataTimerPeriod`</mark>`(10L)`: Setting the period of the IMU data timer to 5000 milliseconds (5 seconds).
* <mark style="color:blue;">`imuDataTimerInitialDelay`</mark>`(0L)`: Setting the initial delay of the IMU data timer to 0 milliseconds (no delay).
* <mark style="color:blue;">`saveDataDateTimeFormat`</mark>`("yyyy-MM-dd'T'HH-mm-ss-SSS'Z'")`: Specifying the date and time format for saving the IMU data file.

**Note:** saveDatadateTimeFormat will be changed if It's going to be used locally.&#x20;



Finally, the `build()` method is called on the `GizoAppOptions.Builder()` instance to create a `GizoAppOptions` object with the configured IMU settings.

This code suggests that the `GizoAppOptions` class specifies various configuration options for the `Gizo` application, including IMU-related settings. The specific implementation and usage of `GizoAppOptions` would depend on the details of the `Gizo` application itself.



* &#x20;**Accelerometer:** It is a sensor commonly found in mobile devices that measures acceleration forces acting on the device in three dimensions: along the x-axis (horizontal), y-axis (vertical), and z-axis (perpendicular to the device's screen). It detects changes in velocity and movement, allowing the device to respond to various types of motion.
* **Linear acceleration sensor:** It is part of the device's sensor array and is used to measure the linear acceleration of the device, excluding the influence of gravity.
* **Magnetic sensor:** It is a sensor that measures the strength and direction of the magnetic field in its vicinity. It is typically used to detect the presence of a magnetic field and determine its orientation.
* **Gyroscope sensor:** It is part of the device's sensor array and is used to measure the device's angular velocity or rotational motion. The gyroscope provides information about the device's orientation and rotation rate.



Here are the available options that can be set in imuSetting in the Application class:

<table><thead><tr><th width="286.3333333333333">Options</th><th width="198">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><p>allowAccelerationSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate the acceleration sensor or not.</td></tr><tr><td><p>allowGyroscopeSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate the gyroscope sensor or not.</td></tr><tr><td><p>allowMagneticSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate the magnetic sensor or not.</td></tr><tr><td><p>saveCsvFile</p><p>(Boolean)</p></td><td>false</td><td>To save CSV file or not.</td></tr><tr><td><p>useAccelerationRawType</p><p>(Boolean)</p></td><td>false</td><td>To use either Raw type or Linear type of Acceleration sensor. </td></tr><tr><td><p>fileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>To save the IMU file in download or cache.</td></tr><tr><td>imuDataTimerPeriod(Long)</td><td>10L</td><td>The period of time that an IMU data row is saved in CSV file.</td></tr><tr><td>imuDataTimerInitialDelay(Long)</td><td>0L</td><td>The initial delay to save IMU data.</td></tr><tr><td><p>saveDateDateTimeFormat</p><p>(String)</p></td><td><p>"yyyy-MM-dd</p><p>'T'HH-mm-ss-SSS'Z'"</p></td><td>The format to save date time.</td></tr></tbody></table>









