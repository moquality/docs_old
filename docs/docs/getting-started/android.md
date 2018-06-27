## Building an Android App

Enable your main activity to be called through an external program. You can do that by setting the following setting in your AndroidManifest file.

```
android:exported="true"
```

## Using Gradle

For Android projects that use the Gradle build system, building a debug APK requires running a command like:
```
./gradlew assembleDebug
```

The output APK is typically located at `[project]/app/build/outputs/apk/app-debug.apk`. You might need to replace "app" with your Android default module name.

## Using Eclipse/Ant

If your app uses the legacy ant build system, the command is usually
```
ant debug
```

Upload the debug apk to [app.moquality.com](https://app.moquality.com).