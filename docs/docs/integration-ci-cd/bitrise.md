# Integrating with Bitrise

## Getting Started

Bitrise is a Continuous Integration and Delivery Platform as a Service. MoQuality integrates with the workflows of Bitrise by adding a step to a workflow. The following instructions outline how to integrate MoQuality with your Bitrise workflow.

## Prerequisites

* Bitrise: If you have not yet installed Bitrise, follow the instructions [here](https://www.bitrise.io/cli).
* mq-cli: To install mq-cli, run `npm install -g mq-cli` in your terminal.
* MoQuality app: If you intend to upload a new build of an app, ensure that you have already uploaded the first version through the [MoQuality website](https://app.moquality.com/).

## Instructions

1. In your command line, navigate to your desired directory, and **clone your git repository**.

    ```
    git clone {git repository}
    ```

2. Integrating MoQuality with Bitrise requires **several variables that you must export**. The first variable is **`API_KEY`**, which will enable user login. To find your API key, run `mq login` to log in to MoQuality. Then, run `mq user` to display user information. Your API key will be in the list of returned information. The next variable is **`APP_ID`**. This will specify which app is being uploaded. To find your app id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app id in the same row. The third variable is **`APK_PATH`**, the path to your folder for apk's. Navigate through your file explorer to find this path. See the below code for an example of setting these variables with a Calculator app.

        export API_KEY={obtained value}
        export APP_ID={obtained value}
        export APK_PATH=/Users/{username}/Calculator/app/build/outputs/apk/

3. **Ensure bitrise.yml is in your current directory**, and **open the file** in an editor.

4. In bitrise.yml, there should be environment variables **`GRADLE_BUILD_FILE_PATH`** and **`GRADLEW_PATH`**. These are the paths to your build.gradle and gradlew files, respectively. You can find these paths using your file explorer. **When you know the paths, enter them in bitrise.yml for their respective variables.** The below code is an example of how your variables should look.


        app:
          envs:
          - GRADLE_BUILD_FILE_PATH: /Users/{username}/Calculator/build.gradle
          - GRADLEW_PATH: /Users/{username}/Calculator/gradlew

5. There are two default workflows in bitrise.yml: deploy and primary. **To begin adding a step** integrating MoQuality with either of these workflows, **remove the last two steps, `deploy-to-bitrise-io@1.3.10` and `cache-push@2.0.5`**. In place of those steps, **add**:

        - script@1.1.5:
            inputs:
            - content: |

6. The lines following `content` are shell commands. **You may create a shell script** to run MoQuality commands and run that script in Bitrise by adding `sh {script name}.sh` beneath `- content: |`, **or you can add the MoQuality commands** beneath `- content: |` without a shell script. The following **sub-intructions exlain how to upload a new build of an app**. Again, these commands can either be run through a shell script or placed directly into bitrise.yml.

    1. Below are the commands to upload an app to MoQuality:

            mq login -a $API_KEY
            mq user
            mq upload -a $APP_ID -f $APK_PATH/app-debug.apk
            mq apps
    
    2. `mq login -a $API_KEY` will log you in using your API key.

    3. `mq user` returns user information, and you can check that your user is correct.

    4. `mq upload -a $APP_ID -f $APK_PATH/app-debug.apk` will upload your app, whose location is provided by `$APK_PATH`, and the command uses `$APP_ID` to determine which app is being uploaded.

    5. `mq apps` returns a list of the users apps, and you can confirm that your app version has incremented by one.

7. Your **new step**, integrating MoQuality with Bitrise, should be **formatted like one of the two examples below**.

        - script@1.1.5:
            inputs:
            - content: |
                mq login -a $API_KEY
                mq user
                mq upload -a $APP_ID -f $APK_PATH/app-debug.apk
                mq apps

        - script@1.1.5:
            inputs:
            - content: |
                sh {script name}.sh

8. In your command line, **run `bitrise run {workflow}`**.

##Troubleshooting

**Permission denied when installing mq-cli**

Run `sudo chown -R {username} /usr/local/lib/node_modules` in your terminal. This will give you permission to write to the node_modules directory.

**Gradle-runner step fails for task ':app:mergeDebugResources'**

Don't worry about this error. Run the workflow again, and it should work.