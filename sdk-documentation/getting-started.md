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

* Install the latest version of the Android Studio.
* Install Mapbox SDK for Android and get access token

Before you begin using MyTestSDK, make sure you have the following prerequisites installed and set up in your development environment:



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

