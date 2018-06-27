# Building an iOS Simulator App

We test iOS simulator apps and native apps.

## iOS Simulator App

Although it is strongly recommended to test an app on real devices, some developers might want to quickly test their apps on a simulator. Below are the steps you can follow to build your iOS app to run on the iOS Simulator through XCode and the command-line.

## XCode Workflow

1. Select a iOS simulator target for the project inside XCode.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/5a71dda50428634376cfaba1/file-qcitH9H5eG.png">

2. Select the .app file under Products and choose to "Show in Finder" to get the file.

	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/5a71ded50428634376cfabb3/file-rpnM91aLEn.png">

	Alternately, you can also navigate to the output folder, which should be located at `~/Library/Developer/Xcode/DerivedData/<project>/Build/Products/<device>`

3. Compress the .app folder to create an archived zip file.
	<img src="https://s3.amazonaws.com/helpscout.net/docs/assets/597447a5042863033a1b4fa1/images/5a71e6da2c7d3a4a4198aaf8/file-vXBRsoCDIm.png">

	 You can now upload this zip file to MoQuality for recording tests.

## CLI Workflow
Go into the directory containing your XCode project and use xcodebuild to build the app.

```
xcodebuild -sdk iphonesimulator -configuration Debug
```
Then zip the .app bundle in `build/Debug-iphonesimulator`

```
zip -r UIKitCatalog.zip UIKitCatalog.app
```

You can now upload this zip file to MoQuality for recording tests.