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

# Listeners

## Overview

Callback listeners provide a way to handle user interactions and system events in Android applications. They allow you to customize the behavior of your app based on the events that occur, making your application more interactive and responsive to user actions.

Callback listeners allow you to register a listener object that will be notified when a specific event occurs. The listener object contains a set of callback methods that will be called by the system when the associated event occurs. These events include Analysis, IMU Sensors, GPS, Video, and Battery.



### <mark style="color:purple;">Session Status listener</mark>

As previously stated, based on the settings we have applied, some files related to video, analysis, GPS, and IMU are saved.

When the Start Session gets activated, these value parameters can be checked out:

<table><thead><tr><th width="370">Value-parameters</th><th width="127">Type</th><th>Description</th></tr></thead><tbody><tr><td>inProgress</td><td>Boolean</td><td>To check whether the camera is recording or not.</td></tr><tr><td>previewAttached</td><td>Boolean</td><td>To check whether the preview is attached or not.</td></tr></tbody></table>



Gain these parameters with the codes below in Preview

{% tabs %}
{% tab title="Kotlin" %}
```kts
gizoAnalysis.onSessionStatus = { inProgress, previewAttached ->
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis component likely represents a module or functionality within the application responsible for managing sessions and their associated status.

Inside the lambda expression, the code block that would be executed when a change in the session status occurs is not provided in the given snippet. However, within this code block, you might find logic to handle the updated session status. For example, the application could perform actions based on whether the recording is in progress (inProgress) or if a preview is currently attached (previewAttached). This could involve updating the user interface, triggering specific behaviors, or performing other operations based on the current session status.



### <mark style="color:purple;">Analysis listener</mark>

In our SDK, we require accurate and efficient detection and localization of objects in images and video streams and also accurate and efficient estimation of the depth or distance of objects in a scene and we gain these data with Gizo Analysis Setting.

When Analysis gets activated, these value parameters can be checked out:

<table><thead><tr><th width="203">Value-Parameters</th><th width="145">Type</th><th>Description</th></tr></thead><tbody><tr><td>preview</td><td>Bitmap?</td><td>It outputs an image that includes object detection &#x26; road lines.</td></tr><tr><td>ttc</td><td>Float?</td><td>Time to collision.</td></tr><tr><td>ttcStatus</td><td>TTCAlert</td><td>It returns state <strong>collision</strong>, <strong>tailgating</strong>, and <strong>None</strong> based on the calculated formula in the TTC.</td></tr><tr><td>frontObject</td><td>String</td><td>The distance to the front car.</td></tr><tr><td>speed</td><td>Float?</td><td>The speed of the car the user is driving in.</td></tr><tr><td>gpsTime</td><td>String</td><td>The current time.</td></tr></tbody></table>



Gain these parameters with the codes below in Preview:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onAnalysisResult = { preview, ttc, ttcStatus,
frontObject, speed, gpsTime ->
 
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis property is responsible for analyzing data and processing results.

The lambda expression assigned to the onAnalysisResult property takes several parameters: preview, ttc, ttcStatus, frontObject, speed, and gpsTime. These parameters likely represent various analysis results and related information.

Within this code block, you might find logic to handle the analysis results and utilize the provided information. This may mean showing the analysis result, changing the interface, saving the result for later, or taking actions based on the outcome...



We can write a customized formula and calculate the TTC in Preview too.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.ttcCalculator { frontObject, speed, ttc ->
    ttc
}
```
{% endtab %}
{% endtabs %}

**Note:** The purpose of this code is to calculate the Time to Collision (TTC) using the provided `depthPtn` and `speed` values. The calculated TTC is then returned as the result of the function call & can be used in the previous tab of the code.



We can calculate the customized ttcStatus based on depthPtn, speed, and TTC in Preview too.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.ttcStatusCalculator { ttc, speed, ttcStatus ->
  ttcStatus
}
```
{% endtab %}
{% endtabs %}

**Note:** The exact implementation of the `ttcStatusCalculator` function is not provided in the given snippet, but it is expected to perform the necessary calculations and logic to determine the TTC status based on the input parameters. The `ttcStatus` variable is likely updated within the function to reflect the calculated TTC status.

After the `ttcStatus` is calculated, it is returned as the result of the function call & can be used in the previous tab of the code.



### <mark style="color:purple;">GPS listener</mark>

As mentioned earlier, this documentation provides instructions on enabling GPS, accessing location, speed limit, and speed.

When GPS gets activated, these value parameters can be checked out:

<table><thead><tr><th width="196">Value-parameters</th><th width="159">Type</th><th>Description</th></tr></thead><tbody><tr><td>location</td><td>Location?</td><td>The location of the user.</td></tr><tr><td>isGpsOn</td><td>Boolean?</td><td>To check whether GPS is on or not.</td></tr><tr><td>speedLimitKph</td><td>Int?</td><td>speed limit kilometer per hour</td></tr><tr><td>speedKph</td><td>Int</td><td>speed kilometer per hour</td></tr></tbody></table>

**Location** refers to the specific geographical coordinates that indicate the position of a GPS receiver or device on the Earth's surface. It represents the latitude and longitude coordinates that define a particular point on the map.



Gain these parameters with the codes below in Preview

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onLocationChange = { location, isGpsOn ->
   
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis object is likely a component responsible for analyzing and processing location data. By assigning a lambda expression to the onLocationChange property, the application can respond to changes in the device’s location.

The lambda expression takes two parameters: location and isGpsOn. Location is the updated GPS info, including latitude, longitude, and other relevant details.. isGpsOn is a Boolean parameter that indicates whether the GPS functionality is currently enabled on the device.

Within this code block, you might find logic to handle the updated location. For example, the application could update the user interface to display the new location information, trigger specific processes or calculations based on the new location, or save the location data for future use.



{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onSpeedChange = { speedLimitKph, speedKph ->
    
}
```
{% endtab %}
{% endtabs %}

The `gizoAnalysis` object is likely a component responsible for analyzing and processing speed-related data. By assigning a lambda expression to the `onSpeedChange` property, the application can respond to changes in the device's speed.

The lambda expression takes two parameters: `speedLimitKph` and `speedKph`. `speedLimitKph` represents the speed limit in kilometers per hour (KPH) that is applicable to the current location or context. `speedKph` represents the current speed of the device or vehicle in KPH.

Inside the lambda expression, the code block that would be executed when a speed change is detected is not provided in the given snippet. However, within this code block, you might find logic to handle the updated speed. For example, the application could compare the current speed with the speed limit and trigger alerts or warnings if the speed exceeds the limit. The user interface could also be updated to display the updated speed information, providing real-time feedback to the user. Additionally, further calculations or analysis based on the speed data could be performed within this code block.



### <mark style="color:purple;">IMU listener</mark>

As previously mentioned, the IMU setting in Gizo SDK allows developers to utilize the sensors that make up the device’s IMU. The IMU typically consists of the accelerometer, gyroscope, and gravity.

When IMU gets activated, these value parameters can be checked out:

<table><thead><tr><th width="238">Value-parameters</th><th width="152">Type</th><th>Description</th></tr></thead><tbody><tr><td>accelerationSensorEvent</td><td>SensorEvent?</td><td>includes information such as Acceleration values, Timestamps &#x26; Accuracy, or precision.</td></tr><tr><td>gyroscopeSensorEvent</td><td>SensorEvent?</td><td>includes information such as Angular velocity values, timestamps &#x26; Accuracy, or precision.</td></tr><tr><td>gravitySensorEvent</td><td>SensorEvent?</td><td>includes information such as Gravity values, timestamps &#x26; Accuracy, or precision.</td></tr><tr><td>isAlign</td><td>Boolean</td><td>Whether the mobile device is in a landscape orientation or not.</td></tr></tbody></table>



Gain these parameters with the codes below in Preview

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onLinearAccelerationSensor={ accelerationSensorEvent->
   
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis object is likely a component responsible for analyzing and processing data from the linear acceleration sensor. Assigning a lambda expression to the onLinearAccelerationSensor property lets the application respond to events triggered by the linear acceleration sensor..

The lambda expression uses accelerationSensorEvent as the input, which comes from the linear acceleration sensor. This event data typically includes information about the acceleration of the device along various axes, such as the X, Y, and Z axes.

Within this code block, you might find logic to handle the received acceleration data. For example, the application could analyze the acceleration values to detect specific motion patterns, such as shaking or sudden movements. The user interface could be updated to provide real-time feedback based on the acceleration values, such as displaying animations or triggering sound effects. Additionally, the acceleration data could be used to trigger specific behaviors or calculations within the application.



{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onGyroscopeSensor={ gyroscopeSensorEvent->
  
}
```
{% endtab %}
{% endtabs %}

The `gizoAnalysis` object is likely a component responsible for analyzing and processing data from the gyroscope sensor. By assigning a lambda expression to the `onGyroscopeSensor` property, the application can respond to events triggered by the gyroscope sensor.

The lambda expression takes a single parameter `gyroscopeSensorEvent`, which represents the event data received from the gyroscope sensor. This event data typically includes information about the device's rotational movement along different axes, such as the X, Y, and Z axes.

Within this code block, you might find logic to handle the received gyroscope data. For example, the application could analyze the gyroscope values to detect specific types of rotation or gestures, such as tilting, shaking, or rotating the device. The user interface could be updated to reflect the device's orientation or movement, such as adjusting the display based on the device's tilt or triggering animations based on rotation. Additionally, the gyroscope data could be used to trigger specific behaviors or calculations within the application.



{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onGravitySensor={ gravitySensorEvent->
   
}
```
{% endtab %}
{% endtabs %}

The `gizoAnalysis` property is responsible for analyzing and processing data from various sensors, including the gravity sensor.

The lambda expression assigned to the `onGravitySensor` property takes a single parameter `gravitySensorEvent`, which represents the event data received from the gravity sensor.

Within this code block, you might find logic to handle the received gravity sensor data. For example, the application could analyze the gravity data to determine the device's orientation or position relative to gravity. This could be used to detect tilts or changes in orientation, allowing the application to respond accordingly. The gravity sensor data could also be used to update the user interface, trigger specific behaviors, or perform calculations based on the device's orientation.



{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onImuSensor = { linearAccelerationEvent, gyroscopeEvent, gravityEvent ->

}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis property is responsible for analyzing and processing data from various sensors, including the IMU sensor.

The lambda expression assigned to the onImuSensor property takes three parameters: linearAccelerationEvent, gyroscopeEvent, and gravityEvent. These parameters represent the event data received from the linear acceleration sensor, gyroscope sensor, and gravity sensor, respectively.

Within this code block, you might find logic to handle the received sensor data. For example, the application could combine linear acceleration, gyroscope, and gravity data to calculate various metrics related to the device’s motion, orientation, or position in three-dimensional space. This could be used to detect device tilt, rotation, or movements in different directions. The application could then respond accordingly, such as updating the user interface, triggering specific behaviors, or performing calculations based on the derived met



In Gizo SDK, if our mobile device is in landscape orientation, the listener calls back true. (isAlign would be true)

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.checkGravityAlignment { isAlign ->
}
```
{% endtab %}
{% endtabs %}

Landscape screen orientation in mobile devices refers to a display mode where the screen is wider than it is tall, resembling the shape of a landscape. In this orientation, the device is typically held horizontally, with the longer edge of the screen parallel to the ground.

When a mobile device is in landscape orientation, the user interface and content on the screen adjust accordingly to make optimal use of the wider space. This orientation is commonly used for activities that benefit from a wider viewing area, such as watching videos, playing games, or viewing wide documents or images.



### <mark style="color:purple;">Video listener</mark>

In mobile devices, the "video settings" typically refer to the configurable options and parameters that allow users to customize various aspects of video recording or playback. These settings can vary depending on the specific device, operating system, and camera capabilities.

When the video gets activated, this value parameter can be checked out:

<table><thead><tr><th width="179.33333333333331">Value-parameter</th><th width="181">Type</th><th>Description</th></tr></thead><tbody><tr><td>event</td><td>VideoRecordEvent</td><td>Used to report video recording events and status.</td></tr></tbody></table>



Gain these parameters with the codes below in Preview

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
gizoAnalysis.onRecordingEvent { event ->
 
}
```
{% endtab %}
{% endtabs %}

The `gizoAnalysis` component likely represents a module or functionality within the application that is responsible for managing recording-related operations.

The lambda expression assigned to the `onRecordingEvent` property takes a single parameter, `event`, which represents the recording event that has occurred.

Within this code block, you might find logic to handle different recording events and perform specific actions based on the event type. For example, the application could respond to events such as recording start, stop, pause, resume, or completion. This could involve updating the user interface, notifying the user, performing additional processing or analysis on the recorded data, or triggering other related operations.



Here there is an example of a sample of using event in your app.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
when (event) {
    is VideoRecordEvent.Finalize -> {
        if (event.hasError()) {
            //Do something
        }
    }
}
```
{% endtab %}
{% endtabs %}

When a recording event occurs, the code checks if the event is an instance of `VideoRecordEvent.Finalize` using the `is` keyword. If it matches, the code block within the corresponding branch is executed.

Inside the `VideoRecordEvent. Finalize` branch, there is an additional check using the `hasError()` function. This function likely checks if the event contains any error information. If the event has an error, the code block within the `if` statement is executed. However, the actual implementation of what should be done when an error occurs is not provided in the given snippet, as it is commented as "//Do something". You would need to replace that comment with the appropriate code that handles the error, such as displaying an error message, logging the error, or taking any necessary corrective action.



### <mark style="color:purple;">Battery listener</mark>

Battery settings on the Gizo SDK library refer to the configuration and management options related to the device’s battery usage and performance. These settings allow users to monitor and control the battery usage of their mobile devices.

When the battery gets activated, this value parameter can be checked out:

<table><thead><tr><th width="184">Value-parameter</th><th width="142">Type</th><th>Description</th></tr></thead><tbody><tr><td>status</td><td>BatteryStatus</td><td>To check what is the battery status: LOW_BATTERY_STOP, LOW-BATTERY_WARNING, or NORMAL</td></tr></tbody></table>



Gain this parameter with the codes below in Preview

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onBatteryStatusChange = { status ->
 
 }
```
{% endtab %}
{% endtabs %}

The `gizoAnalysis` property is responsible for analyzing and processing various aspects of the application, including monitoring the battery status.

The lambda expression assigned to the `onBatteryStatusChange` property takes a single parameter `status`, which represents the updated battery status.

Inside the lambda expression, the code block that would be executed when a change in the battery status occurs is not provided in the given snippet. However, within this code block, you might find logic to handle the updated battery status. For example, the application could perform actions based on the current battery level, such as adjusting power consumption, displaying a low battery warning, or triggering specific behaviors when the battery reaches a certain threshold.
