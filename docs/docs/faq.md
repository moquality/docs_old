# Frequently Asked Questions

## Testing

### What types of apps can be tested with MoQuality?

MoQuality can be used to test native Android and iOS apps.

### What it the maximum number of apps we can test?

You can upload a total of 100 apps for each account. Note that two versions of the same app counts as two apps towards this total.

### Do I need to instrument my app or supply source code?

No instrumentation or source code is required to use the built-in tests. Android apps can be submitted as is. iOS apps should be built with “iOS Device” as the target. If they are built with a simulator as the target, select the simulator checkbox while uploading the app.

### How do you clean up devices after my testing is completed?

After test execution completes, we uninstall the app and any data related to the app (cache is deleted).

While we continue to add additional cleanup steps and improve the cleanup process, it is possible for data to persist between sessions. In case you want to test on a private device, contact us. In some cases you might have to provide sensitive information like login or other security-sensitive details during your automated test sessions. We advise you to create sandbox accounts to perform these tests on your staging environments.

### Do you modify my app?

No, we don't modify your app. Some iOS apps may require re-signing, but this feature is not currently supported. We recommend uploading a version of your app with debugging symbols enabled.

## Test Recording and Editing

### Does the recorder support both Android and iOS?

Yes, both Android and iOS, including iOS simulators, are supported.

### Do I need to additional software on my machine?

Android does not require any additional software. iOS requires Xcode to be installed and the command-line tools enabled. For details on how to setup a system for use with iOS, see [Recorder Setup for iOS Devices](../recorder/ios).


### Can I connect to multiple Android devices from my local machine?

Yes. The recorder allows you to choose which you would like to use after you have logged in.

### What is the maximum test time allowed?

The maximum time for each test is 5 minutes. If you need a longer timeout, please contact us.

### Is there a way to download the results?

We offer this feature as an extra package. After you enable it, a link appears in our dashboard that enables you to download tests and test reports in JSON format.

## Devices

### Are devices able to communicate with other services or systems that are available on the Internet?

Yes. All devices have internet access through a Wifi connection.

### Can I make phone calls or send SMS from the devices?

No, devices do not have carrier SIM setup and cannot make phone calls or send SMS messages. Please contact us via our support challels (see end) with your specific usecase.

### Can I use the device camera?

Yes, you can use the device cameras, both front and rear facing. Images might be dark or blurry.

### Android: Are there any default accounts (e.g., Google) available on cloud devices?

No, cloud devices should be clean and you cannot rely on any active accounts being present on them. 

We do however allow you to add webhooks in the tests recorded through the recorder, which can be used in conjuction with a server side script to partly facilitate co-ordination with account creation and use within tests. Please contact us via our support challels (see end) with your specific usecase.

### Android: Is Google Play Services available on cloud devices? Which version is installed?

Yes, Google Play Services is installed on devices that support it. The services are updated as new versions become available.

### I didn't find an answer for my question?
Please contact us at any of our following support channels:
- Intercom chat on our website 
- Slack chat at http://slack.moquality.com
- Email at support@moquality.com
