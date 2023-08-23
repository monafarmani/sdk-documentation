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

# Permissions

## Overview

Permissions refer to the security mechanisms that control an application's access to specific resources or features of the device. These permissions are declared in the AndroidManifest.xml file and are essential for ensuring user privacy and security.

It's important to note that starting from Android 6.0 (API level 23), dangerous permissions are requested at runtime, even if they are declared in the manifest. This means that the user can grant or deny the permission when the application is running, and the application must handle the permission flow accordingly.

Managing permissions properly is crucial for maintaining user trust and ensuring that applications access only the necessary resources. Android Studio provides tools and APIs to handle permissions effectively and securely within your application.



## <mark style="color:purple;">Permissions Settings</mark>

The following permissions are required by the SDK:

<table><thead><tr><th width="348">PERMISSIONS</th><th>WHERE TO USE</th></tr></thead><tbody><tr><td>ACCESS_COARSE_LOCATION</td><td>In GPS setting.</td></tr><tr><td>ACCESS_FINE_LOCATION</td><td>In GPS setting.</td></tr><tr><td>CAMERA</td><td>In capturing videos.</td></tr><tr><td>ACCESS_NETWORK_STATE</td><td>In Mapbox navigation.</td></tr><tr><td>WRITE_EXTERNAL_STORAGE</td><td>In saving files in the download folder.</td></tr></tbody></table>

## <mark style="color:purple;">Permissions Helper</mark>&#x20;

So far, some permissions have been added to the manifest, but we need to add other helper permissions based on the settings we have made.

To do this, these lines of code should be added to an activity

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
 Gizo.app.permissionRequired 
```
{% endtab %}
{% endtabs %}

The line of code above gives us an array of strings that includes the required permissions based on the setting.



## Why Permissions Helper

* If we grant access to AnalysisSettings, we will also have access to the camera
* If the matrix file or TTC file is downloaded, it allows us to have external access too.
* If we have access to GPS settings, permissions of ACCESS\_COARSE\_LOCATION & ACCESS\_FINE\_LOCATION will be provided.&#x20;
* If the GPS setting file is downloaded, it allows us to have external access too.
* If the IMU setting file is downloaded, it allows us to have external access too.
* If the video setting file is downloaded, it allows us to have external access too.
* If we need external access and the SDK version is not higher than 29, permissions WRITE\_EXTERNAL\_STORAGE & READ\_EXTERNAL\_STORAGE will be available.&#x20;



## Required Permissions&#x20;

The following permissions are required by the SDK:

#### <mark style="color:blue;">ACCESS\_COARSE\_LOCATION</mark>

The ACCESS\_COARSE\_LOCATION permission is required to obtain the user's approximate location. This permission is used to provide location-based services to the user, such as displaying relevant content based on their location.

<mark style="color:red;">**Note:**</mark> This permission does not grant access to the user's precise location or any other location-related features, such as the ability to track the user's movements.

To request the ACCESS\_COARSE\_LOCATION permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">ACCESS\_FINE\_LOCATION</mark>&#x20;

The ACCESS\_FINE\_LOCATION permission is required to obtain the user's precise location. This permission is used to provide location-based services to the user, such as displaying nearby points of interest or providing turn-by-turn directions.

<mark style="color:red;">**Note:**</mark> This permission grants access to the user's precise location data, which can be used to track the user's movements. Make sure to handle the user's location data responsibly and in accordance with your app's privacy policy.

To request the ACCESS\_FINE\_LOCATION permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">CAMERA</mark>

&#x20;The CAMERA permission is required to capture images and scan QR codes. Without this permission, the SDK will not be able to perform these functions.

<mark style="color:red;">**Note:**</mark> This permission does not grant access to other camera-related features, such as the microphone or location data.

To request the CAMERA permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.CAMERA" />
```
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">ACCESS\_NETWORK\_STATE</mark>

The ACCESS\_NETWORK\_STATE permission is required to determine the user's network connectivity status. This permission is used to check if the user is connected to the internet or not, and to adjust the SDK's behavior accordingly.

To request the ACCESS\_NETWORK\_STATE permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">WRITE\_EXTERNAL\_STORAGE</mark>

&#x20;The WRITE\_EXTERNAL\_STORAGE permission is required to write files to the user's external storage, such as saving photos or documents. This permission is used to enable features of the SDK that require the ability to save files, such as file download or export functionality.

<mark style="color:red;">**Note:**</mark> This permission does not grant access to other external storage-related features, such as the ability to delete files.

To request the WRITE\_EXTERNAL\_STORAGE permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```
{% endtab %}
{% endtabs %}
