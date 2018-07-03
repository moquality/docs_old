# Frequently Asked Questions

## **Testing**

### What types of apps can be tested with MoQuality?

MoQuality can be used to test native Android and iOS apps.

### What is the maximum number of apps we can test?

You can upload a total of 100 apps for each account. Note that two versions of the same app count as two apps towards this total.

### Do I need to instrument my app or supply source code?

No instrumentation or source code is required to use the built-in tests. Android apps can be submitted as .apk files. iOS apps should be built with “iOS Device” as the target. If they are built with a simulator as the target, select the simulator checkbox while uploading the app.

### How do you clean up devices after my testing is completed?

After test execution completes, we uninstall the app and any data related to the app (cache is deleted).

While we continue to add additional cleanup steps and improve the cleanup process, it is possible for data to persist between sessions. In case you want to test on a private device, contact us. In some cases you might have to provide sensitive information like login or other security-sensitive details during your automated test sessions. We advise you to create sandbox accounts to perform these tests on your staging environments.

### Do you modify my app?

No, we don't modify your app. Some iOS apps may require re-signing, but this feature is not currently supported. We recommend uploading a version of your app with debugging symbols enabled.

## **Test Recording and Editing**

### Does the recorder support both Android and iOS?

Yes, both Android and iOS, including iOS simulators, are supported.

### Do I need any additional software on my machine?

Android does not require any additional software. iOS requires Xcode to be installed and the command-line tools enabled. For details on how to setup a system for use with iOS, see [Recorder Setup for iOS Devices](../recorder/ios).


### Can I connect to multiple Android devices from my local machine?

Yes. The recorder allows you to choose which device you would like to use after you have logged in.

### What is the maximum test time allowed?

The maximum time for each test is 5 minutes. If you need a longer timeout, please contact us at [support@moquality.com](mailto:support@moquality.com)

### Is there a way to download the results?

We offer this feature as an add-on. After you enable it, a link appears in our dashboard that enables you to download tests and test reports in JSON format.

## Devices

### Can the cloud devices communicate with external web-services?

Yes. All devices have internet access through a Wifi connection.

### Can I make phone calls or send SMS from the test devices?

No, currently our cloud devices do not have carrier SIM setup and cannot make phone calls or send SMS messages. 

### Can I access the cloud device camera?

Yes, you can access both front and rear facing device cameras.

### Android: Are there any default accounts (e.g., Google) available on cloud devices?

No. By default, every device is clean and there is no account data setup.  

However, the test recorder provides the functionality to add webhooks which allows it to communicate with server-side scripts that you may use for account setup. 


### Android: Is Google Play Services available on cloud devices? Which version is installed?

Yes, Google Play Services is installed on devices that support it. The services are updated as new versions become available.

### I didn't find an answer for my question?
Please contact us at any of our following support channels:

- Intercom chat on our website.
- Slack with us at [slack.moquality.com](http://slack.moquality.com).
- Email at [support@moquality.com](mailto:support@moquality.com).
