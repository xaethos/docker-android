FROM xaethos/android-build:no-sdk
MAINTAINER Diego Garcia <xaethos@gmail.com>

# This is a base Linux image with the external tools needed to build
# Android projects. It includes the Android SDK with platform tools
# and bundled Maven repositories.

# Environment variables
ENV TERM=dumb \
    GRADLE_USER_HOME=/var/cache/gradle \
    ANDROID_HOME=/usr/local/android-sdk-linux \
    PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools

# Install Android SDK
#
RUN curl -L http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz \
| tar --no-same-owner -xzC /usr/local/; \
echo y \
| $ANDROID_HOME/tools/android update sdk --force --all --no-ui --filter \
platform-tools,\
tools,\
extra-android-m2repository,\
extra-google-m2repository

# Dockers union FS interacts very badly with the Java in the `android`
# command, deleting the content of tools/ during the update, because it
# is on a lower layer.
#
# If you are using this image, and want to install more compoenents,
# moving the tools directory forces it to be copied up to the writable
# layer, after which updating tools works fine.
#
#RUN mv $ANDROID_HOME/tools $ANDROID_HOME/foo; \
#    mv $ANDROID_HOME/foo $ANDROID_HOME/tools; \
#echo y | $ANDROID_HOME/tools/android update sdk --force --all --no-ui --filter \
#tools,\
#platform-tools,\
#android-23

