---
title: Android Native Libraries Packaging
comments: true
# other options
---


In this post we will discuss my insights/observations on packaging native libraries in an Android apk.

According to Google developer blog it is better to package all the required native libraries as part of apk because of concept of namespaces introduced. This namespace will prevent user apps from accessing system libraries other than ***android ndk native libraries***.
This is introduced to reduce app crashes/incompatability/symbol conflicts with other libraries in different devices.

But there is a way to package dependent native libraries with [Adding additional native libraries](https://source.android.com/devices/tech/config/namespaces_libraries#adding-additional-native-libraries) which needs vendors to ship their own Android image. 

So, in a nutshell by default ***all ndk native libraries, libraries part of apk*** are accessible.

In next post, I will be discussing about ways I found to reduce shared library/Native Code size.

References:

[1] [Namespaces for Native Libraries](https://source.android.com/devices/tech/config/namespaces_libraries) <br>
[2] [Improving Stability with Private C/C++ Symbol Restrictions in Android N](https://android-developers.googleblog.com/2016/06/improving-stability-with-private-cc.html) <br>
