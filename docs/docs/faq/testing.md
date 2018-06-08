# MoQuality

### What types of apps can be tested with MoQuality?
MoQuality can be used to test native Android and iOS apps.

### What it the maximum number of apps we can test?
You can upload a total of 100 apps for each account. When you upload a new version of your app, that counts as a new app.

### Do I need to instrument my app or supply source code?
No instrumentation or source code is required to use the built-in tests. Android apps can be submitted as is. iOS apps should be built with “iOS Device” as the target. If they are built with a simulator as the target, select the simulator checkbox while uploading the app.

### How do you clean up devices after my testing is completed?
After test execution completes, we uninstall the app and any data related to the app (cache is deleted).

While we continue to add additional cleanup steps and improve the cleanup process, it is possible for data to persist between sessions. In case you want to test on a private device, contact us. In some cases you might have to provide sensitive information like login or other security-sensitive details during your automated test sessions. We advise you to create sandbox accounts to perform these tests on your staging enviornments.

### Do you modify my app?
No, we don't modify your app. However some apps need resigning for testing. However we don't support this feature currently. we advise that you upload the app with debug symbols enabled.