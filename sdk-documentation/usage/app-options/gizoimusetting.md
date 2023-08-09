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

The IMU settings in MyTestSDK allow developers to utilize the sensors that make up the device's IMU. The IMU typically consists of the **accelerometer**, **gyroscope** and **gravity**.

For this reason , Add these lines of code in Application class , onCreate function , inside Gizo.initialize to set the Gizo GPS Settings.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
  .imuSetting(
      GizoImuSetting.Builder()
          .allowLinearAccelerationSensor(true)
          .allowGravitySensor(true)
          .allowGyroscopeSensor(true)
          .saveCsvFile(true)
          .imuDataTimerPeriod(5000L)
          .build()
                )
```
{% endtab %}
{% endtabs %}

* **Linear acceleration sensor:** It is part of the device's sensor array and is used to measure the linear acceleration of the device, excluding the influence of gravity.
* **Gravity sensor:** It is part of the device's sensor array and is used to measure the gravitational force acting on the device.
* **Gyroscope sensor:** It is part of the device's sensor array and is used to measure the device's angular velocity or rotational motion. The gyroscope provides information about the device's orientation and rotation rate.

Here are the available options that can be set in imuSetting in the Application class:

<table><thead><tr><th width="286.3333333333333">Options</th><th width="198">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><p>allowLinearAccelerationSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate linear acceleration sensor or not</td></tr><tr><td><p>allowGyroscopeSensor</p><p>(Boolean)</p></td><td>false</td><td>To activate gyroscope sensor or not</td></tr><tr><td><p>allowGravitySensor</p><p>(Boolean)</p></td><td>false</td><td>To activate gravity sensor or not</td></tr><tr><td><p>saveCsvFile</p><p>(Boolean)</p></td><td>false</td><td>To save CSV file or not</td></tr><tr><td><p>fileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>To save IMU file in download or cache</td></tr><tr><td>imuDataTimerPeriod(Long)</td><td>10L</td><td>The period of time that an IMU data row is saved in CSV file</td></tr><tr><td>imuDataTimerInitialDelay(Long)</td><td>0L</td><td>The initial delay to save IMU data</td></tr><tr><td><p>saveDateTimeFormat</p><p>(String)</p></td><td><p>"yyyy-MM-dd</p><p>'T'HH-mm-ss-SSS'Z'"</p></td><td>The format to save date time</td></tr></tbody></table>
