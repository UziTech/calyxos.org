---
title: Building CalyxOS's F-Droid fork
nav_title: Build F-Droid
---

CalyxOS includes [F-Droid](https://f-droid.org) by default. However, since it is an Android app built using the gradle build system, which the AOSP build system does not support, we build it separately and include a prebuilt APK for the OS build.

#### Preparation

{% highlight shell %}
cd ~/calyxos/android11-qpr1
cd external/fdroid/fdroidclient
git fetch --tags
export JAVA_OPTS="-Xmx2048m"
{% endhighlight %}

For development, you can simply put in a dummy value like the one above.

#### Build

{% highlight shell %}
./gradlew --no-daemon build
{% endhighlight %}

#### Copy

We use the full variant.

You can copy `app-full-release-unsigned.apk` to `prebuilts/calyx/fdroid/F-Droid.apk` for it to be included in the OS build.