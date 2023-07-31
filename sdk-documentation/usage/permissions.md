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

## <mark style="color:purple;">Permissions settings</mark>

The following permissions are required by the SDK:

<table><thead><tr><th width="348">PERMISSIONS</th><th>WHERE TO USE</th></tr></thead><tbody><tr><td>ACCESS_COARSE_LOCATION</td><td>in GPS setting.</td></tr><tr><td>ACCESS_FINE_LOCATION</td><td>in GPS setting.</td></tr><tr><td>CAMERA</td><td>in capturing videos.</td></tr><tr><td>ACCESS_NETWORK_STATE</td><td>in mapbox navigation.</td></tr><tr><td>WRITE_EXTERNAL_STORAGE</td><td>in saving files in download folder.</td></tr></tbody></table>

## Permissions Required

The following permissions are required by the SDK:

#### <mark style="color:blue;">ACCESS\_COARSE\_LOCATION</mark>

The ACCESS\_COARSE\_LOCATION permission is required to obtain the user's approximate location. This permission is used to provide location-based services to the user, such as displaying relevant content based on their location.

**Note**: This permission does not grant access to the user's precise location or any other location-related features, such as the ability to track the user's movements.

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

**Note**: This permission grants access to the user's precise location data, which can be used to track the user's movements. Make sure to handle the user's location data responsibly and in accordance with your app's privacy policy.

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

**Note**: This permission does not grant access to other camera-related features, such as the microphone or location data.

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

**Note**: This permission does not grant access to other external storage-related features, such as the ability to delete files.

To request the WRITE\_EXTERNAL\_STORAGE permission in your app, add the following line to your app's Manifest file:

{% tabs %}
{% tab title="xml" %}
```kotlin
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```
{% endtab %}
{% endtabs %}
