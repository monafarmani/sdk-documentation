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

# GizoVideoSetting

## Overview

Video settings on Gizo SDK refer to the various options and configurations that allow users to control and customize the video recording and playback experience. These settings can be accessed through the camera or video app on your mobile device.

Gizo video setting is used to customize some behavior and functionality of our library, including specifying the quality of video capturing and where to save video files.

To have access to video setting options, you need to add these lines of code in the Application class, onCreate function, inside Gizo.initialize.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
.videoSetting(
    GizoVideoSetting.Builder()
        .quality(Quality.HD)
        .fileLocation(FileLocationPath.CACHE)
        .build()
)
```
{% endtab %}
{% endtabs %}

The `GizoVideoSetting` builder sets the video-related properties such as `quality` (setting the video quality to HD quality), and `fileLocation` (specifying the file location path for storing the video files, in this case, set to the cache directory).

Finally, the `build()` method is called on the `GizoAppOptions.Builder()` instance to create a `GizoAppOptions` object with the configured video settings.

This code suggests that the `GizoAppOptions` class provides a way to specify various configuration options for the `Gizo` application, including video-related settings. The specific implementation and usage of `GizoAppOptions` would depend on the details of the `Gizo` application itself.



Here are the available options that can be set in videoSetting in the Application class:

<table><thead><tr><th width="227.33333333333331">Options</th><th width="213">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>quality(Quality)</td><td>Quality.HD</td><td>To define the quality of video capturing.</td></tr><tr><td><p>fileLocation</p><p>(FileLocationPath)</p></td><td><p>FileLocationPath</p><p>.CACHE</p></td><td>To save video files in download or cache.</td></tr></tbody></table>
