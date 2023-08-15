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

Welcome to MyTestSDK! This guide will help you get started with integrating and using our library in your Android projects.

## Introduction

MyTestSDK is a powerful and versatile library that provides a great analysis of the way people drive their cars. MyTestSDK allows precise control over driving, monitoring intelligence, and issuing warnings for risk of accidents…



## prerequisites

Before you begin using MyTestSDK, make sure you have the following prerequisites installed and set up in your development environment:

* Install the latest version of the Android Studio.
* Install Mapbox SDK for Android and get access token



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

The `settings.gradle` file in Android Studio is a configuration file used to define your project’s settings and modules. It is located in the root directory of your project, alongside the `build.gradle` file.

Some key aspects of the `settings.gradle` file include Project Structure, Module Inclusion, Module Names, and Multi-Module Projects.

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

In Android Studio, the `build.gradle` file is a configuration file that is used to define various settings and dependencies for your Android project. It is located in the root directory of your project and each module within the project.

4. We need to implement settings for Mapbox because we use it in our library, so add the following lines to settings.gradle too:

{% tabs %}
{% tab title="First Tab" %}
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

{% tab title="Second Tab" %}
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

Locate the toolbar at the top of the Android Studio window. There, you should see a series of icons, including a circular arrow icon labeled "Sync Project with Gradle Files."

* If the icon is highlighted and clickable, it means the project is not synchronized with the `build.gradle` files.
* If the icon is grayed out, it means the project is already synchronized.



## Using the SDK in your Android Application

### &#x20;<mark style="color:purple;">Initialize the SDK</mark>

To initialize the SDK, you will need to create a new instance of the Application class in your app's module:

In the example above, we create a new instance of the Application class and call the initialize method to initialize the SDK.

In the example above, we add some lines of code to AndroidManifest.xml as well.

In the AndroidManifest.xml file, the `<application>` element is used to define the characteristics and configurations of your Android application. The `android:name` attribute within the `<application>` element specifies the name of the class that represents the application itself.

**Note:** For using features of the SDK you need to add Model and required App Options Setting in the following steps.

