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

# App Options

## Overview

The SDK provides several options that can be configured at the app level to customize its behavior.&#x20;

Welcome to the App Options section of our Android library! This section provides you with the flexibility to customize the behavior and functionality of our library according to your specific needs and these options can be set in the Application class of your app. By modifying these settings, you can tailor the library's features and options to seamlessly integrate with your application and deliver a personalized user experience.

In this documentation, we will walk you through the various settings available and explain how each setting influences the library's behavior. You'll find detailed descriptions, default values & usage examples for each setting to help you understand their purpose and make informed decisions when configuring the library.

Please refer to the following sections for detailed information on each setting, including usage examples.&#x20;

Let's dive in and discover the settings that will empower you to make the most of our Android library!



## Setting App Options

To set app options for the SDK, you will need to create a new instance of the Application class in your app's module and set the desired options:

{% tabs %}
{% tab title="Kotlin" %}
<pre class="language-kotlin"><code class="lang-kotlin"><strong>class Application : Application() {
</strong>    override fun onCreate() {
        super.onCreate()

        Gizo.initialize(
            this,
            GizoAppOptions.Builder()
                .debug(true)
                .folderName("GizoSample")
                .analysisSetting(GizoAnalysisSettings.Builder().build())
                .imuSetting(GizoImuSetting.Builder().build())
                .gpsSetting(GizoGpsSetting.Builder().build())
                .videoSetting(GizoVideoSetting.Builder().build())
                .batterySetting(GizoBatterySetting.Builder().build())
                .build()
        )
    }
}
</code></pre>
{% endtab %}
{% endtabs %}

In the example above, we initialize the SDK instance as before and then create a new instance of the GizoAppOptions class and set the desired options using the builder pattern.



## Available Options

&#x20;Here are the available options that can be set in the Application class:

<table><thead><tr><th width="224.33333333333331">Option</th><th width="143">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>debug(Boolean)</td><td>true</td><td>Set to enable debugging log feature.</td></tr><tr><td>folderName(String)</td><td>"Gizo"</td><td>Set to save files in a download folder with this name.</td></tr><tr><td><p>analysisSetting</p><p>(<a href="broken-reference">GizoAnalysisSettings</a>)</p></td><td>null</td><td>Set to activate analyzing model &#x26; main export of the SDK.</td></tr><tr><td><p>imuSetting</p><p>(<a href="broken-reference">GizoImuSetting</a>)</p></td><td>null</td><td>Set to activate some sensors, such as LinearAccelerationSensor , GyroscopeSensor &#x26; GravitySenso, and get callbacks.</td></tr><tr><td><p>gpsSetting</p><p>(<a href="broken-reference">GizoGpsSetting</a>)</p></td><td>null</td><td>Set to provide location information to use in speed limit.</td></tr><tr><td><p>videoSetting</p><p>(<a href="broken-reference">GizoVideoSetting</a>)</p></td><td>null</td><td>Set the video export.</td></tr><tr><td><p>batterySetting</p><p>(<a href="broken-reference">GizoBatterySetting</a>)</p></td><td>null</td><td>Set the required implementation when the battery is in different status.</td></tr></tbody></table>



* **GizoAnalysisSetting** allows developers to gain some data based on the image caught from the camera and get object detection & depth estimation.
* **GizoImuSetting** allows developers to utilize the sensors that make up the device's IMU. The IMU typically consists of the **accelerometer**, **gyroscope,** and **gravity**.
* **GizoGpsSetting** provides instructions on enabling GPS, accessing location, speed limit, and speed.
* **GizoVideoSetting** refers to the configuration and utilization of video-related features and components within an Android application. Video settings typically involve tasks, such as capturing video from the device’s camera, playing video files, or streaming video content.
* **GizoBatterySetting** refers to the configuration and management options related to the device's battery usage and performance. These settings allow users to monitor and control the battery usage of their mobile devices.
