# Integrate with _fastlane_

## Introduction

_fastlane_ is a Continuous Integration and Continuous Delivery tool for iOS and Android apps. MoQuality integrates with _fastlane_ through the simple addition of a step to a lane.

## Prerequisites

* _fastlane_: If you have not yet installed _fastlane_, follow the instructions [here](https://docs.fastlane.tools/).
* MQ CLI: [Install the MQ CLI](mq-cli.md#installation).
* MoQuality app: If you intend to upload a new build of an app, ensure that you have already uploaded the first version through the [MoQuality website](https://app.moquality.com/).

## Example Code

MoQuality hosts a [GitHub repository](https://github.com/moquality/devcenter) that contains example code for all of our CI/CD integrations, including _fastlane_. You can take advantage of this repository by running the following command in the directory of your choosing.

``` shell
git clone https://github.com/moquality/devcenter.git
```

## Instructions

To integrate MoQuality with _fastlane_, you will add a step to your lane that runs a shell script containing your MQ CLI commands. For this documentation, we will call that script `mq.sh`, but you can call it whatever you wish.

### Set Environment Variables

There are two environment variables that you must set. The first variable is `API_KEY`, which will enable user login. To find your API key, run `mq login` in your command line to log in to MoQuality. Then, run `mq user` to display user information. Your API key will be in the list of returned information. The second variable is `APP_ID`. This will specify which app is being uploaded. To find your app Id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app Id in the same row. Run the below example commands in your command line to set these environment variables.

``` shell
export API_KEY=[OBTAINED_VALUE]
export APP_ID=[OBTAINED_VALUE]
```

### Create Shell Script

Create a shell script in the same directory as your `Fastfile` called `mq.sh`. Open that shell script in an editor.

This shell script will contain the MQ CLI commands that your new step will run. Before writing that step, we will write the shell script. The next section follows the creation of a shell script to upload an apk file built using Gradle, to MoQuality.

``` shell
#!/bin/sh

npm install -g mq-cli

mq login -a $API_KEY
mq user
mq upload -a $APP_ID -f $1
mq apps
```

* `npm install mq-cli` installs the MQ CLI. See the [MQ CLI documentation](mq-cli.md#Installation) for alternative installation commands.

* `mq login -a $API_KEY` logs you in using your API key.

* `mq user` returns user information, and you can check that your user is correct.

* `mq upload -a $APP_ID -f $1` will upload your app, whose location is provided by `$1`, the apk file's path that will be passed as an argument during execution. The command uses `$APP_ID` to determine which app is being uploaded.

* `mq apps` returns a list of your apps, and you can confirm that your app version has incremented by one.

### Edit `Fastfile`

Open your `Fastfile` in an editor. Find the lane to which you want to add the MoQuality step. If you build your app in this lane, make sure you add the new step after the app has been built. Below is an example lane before the step has been added.

``` Ruby
lane :beta do
  gradle(task: "clean assembleDebug")
end
```

### Add Shell Method to `Fastfile`

Add a shell method that runs your shell script to the lane. If you are following the example upload script, pass as an argument to the script the output variable from the Gradle step that provides the apk path. Below is the updated example lane.

``` Ruby
lane :beta do
  gradle(task: "clean assembleDebug")
  sh(“sh”,”mqtest.sh”,"#{lane_context[SharedValues::GRADLE_APK_OUTPUT_PATH]}")
end
```

### Run the Lane

Now that you have integrated MoQuality with _fastlane_, try running the lane with `fastlane [LANE_NAME]` in your command line.

## Troubleshooting

### Undocumented Error

If you encounter an error that is not documented, please open an issue on our [public GitHub repository](https://github.com/moquality/devcenter/issues). Alternatively, you can report your error to <hello@moquality.com>.