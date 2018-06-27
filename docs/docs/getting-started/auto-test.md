
# Auto-generating Tests

This feature allows MQ-Bot (our AI Agent) to create tests automatically and executing them on devices users specify.
The MQ-Bot tries to systematically identify widgets on every screen and interacts with them. In the end, it gives you a list of test runs it has conducted and a pass or success for each of them, along with screenshots, AppMap, and various statistics. To view results and reports of the test runs, visit  [Dashboard](getting-started/view-results).

## Use Case

In contrast to demonstrating a test and running them, robot test can be used for quick feedback and check cases that you might otherwise miss out.The more you use this feature on your app, the smarter it gets. For example, if the robot finds a bug, it prioritizes testing towards creating test runs to produce  that bug. For enterprise customers, the robot learns the context of your app and creates test runs like a human would.


 In order to automatically generate tests, click on Generate Tests.
Now specify the name of the report, number of tests you want to generate and the maximum
amount of time MQ-Bot ,should run. For example, if you specify 10 tests to be generated in an hour, than the MQ-Bot will generate approximately 10 tests in an hour. If you specify
30 min instead of an hour, it will still generate the same number of tests, but the
tests will be shorter.

<img src="../dashboard-img/8.png" height="360px" />

## Training MQ-Bot
Our MQ-Bot can be trained!! By recording with [MoQuality Recorder](getting-started/view-results), we can train the MQ-Bot to know the important
test flows and screens. It makes the MQ-Bot bias itself towards such flows and screen when creating tests.18 

## Viewing results

To view results and reports of the test runs, visit  [Dashboard](view-results)