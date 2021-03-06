#Connect SDK Android Lite
Connect SDK is an open source framework that connects your mobile apps with multiple TV platforms. Because most TV platforms support a variety of protocols, Connect SDK integrates and abstracts the discovery and connectivity between all supported protocols.

This repository contains the lite version of the Connect SDK project, and does not include support for platforms that require heavy and/or external dependencies. For the full Connect SDK, clone the [main repository](https://github.com/ConnectSDK/Connect-SDK-Android).

For more information, visit our [website](http://www.connectsdk.com/).

* [General information about Connect SDK](http://www.connectsdk.com/discover/)
* [Platform documentation & FAQs](http://www.connectsdk.com/docs/android/)
* [API documentation](http://www.connectsdk.com/apis/android/)

##Dependencies
This project has the following dependencies.
* [Java-WebSocket library](https://github.com/TooTallNate/Java-WebSocket)
* [Connect-SDK-Android-Core](https://github.com/ConnectSDK/Connect-SDK-Android-Core) submodule

##Including Connect SDK in your app with Android Studio
Edit your project's build.gradle to add this in the "dependencies" section
```groovy
dependencies {
    //...
    compile 'com.connectsdk:connect-sdk-android-lite:1.4.+'
}
```
##Including Connect SDK in your app with Android Studio from sources
1. Open your terminal and execute these commands
    - cd your_project_folder
    - git clone https://github.com/ConnectSDK/Connect-SDK-Android-Lite.git
    - cd Connect-SDK-Android
    - git submodule init
    - git submodule update

2. On the root of your project directory create/modify the settings.gradle file. It should contain something like the following:
    ```groovy
    include ':app', ':Connect-SDK-Android-Lite'
    ```

3. Edit your project's build.gradle to add this in the "dependencies" section:
    ```groovy
    dependencies {
        //...
        compile project(':Connect-SDK-Android-Lite')
    }
    ```

4. Sync project with gradle files
5. Add permissions to your manifest

##Including Connect SDK in your app with Eclipse


1. Clone Connect-SDK-Android-Lite project (or download & unzip)
2. Set up the submodules by running the following commands in Terminal from Connect-SDK-Android-Lite folder
   - `git submodule init`
   - `git submodule update`
2. Open Eclipse
3. Click `File > Import`
4. Select `Existing Android Code Into Workspace` and click `Next`
5. Browse to the Connect-SDK-Android-Lite project folder and click `Open`
6. Check all projects and click `Finish`
7. Right-click the `Connect-SDK-Android-Core` project and select `Properties`, in the `Library` pane of the `Android` tab 
   - add Connect-SDK-Android-Lite
8. **IN YOUR PROJECT** select `Properties`, in the `Library` pane of the `Android` tab 
   - add Connect-SDK-Android-Core
9. Set up your manifest file as per the instructions below

###Permissions to include in manifest
* Required for SSDP & Zeroconf discovery
 - `android.permission.INTERNET`
 - `android.permission.CHANGE_WIFI_MULTICAST_STATE`
* Required for interacting with devices
 - `android.permission.ACCESS_NETWORK_STATE`
 - `android.permission.ACCESS_WIFI_STATE`
* Required for storing device pairing information
 - `android.permission.WRITE_EXTERNAL_STORAGE`

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

###Proguard configuration
Add the following line to your proguard configuration file (otherwise `DiscoveryManager` won't be able to set any `DiscoveryProvider`).

```
-keep class com.connectsdk.**       { * ; }
```

##Contact
* Twitter [@ConnectSDK](https://www.twitter.com/ConnectSDK)
* Ask a question with the "tv" tag on [Stack Overflow](http://stackoverflow.com/tags/tv)
* General Inquiries info@connectsdk.com
* Developer Support support@connectsdk.com
* Partnerships partners@connectsdk.com

##Credits
Connect SDK for Android makes use of the following open-source projects.

* [Java-WebSocket](https://github.com/TooTallNate/Java-WebSocket) (MIT)
* [JmDNS](http://jmdns.sourceforge.net) (Apache License, Version 2.0)
* [Android-DLNA](https://code.google.com/p/android-dlna/) (Apache License, Version 2.0)

##License
Copyright (c) 2013-2014 LG Electronics.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

> http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
