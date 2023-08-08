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

# Gizo Analysis

### <mark style="color:purple;">Start Gizo Analysis</mark>

To start using the SDK we need to start Gizo Analysis. for this reason we need a lifecycle like an activity or a fragment and implement these lines of code in the Activity.

Based on the [settings](broken-reference) applied by the developer, a series of features will be added to the sdk.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
 Gizo.app.gizoAnalysis.start(lifecycleOwner = this, onDone = {})
```
{% endtab %}
{% endtabs %}

**onDone is called when start Gizo Analysis is completed.**

### <mark style="color:purple;">Stop Gizo Analysis</mark>

When Stop Gizo Analysis is called all settings get inactive.&#x20;

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
  Gizo.app.gizoAnalysis.stop()
```
{% endtab %}
{% endtabs %}

### <mark style="color:purple;">Start saving session</mark>

Based on the settings we have applied, some files related to video , Analysis , gps and Imu are saved.

To start saving files using MyTestSDK , use the following code:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
gizoAnalysis.startSavingSession() 
```
{% endtab %}
{% endtabs %}

### <mark style="color:purple;">Stop saving session</mark>

To stop saving files using MyTestSDK , use the following code:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
gizoAnalysis.stopSavingSession()
```
{% endtab %}
{% endtabs %}

### <mark style="color:purple;">Attach preview to camera</mark>

Preview View is a Custom View that displays the camera feed for CameraX's Preview use case. This class manages the preview Surface's lifecycle. It internally uses either a TextureView or SurfaceView to display the camera feed, and applies required transformations on them to correctly display the preview, this involves correcting their aspect ratio, scale and rotation.

So, to display camera a previewView should be attached as well.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.attachPreview(previewView)
```
{% endtab %}
{% endtabs %}

###

### Video Recording Options in MyTestSDK

### <mark style="color:purple;">Lock and Unlock Preview</mark>

Lock preview attaches the preview screen , while unlock preview detaches it .They are used to give developers the ability to display preview or not.

To lock the preview using MyTestSDK , follow this line of code:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
gizoAnalysis.lockPreview()
```
{% endtab %}
{% endtabs %}

To unlock the preview using MyTestSDK , follow this line of code:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
gizoAnalysis.unlockPreview(previewView)
```
{% endtab %}
{% endtabs %}
