# Getting Started with the Recorder

The MoQuality test recorder allows a developer to record test cases for their mobile apps.

## Downloading the Recorder

* [Windows](https://storage.googleapis.com/moquality/releases/prod-recorder/latest/recorder-win32-x64.zip)
* [Mac OS X](https://storage.googleapis.com/moquality/releases/prod-recorder/latest/recorder-darwin-x64.tar.gz)
* Linux (Coming Soon)

## Setup

Setup differs rather significantly between Android and iOS. Please consult the relevant page for the device you wish to record test cases with.

* [Recorder Setup for Android Devices](android)
* [Recorder Setup for iOS Devices](ios)

## Recording a Test Case

TODO.

## Replaying a Test

TODO.

## Troubleshooting

### Infinite Loading Screen

In some cases, the recorder may fail to start properly when connecting to a device. If this occurs, you will be presented with an error message, following which the loading screen will continue to load infinitely. This usually happens as a result of a desynchronization between the device and ADB, the Android Debug Bridge, resulting in ADB classifying the device as "offline". If this happens, try the following steps:

1. Close the recorder.
2. Unplug the device.
3. Disable USB debugging in the devices settings.
4. Re-enable USB debugging.
5. Plug the device back in.
6. Start the recorder again.

If the problem persists, please contact MoQuality for further support.

## Appendix: Differences between Android and iOS

For the most part, Android and iOS devices behave similarly in the recorder, but there are a few differences. Some of these are obvious, as they pertain to unique features that one device type or the other has, such as the back button, which doesn't exist on iOS.

A larger, less obvious difference is that of touch control. On Android, the mouse emulates a touch input, providing a clean 1-to-1 interaction between the recorder and the app. Unfortunately, due to limitations in iOS automation, the recorder is unable to do this 1-to-1 interaction with iOS devices.

When clicking on the screen while using an iOS device, a circle will appear where the mouse button was pressed. If the mouse is dragged past a threshold distance away from that starting point, a second circle will appear under the mouse with a line connecting the two. If this appears, releasing the mouse will perform a drag from the first circle to the second; if it has not appeared, a click will be performed at the location of the circle instead.
