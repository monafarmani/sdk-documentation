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
