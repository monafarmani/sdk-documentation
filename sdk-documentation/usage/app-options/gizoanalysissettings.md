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

# GizoAnalysisSettings

## overview

In our SDK, we require accurate and efficient detection and localization of objects in images and video streams and also  accurate and efficient estimation of the depth or distance of objects in a scene.

Object detection and depth estimation are crucial technologies in Android development that empower applications to perceive and understand their surroundings. By leveraging these capabilities, developers can enable their apps to identify objects within images or video streams and estimate the relative distances between objects in a scene.

\
**Object detection** plays a vital role in various Android applications, enabling tasks such as object recognition, tracking, and augmented reality

**Depth estimation** enables Android applications to perceive the relative distances between objects in a scene. This capability is valuable for tasks like depth-based segmentation, virtual reality, or 3D reconstruction.

In Android Studio, object detection and depth estimation can be implemented using machine learning models, such as those built with TensorFlow, and deployed using the TensorFlow Lite library.&#x20;



### <mark style="color:purple;">Step 1: Adding model</mark>

the model should be added in assets of the app module.

Download the model from this link:&#x20;



### <mark style="color:purple;">Step 2: Add Gizo Analysis Settings</mark>

Gizo Analysis setting is used to customize some behavior and functionality of our library including specifying the processing method on the model, the distance from the windshield to the hood of the car, the initial amount of timer, time to collision number (TTC), where to save the file, what period interval the data should be saved and sent & where to save matrix file.

To do this task, add these lines of code in the Application class to set the Gizo Analysis Settings:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
class Application : Application() {
    override fun onCreate() {
        super.onCreate()

        Gizo.initialize(
            this,
            GizoApp.GizoAppOptions.Builder()
                .debug(true)
                .folderName("GizoSample")
                .analysisSetting(GizoAnalysisSettings.Builder()
                
                //add these lines
                
                    .allow(true)
                    .modelName("arti_sense.tflite")
                    .loadDelegate(GizoAnalysisSettings.AnalysisDelegateType.Auto)
                    .carHeight(1.6)
                    .saveMatrixFile(true)
                    .saveTTcFile(true)
                    .build())
                    
                    //
                .imuSetting(GizoImuSetting.Builder().build())
                .gpsSetting(GizoGpsSetting.Builder().build())
                .videoSetting(GizoVideoSetting.Builder().build())
                .batterySetting(GizoBatterySetting.Builder().build())
                
                .build()
        )
    }
   }
```
{% endtab %}
{% endtabs %}



&#x20;Here are the available options that can be set in analysisSetting in  the Application class:

<table><thead><tr><th width="240.33333333333331">Options</th><th width="207">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>allow(Boolean)</td><td>false</td><td><p>To allow to use it or not.</p><p> </p></td></tr><tr><td>modelName(String)</td><td>""</td><td>A name that corresponds to this model's name.</td></tr><tr><td><p>loadDelegate</p><p>(AnalysisDelegateType)</p></td><td><p>AnalysisDelegateType</p><p>.Auto</p></td><td>To specify the processing method on the model e.g. CPU, GPU, NNAPI</td></tr><tr><td>carHeight(Double)</td><td>1.6</td><td>To specify the distance from the windshield to the hood of the car.</td></tr><tr><td>collisionThreshold(Float)</td><td>0.5f</td><td>The number that is used in the TTC calculations.</td></tr><tr><td>saveTTcFile(Boolean)</td><td>false</td><td>Should the file of TTC be saved in CSV format or not.</td></tr><tr><td><p>ttcFileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>Where the file should be saved, in the cache, or download.</td></tr><tr><td><p>ttcDataTimerPeriod</p><p>(Long)</p></td><td>30L</td><td>To specify in what period of time interval the data should be saved and sent.</td></tr><tr><td><p>ttcDataTimerInitialDelay</p><p>(Long)</p></td><td>0L</td><td>To specify the initial amount of timer </td></tr><tr><td><p>saveMatrixFile</p><p>(Boolean)</p></td><td>false</td><td>Should it save the matrix file that is created based on the camera resolution or not?</td></tr><tr><td><p>matrixFileLocation</p><p>(GizoFileLocationPath)</p></td><td><p>GizoFileLocationPath</p><p>.CACHE</p></td><td>Where to save matrix file.</td></tr></tbody></table>



### <mark style="color:purple;">Step 3: Loading model</mark>

Loading a model in Android Studio allows the application to utilize the trained model's intelligence and perform complex tasks that go beyond traditional programming capabilities. By incorporating machine learning models into Android applications, developers can provide intelligent, data-driven features and functionalities to their users.

Add these lines of code in Application class to load the model and receive the listener for different status of loading, such as LOADING, LOADED, FAILED, NOT\_LOADED

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
class Application : Application() {
    override fun onCreate() {
        super.onCreate()

        Gizo.initialize(
            this,
            GizoApp.GizoAppOptions.Builder().build()
            .analysisSetting(GizoAnalysisSettings.Builder(
                .allow(true)
                .modelName("arti_sense.tflite")
                .loadDelegate(GizoAnalysisSettings.AnalysisDelegateType.Auto)
                .carHeight(1.6)
                .saveMatrixFile(true)
                    .saveTTcFile(true)
                    .build())
        )
        Gizo.app.setLoadModelObserver { status ->
            Log.d("LoadModelStatus", "status:" + status.name)
        }

        Gizo.app.loadModel()
    }
}
```
{% endtab %}
{% endtabs %}

**Note:** After these settings are done, a series of callbacks are triggered so that the corresponding output can be observed.

**Note:** To enable GizoAnalysisSettings, it is essential to activate [GPS Setting](broken-reference).&#x20;
