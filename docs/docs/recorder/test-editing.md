# Test Editing in the Recorder

## Introduction

Using the recorder to record test cases is one of the fastest, and most efficient ways to test your app. However, there may be times when you would like to tweak your individual test steps for more control, test editing allows you to do that!


## Opening the Edit Menu 

The *Edit Menu* can be accessed by hovering over the selected *Test Step*, and clicking the *Edit Button*.

<img src="../android/edit_button.png" style="max-width:600px;max-height:480px" />

## Editing Step Description

If you would like to change the description of a test step, it's as easy as replacing the content inside the *Description* tab and pressing *Submit*

<img src="../android/edit_test_description.png" style="max-width:600px;max-height:480px" />

## Editing Test Parameters (Coming Soon)

We are currently in the process of adding the ability to parameterize test inputs, such as usernames and passwords, to expand the testing capabilities of an individual test.

<img src="../android/edit_test_params.png" style="max-width:600px;max-height:480px" />

## Adding Sleep Actions (Wait)

*Sometimes* our AI will try to continue through a test, despite the device not being ready to receive the additional information. This can happen for several reasons, including changes in internet connection speed, or background apps hogging the phone's processing power. The simplest way to tell the app to wait, is to add a sleep action immediately following a problematic action. 

<img src="../android/add_sleep_action.png" style="max-width:600px;max-height:480px" />


## Selecting a New Target (Beta)

*Occasionally*, our AI will be unable to detect the appropriate widget or it may select the incorrect widget. To correct this we have added the ability to select a new target within current screenshot. To select a new widget, hover over the screenshot until you see a red box surround the particular item you would like to designate as a target. 

<img src="../android/select_new_target.gif" style="max-width:600px;max-height:480px"/>





