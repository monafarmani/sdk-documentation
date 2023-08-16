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
gizoAnalysis.onSessionStatus = { isRecording, previewAttached ->
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis component likely represents a module or functionality within the application responsible for managing sessions and their associated status.

Inside the lambda expression, the code block that would be executed when a change in the session status occurs is not provided in the given snippet. However, within this code block, you might find logic to handle the updated session status. For example, the application could perform actions based on whether the recording is in progress (isRecording) or if a preview is currently attached (previewAttached). This could involve updating the user interface, triggering specific behaviors, or performing other operations based on the current session status.



### <mark style="color:purple;">Analysis listener</mark>

In our SDK, we require accurate and efficient detection and localization of objects in images and video streams and also accurate and efficient estimation of the depth or distance of objects in a scene and we gain these data with Gizo Analysis Setting.

When Analysis gets activated, these value parameters can be checked out:

<table><thead><tr><th width="203">Value-Parameters</th><th width="145">Type</th><th>Description</th></tr></thead><tbody><tr><td>result</td><td>Bitmap?</td><td>It outputs an image that includes object detection &#x26; road lines.</td></tr><tr><td>fps</td><td>String</td><td>It provides the analysis time on the output image in milliseconds.</td></tr><tr><td>ttc</td><td>Float?</td><td>Time to collision.</td></tr><tr><td>ttcStatus</td><td>TTCAlert</td><td>It returns state <strong>danger</strong>, <strong>warning</strong>, and <strong>None</strong> based on the calculated formula in the TTC.</td></tr><tr><td>ttcDepthPtn</td><td>String</td><td>The distance to the front car.</td></tr><tr><td>speed</td><td>Float?</td><td>The speed of the car the user is driving in.</td></tr><tr><td>gpsTime</td><td>String</td><td>The current time.</td></tr><tr><td>collisionThreshold </td><td>Float</td><td>It provides a number that determines the specific status of danger, warning, or none.</td></tr></tbody></table>



Gain these parameters with the codes below in Preview:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.onAnalysisResult = { result, fps, ttc, ttcStatus,
ttcDepthPtn, speed, gpsTime ->
 
}
```
{% endtab %}
{% endtabs %}

The gizoAnalysis property is responsible for analyzing data and processing results.

The lambda expression assigned to the onAnalysisResult property takes several parameters: result, fps, ttc, ttcStatus, ttcDepthPtn, speed, and gpsTime. These parameters likely represent various analysis results and related information.

Within this code block, you might find logic to handle the analysis results and utilize the provided information. This may mean showing the analysis result, changing the interface, saving the result for later, or taking actions based on the outcome...



We can write a customized formula and calculate the TTC in Preview too.

{% tabs %}
{% tab title="Kotlin" %}
<pre class="language-kotlin"><code class="lang-kotlin"><strong>Gizo.app.gizoAnalysis.ttcCalculator { depthPtn, speed, ttc ->
</strong>    ttc
}
</code></pre>
{% endtab %}
{% endtabs %}

**Note:** The purpose of this code is to calculate the Time to Collision (TTC) using the provided `depthPtn` and `speed` values. The calculated TTC is then returned as the result of the function call & can be used in the previous tab of the code.



We can calculate the customized ttcStatus based on depthPtn, speed, collisionThreshold, and TTC in Preview too.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.ttcStatusCalculator { ttc, speed, collisionThreshold, ttcStatus ->
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

The lambda expression takes two parameters: location and isGpsOn. Location is the updated GPS info, including latitude, longitude, and other relevant details.. isGpsOn is a boolean parameter that indicates whether the GPS functionality is currently enabled on the device.

Within this code block, you might find logic to handle the updated location. For example, the application could update the user interface to display the new location information, trigger specific processes or calculations based on the new location, or save the location data for future use.



