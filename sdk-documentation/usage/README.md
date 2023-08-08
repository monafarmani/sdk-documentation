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

# ⚙ Usage

To use MyTestSDK in your app, follow these steps:

* To start to use the SDK we need to start the [Gizo Analysis](broken-reference). for this reason we need a lifecycle like an activity or a fragment and implement some lines of code in Main Activity. Based on the [settings](broken-reference) applied by the developers, a series of features will be added to the SDK .
* The SDK requires certain [permissions ](permissions.md)in order to function properly. These permissions are necessary to enable the GPS setting, capturing videos, mapbox navigation & saving files in download folder.
* The SDK provides several [options ](broken-reference)that can be configured at the app level to customize its behavior. These options can be set in the Application class of your app.
* Model loading which was explained in [Analysis setting](broken-reference).
* Using a [callback listener](broken-reference) which is a mechanism that allows you to register a listener object that will be notified when a specific event occurs. The listener object contains a set of callback methods that will be called by the system when the associated event occurs. These events include Analysis, IMU Sensors, GPS, Video and Battery.
* The SDK provides some [features ](broken-reference)that can be used to control some trends of recording the videos.

































##
