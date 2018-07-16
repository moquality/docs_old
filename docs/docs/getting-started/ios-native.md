# Building an iOS Native App

This document gives you an overview of how you can upload your iOS app for real device testing through MoQuality. The steps below walk you through the process of exporting your app as an IPA file (iPhone Application).

1. In your build scheme, choose a "Generic Device", this allows you to Archive for multiple architectures and build without having the device plugged in.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59a9e309042863033a1c8a25/file-4ZAJu167B3.png" style="width: 368px;">

2. After this change, build your app for testing to ensure the binaries are in the right place.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/5a7392d40428634376cfbae7/file-3Zxqa1GouU.png" style="width: 238px;">
    
3. Build an *Archive* for your project by selecting *Product > Archive*.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/5a73920a2c7d3a4a4198b966/file-Vo1LZXeXW1.png" style="width: 187px;">
    
4. Navigate to the *Archives organizer* (Go to the Window > Organizer) to export the app IPA

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59a9e404042863033a1c8a2f/file-qs8QefyNiY.png" style="background-color: initial; width: 467px;">

5. On the method of distribution screen, select *Ad Hoc Distribution*.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59d4690c042863379ddc6199/file-cKWAZJ7gzb.png" style="width: 481px;">
    
6. Follow the later prompts to login to your Apple account, if necessary.

7. On the Ad hoc distribution screen, make sure to select *App Thinning* to **None**.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59d469af042863379ddc619f/file-rXHn3kqgtr.png" style="width: 470px;">
    
7. Select *Automatically manage *signing*,* unless you would like to manually create/select the provisioning profiles.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59d469c7042863379ddc61a0/file-Pw99iFEsvy.png" style="width: 472px;">
    
8. On the final screen, select Export and choose the path for the destination folder.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/59d46d202c7d3a40f0ed2b61/file-K4oVNyqbLY.png" style="width: 470px;">

9. In this folder you will find the IPA file that you need to upload to your MoQuality account for testing.
