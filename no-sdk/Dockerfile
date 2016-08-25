FROM java:8-jdk
MAINTAINER Diego Garcia <xaethos@gmail.com>

# This is a base Linux image with the external tools needed to build
# Android projects. It does NOT include the Android SDK.
#
# It is suitable when the SDK will be provided by other means, such as a
# mounted volume, or android-sdk-resource in Concourse.

# Need some 32 bit libs for aapt and adb
RUN dpkg --add-architecture i386 \
    && apt-get update && apt-get install -y --no-install-recommends \
        libstdc++6:i386 \
        zlib1g:i386 \
    && rm -rf /var/lib/apt/lists/*
