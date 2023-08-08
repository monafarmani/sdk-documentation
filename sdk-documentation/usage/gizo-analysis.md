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

# Start The Camera

To start using the SDK we need to start the camera, for this reason we need a lifecycle like an activity or a fragment and implementation of these lines of code in the Activity: first we start the camera, second preview is attached.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
 Gizo.app.gizoAnalysis.startCamera(lifecycleOwner = this, onDone = {})
```
{% endtab %}
{% endtabs %}

**onDone is called when start camera is completed.**

Preview View is a Custom View that displays the camera feed for CameraX's Preview use case. This class manages the preview Surface's lifecycle. It internally uses either a TextureView or SurfaceView to display the camera feed, and applies required transformations on them to correctly display the preview, this involves correcting their aspect ratio, scale and rotation.

So, to display camera a previewView should be attached as well.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
Gizo.app.gizoAnalysis.attachPreview(previewView)
```
{% endtab %}
{% endtabs %}

## Video Recording Options in MyTestSDK

### <mark style="color:purple;">Overview</mark>

The video recording options in MyTestSDK allow developers to easily integrate video recording capabilities into their Android applications. This documentation provides instructions on how to utilize the start and stop recording functionality,  start and stop the camera, as well as lock and unlock the preview.

### <mark style="color:purple;">Start and Stop Recording</mark>

To start and stop video recording using MyTestSDK , use the following code:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
// Start video recording
coroutineScope.launch {
    gizoAnalysis.startRecording { event ->
        when (event) {
            is VideoRecordEvent.Finalize -> {
                if (event.hasError()) {
                    //Do something
             }
          }
       }
     }
 }
 
 // Stop video recording
 gizoAnalysis.stopRecording()
```
{% endtab %}
{% endtabs %}

### <mark style="color:purple;">Lock and Unlock Preview</mark>

Lock preview attaches the preview screen , while unlock preview detaches it .They are used to give developers the ability to display preview or not.

To lock and unlock the preview using MyTestSDK , add these lines:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
// lock preview
gizoAnalysis.lockPreview()

// unlock preview
gizoAnalysis.unlockPreview(previewView)
```
{% endtab %}
{% endtabs %}

### <mark style="color:purple;">Stop camera</mark>

Stop Camera is called when an activity is about to be destroyed or removed from memory.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
override fun onDestroy() {
    super.onDestroy()
    gizoAnalysis.stopCamera()
}
```
{% endtab %}
{% endtabs %}
