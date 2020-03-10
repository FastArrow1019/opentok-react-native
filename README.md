React Native library for OpenTok iOS and Android SDKs

Pre-Requisites
Installation
iOS Installation
Android Installation
API Reference
OTSession Component
OTPublisher Component
OTSubscriber Component
Event Data
Samples
Contributing
In this repo, you'll find the OpenTok React Native library:
Pre-Requisites:
Install node.js

Install and update Xcode (you will need a Mac)

React Native iOS installation instructions
Install and update Android Studio
React Native Android installation instructions
Installation:
In your terminal, change into your React Native project's directory

Add the library using npm or yarn.

npm install opentok-react-native
yarn add opentok-react-native
iOS Installation
Note: Please make sure to have CocoaPods on your computer. If you've installed this package before, you may need to edit your Podfile and project structure because the installation process has changed.

In you terminal, change into the ios directory of your React Native project.

Create a pod file by running: pod init.

For React Native < 0.60, add this to your Podfile:

    target '<YourProjectName>' do

      # Pods for <YourProject>
        pod 'OpenTok', '2.16.3'
    end

Now run, pod install

After installing the OpenTok iOS SDK, change into your root directory of your project.

For React Native < 0.60, now run react-native link opentok-react-native.

Open <YourProjectName>.xcworkspace contents in XCode. This file can be found in the ios folder of your React Native project.

Click File and New File

Add an empty swift file to your project:

You can name this file anything i.e: OTInstall.swift. This is done to set some flags in XCode so the Swift code can be used.
Click Create Bridging Header when you're prompted with the following modal: Would you like to configure an Objective-C bridging header?

Ensure you have enabled both camera and microphone usage by adding the following entries to your Info.plist file:

<key>NSCameraUsageDescription</key>
<string>Your message to user when the camera is accessed for the first time</string>
<key>NSMicrophoneUsageDescription</key>
<string>Your message to user when the microphone is accessed for the first time</string>
If you try to archive the app and it fails, please do the following:

Go to Target
Click on Build Phases
Under the Link Binary With Libraries section, remove the libOpenTokReactNative.a and add it again
Android Installation
In your terminal, change into your project directory.

If you have already run react-native link opentok-react-native for the iOS installation, please skip this step.

Run react-native link opentok-react-native
Open your Android project in Android Studio.

Add the following to your project build.gradle file:

        maven {
            url "http://tokbox.bintray.com/maven"
        }
Sync Gradle

Make sure the following in your app's gradle compileSdkVersion, buildToolsVersion, minSdkVersion, and targetSdkVersion are greater than or equal to versions specified in the OpenTok React Native library.

As for the older Android devices, ensure you add camera and audio permissions to your AndroidManifest.xml file:

    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-feature android:name="android.hardware.camera" android:required="true" />
    <uses-feature android:name="android.hardware.camera.autofocus" android:required="false" />
    <uses-feature android:name="android.hardware.microphone" android:required="true" />
Newer versions of Android–API Level 23 (Android 6.0)–have a different permissions model that is already handled by this library.
