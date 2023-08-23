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

# GizoAnalysisSetting

## Overview

In our SDK, we require accurate and efficient detection and localization of objects in images and video streams and also accurate and efficient estimation of the depth or distance of objects in a scene.

Object detection and depth estimation are crucial technologies in Android development that empower applications to perceive and understand their surroundings. By leveraging these capabilities, developers can enable their apps to identify objects within images or video streams and estimate the relative distances between objects in a scene.

\
**Object detection** plays a vital role in various Android applications, enabling tasks such as object recognition, tracking, and augmented reality

**Depth estimation** enables Android applications to perceive the relative distances between objects in a scene. This capability is valuable for tasks like depth-based segmentation, virtual reality, or 3D reconstruction.

In Android Studio, object detection and depth estimation can be implemented using machine learning models, such as those built with TensorFlow, and deployed using the TensorFlow Lite library.&#x20;



### <mark style="color:purple;">Step 1: Adding model</mark>

The model should be added to the assets of the app module.

Download the model from this link:&#x20;



### <mark style="color:purple;">Step 2: Add Gizo Analysis Settings</mark>

Gizo Analysis setting is used to customize some behavior and functionality of our library including specifying the processing method on the model, the distance from the windshield to the hood of the car, the initial amount of timer, time to collision number (TTC), where to save the file, what period interval the data should be saved or sent, and where to save matrix file.

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
                
                 //add these lines
                .analysisSetting(GizoAnalysisSettings.Builder()
                    .allowAnalysis(true)
                    .modelName("arti_sense.data")
                    .loadDelegate(AnalysisDelegateType.Auto)
                    .collisionThreshold(0.5f)
                    .tailgatingThreshold(1.0f)
                    .saveTtcCsvFile(true)
                    .ttcFileLocation(FileLocationPath.CACHE)
                    .saveDataTimerPeriod(30L)
                    .saveDataTimerInitialDelay(0L)
                    .saveMatrixFile(true)
                    .matrixFileLocation(FileLocationPath.CACHE)
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

The `GizoAnalysisSettings` builder sets the analysis-related properties such as:

* <mark style="color:blue;">`allowAnalysis`</mark>`(true)`: Enabling the analysis feature.
* <mark style="color:blue;">`modelName`</mark>`("arti_sense.data")`: Providing the name of the model to be used for analysis.
* <mark style="color:blue;">`loadDelegate`</mark>`(AnalysisDelegateType.Auto)`: Specifying the analysis delegate type as "Auto", which determines the best delegate based on the device's capabilities.
* <mark style="color:blue;">`collisionThreshold`</mark>`(0.5f)`: Setting the collision threshold value for analysis.

**Note:** collisionThreshold parameter can be either Float or ThresholdType.None. If ThresholdType.None is chosen as the parameter, collision wouldn't be considered in the ttc status calculation.

* <mark style="color:blue;">`tailgatingThreshold`</mark>`(1.0f)`: Setting the tailgating threshold value for analysis.

**Note:** tailgatingThreshold parameter can be either Float or ThresholdType.None. If ThresholdType.None is chosen as the parameter, tailgating wouldn't be considered in the ttc status calculation.

* <mark style="color:blue;">`saveTtcCsvFile`</mark>`(true)`: Indicating that the TTC data should be saved to a file.
* <mark style="color:blue;">`ttcFileLocation`</mark>`(FileLocationPath.CACHE)`: Specifying the file location path for storing Time-to-Collision (TTC) data (in this case, set to the cache directory).
* <mark style="color:blue;">`saveDataTimerPeriod`</mark>`(30L)`: Setting the period of the TTC data timer to 30 milliseconds.
* <mark style="color:blue;">`saveDataTimerInitialDelay`</mark>`(0L)`: Setting the initial delay of the TTC data timer to 0 milliseconds (no delay).
* <mark style="color:blue;">`saveMatrixFile`</mark>`(true)`: Indicating that the analysis matrix file should be saved.
* <mark style="color:blue;">`matrixFileLocation`</mark>`(FileLocationPath.CACHE)`: Specifying the file location path for storing the Matrix of the camera (in this case, set to the cache directory).&#x20;

Finally, the `build()` method is called on the `GizoAppOptions.Builder()` instance to create a `GizoAppOptions` object with the configured analysis settings.



&#x20;Here are the available options that can be set in analysisSetting in the Application class:

<table><thead><tr><th width="240.33333333333331">Options</th><th width="207">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>allowAnalysis(Boolean)</td><td>false</td><td><p>To allow to use it or not.</p><p> </p></td></tr><tr><td>modelName(String)</td><td>""</td><td>A name that corresponds to this model's name.</td></tr><tr><td><p>loadDelegate</p><p>(AnalysisDelegateType)</p></td><td><p>AnalysisDelegateType</p><p>.Auto</p></td><td>To specify the processing method on the model e.g. CPU, GPU, NNAPI.</td></tr><tr><td><p>collisionThreshold</p><p>(Float or ThresholdType)</p></td><td>0.5f</td><td>The number that is used in the TTC calculations collision.</td></tr><tr><td><p>tailgatingThreshold</p><p>(Float or ThresholdType)</p></td><td>1.0f</td><td>The number that is used in the TTC calculations tailgating.</td></tr><tr><td>saveTtcCsvFile(Boolean)</td><td>false</td><td>Should the file of TTC be saved in CSV format or not.</td></tr><tr><td><p>ttcFileLocation</p><p>(FileLocationPath)</p></td><td><p>FileLocationPath</p><p>.CACHE</p></td><td>Where the file should be saved, in the cache or download.</td></tr><tr><td><p>ttcDataTimerPeriod</p><p>(Long)</p></td><td>30L</td><td>To specify in what period of time interval the data should be saved and sent.</td></tr><tr><td><p>ttcDataTimerInitialDelay</p><p>(Long)</p></td><td>0L</td><td>To specify the initial amount of timer.</td></tr><tr><td><p>saveMatrixFile</p><p>(Boolean)</p></td><td>false</td><td>Should it save the matrix file that is created based on the camera resolution or not?</td></tr><tr><td><p>matrixFileLocation</p><p>(FileLocationPath)</p></td><td><p>FileLocationPath</p><p>.CACHE</p></td><td>Where to save matrix file.</td></tr></tbody></table>

###

### <mark style="color:purple;">Step 3: Loading model</mark>

Loading a model in Android Studio allows the application to utilize the trained model's intelligence and perform complex tasks that go beyond traditional programming capabilities. By incorporating machine learning models into Android applications, developers can provide intelligent, data-driven features and functionalities to their users.

Add these lines of code in the Application class to load the model and receive the listener for different stats of loading, such as LOADING, LOADED, FAILED, NOT\_LOADED.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
class Application : Application() {
    override fun onCreate() {
        super.onCreate()

        Gizo.initialize(
            this,
            GizoApp.GizoAppOptions.Builder().build()
              .analysisSetting(GizoAnalysisSettings.Builder()
                    .allowAnalysis(true)
                    .modelName("arti_sense.data")
                    .loadDelegate(AnalysisDelegateType.Auto)
                    .collisionThreshold(0.5f)
                    .tailgatingThreshold(1.0f)
                    .saveTtcCsvFile(true)
                    .ttcFileLocation(FileLocationPath.CACHE)
                    .saveDataTimerPeriod(30L)
                    .saveDataTimerInitialDelay(0L)
                    .saveMatrixFile(true)
                    .matrixFileLocation(FileLocationPath.CACHE)
                    .build())
        )
        Gizo.app.setLoadModelObserver { status ->
            
        }

        Gizo.app.loadModel()
    }
}
```
{% endtab %}
{% endtabs %}

**Note:** After these settings are done, a series of callbacks are triggered so that the corresponding output can be observed.

**Note:** To enable GizoAnalysisSettings, it is essential to activate [GPS Setting](broken-reference).&#x20;
