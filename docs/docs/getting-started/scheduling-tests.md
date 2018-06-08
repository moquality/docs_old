

# Scheduling Tests

Writing test cases is hard. Using MoQuality test recorder, it is a matter of few clicks to record a test case. In the background, AI understands the test case and ensures it is playable across multiple devices and is adaptible to future app versions and os updates.


*** Features: ***

1. Perform any action that you will in your app
2. Assertions which checks for text or widgets
3. Convert demonstrations to tests and run it on any device on our cloud. 


Before a user is able to schedule tests runs on devices, he has to create test cases uses  MoQuality Recorder, select devices to run on, create various test suite. 

1.  *** Upload an app ***
Upload an app at (http://app.moquality.com)

2. *** Create test cases using Recorder  *** 
To create test cases, go the Tests tab and click on + in the Tests module to add a test. You can download the recorder for your machine. Login to the recorder and record a test. Read more about recording test cases here.

3. *** Create test suites: ***
Go to the Tests tab and click on + in the Test Suites module to create test suites. You can select a number of tests that will run in order when we execute them.

4. *** Create device group : ***
Go to the Devices tab. You can now select a custom device group or create your own. 

5. *** Create a test report  ***
Go to the Overview page and create a test report by clicking on + in the Test Reports module. Select one test suite and a device group to schedule runs for this test report.

6. *** Reporting and executing tests *** 
Visit the guide.

*** Note: ***
The test cases you create adapt to every version of the app you upload. So the test, test suites, and device groups you create show up for every new version. Only the overview page keeps changing because the test report runs on a particular version.



We now  describe the setup to create device groups, suites, etc. now


## Pre-requisites for Tests scheduling


### Upload an app 
Visit upload app documentation

### Record Tests with MoQuality Recorder
Visit recorder documentation.

### View recorded test cases

Naviagate to Tests page. This page provides an overview of all the tests that have been recorded with the MoQuality Recorder. A test consist of a series of actions performed on an app on a device. It is displayed as a series of screenshot and a heilighted area indiciating the action widget.

<img src="../dashboard-img/4.png" height="480px" />



### Test Suites  

A test is a series of action that should be performed to cover a use case or check an assertion. All our tests always start after clearing any cache related to the app.

A test suite is a series of tests that should be run in an order. A test report is a test of these test suites. A test is created using the MQRecorder. After creating a few tests, you can create test suites. 

*** Usecase ***
...


*** Creating a suite ***

Navigate to the Suite tab and click on the Create Test Suite.

<img src="../dashboard-img/11.png" height="480px" />

Now name the Test Suite and select the tests that are part of it. You can create multiple test suites this way. 

<img src="../dashboard-img/12.png" height="480px" />





 
# Create Devices  group
We rent devices from various test infrastructure providers. Today we support around 50 devices and we are continuously adding new devices into our system as and when our users need them.

A device group is a collection of devices on which you want to run tests on. A user can create a group of devices you want to run tests on. There are few presets available such as Google Devices, Samsung Devices, Popular Devices.

<img src=.."../dashboard-img/5.png" height="480px" />

In order to create a custom device group click the + button. Custom device groups are important in many situations. For example, a user may want to run the apps on devices that have the latest android version, or to confirm it works on old versions. Another example is to create a group of devices from a certain manufacturer, or a user wants to create a group of popular devices. An example is shown below to create a custom group

<img src="../dashboard-img/9.png" height="480px" />


# Settings (optional)
Here you can change the name of the app and version. You can also specify Package Name of the app and launchable activity name. If you are not sure, do not change these fields.

<img src="../dashboard-img/10.png" height="480px" />
























#Executing Tests and Viewing Test Reports

You can reach the Test Reports  from the Dashboard by clicking Overview. 

<img src="../dashboard-img/2.png" height="480px" />


There are two ways to execute tests and reports:

1. Executing exisiting tests that have been recorded by MoQuality Recorder.

2. Automatically generating test using MoQuality AI-bot.

### Executing existing tests


Tests recorded by the recorder can be replayed and tested on other devices.
Click on Run Tests, then the following window would pop-up. Enter the name of the report, 
select a device group, and select tests/suites you want to run on other devices.

<img src="../dashboard-img/7.png" height="480px" />

#### Use Case:
1. Using the Moquality recorder, you have recorded a login test on Nexus 6p that checks whether login functionality works on Nexus 6p or not. Now you want to test
it on a Samsung Galaxy S8. All you have to do is schedule a test run on Samsung Galaxy S8.

2. Ensuring that a new version of your app has all the  existing tests  running smoothly.

3. Ensuring that a your app has all the  existing tests  running smoothly
on a new version of android/iOS.

Click on Run Tests, then the following window would pop-up. Enter the name of the report, 
select a device group, and select tests/suites you want to run on other devices.

<img src="../dashboard-img/7.png" height="480px" />