# Executing Tests and viewing Test Reports

You can reach the Test Reports  from the Dashboard by clicking Overview. 

<img src="/dashboard/2.png" height="360px" />


There are two types of reports that are generated.

### Executing existing tests


Tests recorded by the recorder can be replayed and tested on other devices.
Click on Run Tests, then the following window would pop-up. Enter the name of the report, 
select a device group, and select tests/suites you want to run on other devices.

<img src="/dashboard/7.png" height="360px" />

#### Use Case:
1. Using the Moquality recorder, you have recorded a login test on Nexus 6p that checks whether login functionality works on Nexus 6p or not. Now you want to test
it on Samsung Galaxy S8. All you have to do schedule a test run on Samsung Galaxy S8.

2. Imagine that you have a new version of your app and you want to confirm if existing tests are running smoothly on the new version.

3. There is a new version of Android, and you want to confirm if existing tests are compatible with the new android version.

Click on Run Tests, then the following window would pop-up. Enter the name of the report, 
select a device group, and select tests/suites you want to run on other devices.

<img src="/dashboard/7.png" height="360px" />


### Auto-generated Test

This feature allows MQ-Bot (our AI Agent) to create tests automatically and executing them on devices a user specify.
The MQ-Bot tries to systematically identify widgets on every screen and interacts with them. In the end, it gives you a list of test runs it conducted and a pass or success for each of them.

#### Use Case:

In contrast to demonstrating a test and running them, robot test can be used for quick feedback and check cases that you might otherwise miss out.The more you use this feature on your app, the smarter it gets. For example, if the robot finds a bug it prioritizes testing towards creating test runs near the bug. For enterprise customers, the robot learns the context of your app and creates test runs like a human would.


 In order to automatically generate tests, click on Generate Tests.
Now specify the name of the report, number of tests you want to generate and the maximum
amount of time MQ-Bot ,should run. For example, if you specify 10 tests to be generated in an hour, than the MQ-Bot will generate approximately 10 tests in an hour. If you specify
30 min instead of an hour, it will still generate the same number of tests, but the
tests will be shorter.

<img src="/dashboard/8.png" height="360px" />


## Viewing Test Reports


Each row represents the Test Report created, it's status, suites it ran on, device groups, and the various actions. The status is either a tick singalling that no bugs found, red ballon showing that there are bugs, orange ballon indicating warnings or potential risks or an hour glass indicating that the tests yet to be executed.

There are currently two actions available now:

### View Report

 It shows the test runs of all the tests in the report across all the selected devices. The report provides the details af tests as well such as if the test was successfull along with any bugs. By clicking the view report button you get the details of the test runs.

<img src="/dashboard/13.png" height="360px" />

By clicking on the individual test, you can see the screenshots of a test.

<img src="/dashboard/14.png" height="360px" />




### View map

 It present a snapshot of the whole app itself. It shows how all the screens are connected with each other and therefore 
 ...

<img src="/dashboard/15.png" height="360px" />


