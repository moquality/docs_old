# Recorder Setup for Android Devices

## Enable USB Debugging

1. Select a device you would like to test with and then **turn on USB Debugging**, which can be found inside of **Settings > Developer Options > USB Debugging** and connect your device to your computer. **Press 'Always Allow"** on the popup on the device.

    <img src="../android/usb_debugging.png" style="max-width:600px;max-height:480px" />

## Upload App

1. Make sure to have uploaded a version of your app to test on [app.moquality.com](https://app.moquality.com). We automatically will find the `package name` and `activity name` for the app. You can verify it under the Settings tab.

    <img src="../android/package_name.png" style="max-width:600px;max-height:480px" />

## Launch Recorder

1. Launch the recorder with your connected device and log in with either your *API key* or *username/password*. Select your device and app from the drop down, as well as your screen size and keyboard preference. We recommend setting it to no-keyboard, tests are more reliable without flaky keyboard. The recorder itself has a text input feature which will allow you to input text into text boxes.

    <img src="../android/login.gif" style="max-width:600px;max-height:480px" />

2. **Press Record** (on top left) to begin  recording your test on your device. Interact with the screen projection you see in front of you. You **MUST use the bottom interface buttons** for actions instead of the hardware buttons on your device. Hardware buttons include back button, home screen button and show apps button. Similarly, if your device has software buttons, do not click them. We assume that software buttoms will never be a part of a test case and discard them.

    <img src="../android/recording_demo.gif" style="max-width:600px;max-height:480px" />

3. When you are done recording a test, **press SAVE and name your test**. You can then view the test in the app.moquality.com website.

    <img src="../android/save_test.gif" style="max-width:600px;max-height:480px" />

## Replay Tests

1. To **confirm the test was valid, move to the Tests Tab and try to run the test**. If you are unable to run the test, you may have to re-record it, or head down to the FAQ to see possible solutions.

    <img src="../android/test_replay.gif" style="max-width:600px;max-height:480px" />

## FAQ

**Why does my phone not connect?**

Double-check that USB debugging is on and that you have clicked 'Allow' on the on-screen popup. You may have to unplug and replug the device in some cases.

**Why does it say I need to re-record in 'Stable Mode'?**

For some apps and tests, the regular mode may be unable to capture all the necessary details to successfully run the test. You can toggle 'Stable Mode' inside the recording by going into 'Settings' and toggling the option.
