

# Scheduling Tests

Writing test cases is hard. Using MoQuality test recorder, it is a matter of a few clicks to record a test case. In the background, AI understands the test case and ensures it is playable across multiple devices and is adaptable to future app versions and os updates.


## Features

1. Perform any action that you will in your app
2. Assertions which checks for text or widgets
3. Convert demonstrations to tests and run it on any device on our cloud. 

## Use Case
1. Using the MoQuality recorder, you have recorded a login test on Nexus 6p that checks whether login functionality works on Nexus 6p or not. Now you want to test
it on a Samsung Galaxy S8. All you have to do is schedule a test run on Samsung Galaxy S8.

2. Ensuring that a new version of your app has all the  existing tests  running smoothly.

3. Ensuring that a your app has all the  existing tests  running smoothly
on a new version of android/iOS.



Before a user is able to schedule tests runs on devices, he has to create test cases uses  MoQuality Recorder, select devices to run on, create various test suite. 

1. [Upload an app](getting-started/upload-app)
2. [Create test cases using Recorder](getting-started/recorder-link)
3. [View Recorded Tests](getting-started/view-tests)
4. [Create test suites](getting-started/test-suite)
5. [Create device group](getting-started/devices)

*** Note: ***
The test cases you create adapt to every version of the app you upload. So the test, test suites, and device groups you create show up for every new version. Only the overview page keeps changing because the test report runs on a particular version.


## Executing Tests 

You can reach the Test Reports  from the Dashboard by clicking Overview. 
<img src="../dashboard-img/3.png" height="480px" />

Click on Run Tests, then the following window would pop-up. Enter the name of the report, 
select a device group, and select tests/suites you want to run on other devices.

<img src="../dashboard-img/7.png" height="400px" />

## Viewing results

To view results and reports of the test runs, visit  [View Results](view-results)