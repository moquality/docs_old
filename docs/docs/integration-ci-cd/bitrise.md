# Integrate with Bitrise

## Introduction

Bitrise is a Continuous Integration and Delivery Platform as a Service. MoQuality integrates with the workflows of Bitrise by adding a step to a workflow. The following instructions outline how to integrate MoQuality with your Bitrise workflow.

## Prerequisites

* Bitrise: If you have not yet installed Bitrise, follow the instructions [here](https://www.bitrise.io/cli).
* MQ CLI: [Install MQ CLI](mq-cli.md#installation).
* MoQuality app: If you intend to upload a new build of an app, ensure that you have already uploaded the first version through the [MoQuality website](https://app.moquality.com/).

## Instructions

### Export Several Variables

Integrating MoQuality with Bitrise requires that you export several environment variables. The first variable is `API_KEY`, which will enable user login. To find your API key, run `mq login` in your command line to log in to MoQuality. Then, run `mq user` to display user information. Your API key will be in the list of returned information. The next variable is `APP_ID`. This will specify which app is being uploaded. To find your app Id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app Id in the same row. The third variable is `APK_PATH`, the path to your folder for apk's. Navigate through your file explorer to find this path. See the below command line commands as an example of setting these variables for a Calculator app.

``` bash
export API_KEY=[OBTAINED_VALUE]
export APP_ID=[OBTAINED_VALUE]
export APK_PATH=/Users/[USERNAME]/Calculator/app/build/outputs/apk/
```

### Open `bitrise.yml`

Ensure `bitrise.yml` is in your main directory, and open the file in an editor.

### Set File Paths

In bitrise.yml, there should be environment variables `GRADLE_BUILD_FILE_PATH` and `GRADLEW_PATH`. These are the paths to your build.gradle and gradlew files, respectively. You can find these paths using your file explorer. When you know the paths, enter them in bitrise.yml for their respective variables. The below code is an example of how your variables might look.

``` YAML
app:
  envs:
  - GRADLE_BUILD_FILE_PATH: /Users/[USERNAME]/Calculator/build.gradle
  - GRADLEW_PATH: /Users/[USERNAME]/Calculator/gradlew
```

### Remove Two Steps

There are two default workflows in bitrise.yml: deploy and primary. To begin adding a step integrating MoQuality with either of these workflows, remove the last two steps, `deploy-to-bitrise-io@1.3.10` and `cache-push@2.0.5`.

### Add MQ CLI Installation Step

In place of those steps, add:

``` YAML
- script@1.1.5:
    title: Install MQ CLI and Upload App to MoQuality
    inputs:
    - content: |
```

### Fill New Step

The lines following `content` are shell commands. You may create a shell script to run MoQuality commands and run that script in Bitrise by adding `sh [script name].sh` beneath `- content: |`, or you can add the MoQuality commands beneath `- content: |` without a shell script. The following sub-intructions exlain how to install the MQCLI and upload a new build of an app. Again, these commands can either be run through a shell script or placed directly into bitrise.yml. Below are the commands to upload an app to MoQuality:

``` bash
    npm install -g mq-cli

    mq login -a $API_KEY
    mq user
    mq upload -a $APP_ID -f $APK_PATH/app-debug.apk
    mq apps
```

* `npm install mq-cli` installs the MQ CLI. See the [MQ CLI documentation](mq-cli/#Installation) for alternative installation commands.

* `mq login -a $API_KEY` will log you in using your API key.

* `mq user` returns user information, and you can check that your user is correct.

* `mq upload -a $APP_ID -f $APK_PATH/app-debug.apk` will upload your app, whose location is provided by `$APK_PATH`, and the command uses `$APP_ID` to determine which app is being uploaded.

* `mq apps` returns a list of the users apps, and you can confirm that your app version has incremented by one.

### Completed Step Examples

Your new step, integrating MoQuality with Bitrise, should be formatted like one of the two examples below.

``` YAML
- script@1.1.5:
    title: Install MQ CLI and Upload App to MoQuality
    inputs:
    - content: |
        npm install mq-cli
        mq login -a $API_KEY
        mq user
        mq upload -a $APP_ID -f $APK_PATH/app-debug.apk
        mq apps

- script@1.1.5:
    title: Install MQ CLI and Upload App to MoQuality
    inputs:
    - content: |
        sh [SCRIPT_NAME].sh
```

### Run Workflow

In your command line, run `bitrise run [WORKFLOW]`.

## Troubleshooting

### Permission denied when installing MQ CLI

Run `sudo chown -R [USERNAME] /usr/local/lib/node_modules` in your terminal. This will give you permission to write to the node_modules directory.

### Gradle-runner step fails for task ':app:mergeDebugResources'

Don't worry about this error. Run the workflow again, and it should work.
