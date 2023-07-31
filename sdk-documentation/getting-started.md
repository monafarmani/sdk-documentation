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

# 🚀 Getting Started

## Requirements

* Install the latest version of Android studio.
* Install [mapbox ](https://docs.mapbox.com/android/maps/guides/install/)SDK for Android and get access token.

## To use My Test library, follow these steps:

1. Open your Android project in Android Studio.
2. Add the following lines to settings.gradle:

{% tabs %}
{% tab title="Groovy" %}
```kotlin
allprojects {
	repositories {
		maven { url 'https://jitpack.io' }
	}
}	
```
{% endtab %}

{% tab title="Kts" %}
```kotlin
repositories {
        maven ("https://jitpack.io")
}
```
{% endtab %}
{% endtabs %}

3. Add the following lines to your app-level `build.gradle` file:

{% tabs %}
{% tab title="Groovy" %}
```kotlin
dependencies {
    implementation 'com.github.monafarmani:new:0.0.12'
}
```
{% endtab %}

{% tab title="Kts" %}
```kotlin
dependencies {
    implementation ("com.github.monafarmani:new:0.0.12")
}
```
{% endtab %}
{% endtabs %}

4. We need to implement settings for map box because it is used in our library, so add the following lines to settings.gradle too:

{% tabs %}
{% tab title="Groovy" %}
```kotlin
allprojects {
    repositories {
      maven {
            url 'https://api.mapbox.com/downloads/v2/releases/maven'
            authentication {
                basic(BasicAuthentication)
            }
            credentials {
                username = "mapbox"
                password = "MAPBOX_SECRET_KEY"
            }
        }
    }
}
```
{% endtab %}

{% tab title="Kts" %}
```kotlin
repositories {
    maven {
        url = uri("https://api.mapbox.com/downloads/v2/releases/maven")
        authentication {
            create<BasicAuthentication>("basic")
        }
        credentials {
            username = "mapbox"
            password = "MAPBOX_SECRET_KEY"
        }
    }
}
```
{% endtab %}
{% endtabs %}

5. Sync your project with Gradle.

## Using the SDK in your Android Application

### &#x20;<mark style="color:purple;">Initialize the SDK</mark>

To initialize the SDK, you will need to create a new instance of the Application class in your app's module:

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
class Application : Application() {

    override fun onCreate() {
        super.onCreate()

        Gizo.initialize(
            this,
            GizoApp.GizoAppOptions.Builder().build()
        )
    }
}
```
{% endtab %}
{% endtabs %}

In the example above, we create a new instance of the Application class and call the initialize method to initialize the sdk.

{% tabs %}
{% tab title="Kotlin" %}
```kotlin
<application
    android:name=".Application"
>
```
{% endtab %}
{% endtabs %}

In the examole above, we add some lines of code to AndroidManifest.xml as well.

**Note:** For using features of the sdk you need to add [Model ](broken-reference)and required [App Options Setting](broken-reference) in the following steps.

