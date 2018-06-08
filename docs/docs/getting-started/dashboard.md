# Dashboard
## Testing with MoQuality Flow

### Testing
In Robo testing, test cases are automatically generated and tested on a device. This article only discusses how you can test when you want to specify test cases.

Learn more about our concepts:

Tests and Test Suites
Devices and Device Groups
Test Reports
For testing specific test cases you will follow these steps:

1. Create test cases
To create test cases, go the Tests tab and click on + in the Tests module to add a test. You can download the recorder for your machine. Login to the recorder and record a test. Read more about recording test cases here.

2. Create test suites
Go to the Tests tab and click on + in the Test Suites module to create test suites. You can select a number of tests that will run in order when we execute them.

3. Create device groups
Go to the Devices tab. You can now select a custom device group or create your own. 

4. Create a test report
Go to the Overview page and create a test report by clicking on + in the Test Reports module. Select one test suite and a device group to schedule runs for this test report.

Note:
The test cases you create adapt to every version of the app you upload. So the test, test suites, and device groups you create show up for every new version. Only the overview page keeps changing because the test report runs on a particular version.


## Uploading an App
1. Login on the MoQuality URL (http://app.moquality.com) and click on the Add APP box.
<img src="/dashboard/1.png" height="360px" />

2. Upload the app by cliking the Click to select or Drop App file here box.
s<img rc="/dashboard/2.png" height="360px" />

3. Enter the App Name, description, and select the type of App (Android/iOS).

## Dashboard Overview

The overview tab provide the App and Test Reports details. Test Reports are described in detail in the Test Report Section. Here you can schedule the test runs recorded with Moquality recorder or Automatic Testing on a set of selected devices.

<img src="/dashboard/3.png" height="360px" />

# Tests 

Writing test cases is hard. So we built a recorder in which you demonstrate (not record) your test case.

*** Use Case:***

In contrast to a test recorder which uses user input to select the best selectors, we only need a demonstration of the test. In the background, our AI engine post processes this information and finds the best way to run the test on any device you select.

*** Features: ***

1. Perform any action that you will in your app
2. Assertions which checks for text or widgets
3. Convert demonstrations to tests and run it on any device on our cloud. 

*** Viewing recorded tests: ***

Naviagate to Tests tab. This tab provides an overview of all the tests that have been recorded with the MoQuality Recorder. A test consist of a series of actions performed on an app on a device. It is displayed as a series of screenshot and a heilighted area indiciating the action widget.

<img src="/dashboard/4.png" height="360px" />



# Suite Overview
A test is a series of action that should be performed to cover a use case or check an assertion. All our tests always start after clearing any cache related to the app.

A test suite is a series of tests that should be run in an order. A test report is a test of these test suites. A test is created using the MQRecorder. After creating a few tests, you can create test suites. 

*** Usecase ***
...


*** Creating a suite ***

Navigate to the Suite tab and click on the Create Test Suite.

<img src="/dashboard/11.png" height="360px" />

Now name the Test Suite and select the tests that are part of it. You can create multiple test suites this way. 

<img src="/dashboard/12.png" height="360px" />






# Devices 
We rent devices from various test infrastructure providers. Today we support around 50 devices and we are continuously adding new devices into our system as and when our users need them.

A device group is a collection of devices on which you want to run tests on. A user can create a group of devices you want to run tests on. There are few presets available such as Google Devices, Samsung Devices, Popular Devices.

<img src="/dashboard/5.png" height="360px" />

In order to create a custom device group click the + button. Custom device groups are important in many situations. For example, a user may want to run the apps on devices that have the latest android version, or to confirm it works on old versions. Another example is to create a group of devices from a certain manufacturer, or a user wants to create a group of popular devices. An example is shown below to create a custom group

<img src="/dashboard/9.png" height="360px" />


#Settings
Here you can change the name of the app and version. You can also specify Package Name of the app and launchable activity name. If you are not sure, do not change these fields.

<img src="/dashboard/10.png" height="360px" />





