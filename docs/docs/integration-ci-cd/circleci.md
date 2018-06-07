# Integrating with CircleCI

## Getting Started

CircleCI is a Continuous Integration and Continuous Delivery platform that allows developers to automate the build, test, and deployment of software for mobile, enterprise, and web applications. MoQuality integrates with CircleCI by simply adding a step to a job. This step enables devleopers to use mq-cli within their container. The following instructions walk through how to integrate MoQuality with CircleCI.

## Prerequisites

* CircleCI: If you have not yet installed CircleCI, follow the instructions [here](https://circleci.com/docs/2.0/local-cli/).
* mq-cli: To install mq-cli, run `npm install -g mq-cli` in your terminal.
* MoQuality app: If you intend to upload a new build of an app using mq-cli, ensure that you have already uploaded the first version through the [MoQuality website](https://app.moquality.com/).

## Instructions

1. **Open your config.yml file** in an editor.

2. Under `steps: ` in your job, **add a run step called `Install mq-cli`**.

        - run:
            name: Install mq-cli

3. Beneath `name:`, **add `command: |`**. This indicates that you are going to issue multiple lines of commands. Your step should look like the below.

        - run:
            name: Install mq-cli
            command: |

4. There are **four commands you must run to install mq-cli** within your container. The first tw are **`curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`** and **`sudo apt-get install -y nodejs`**. These commands are based off of [these instructions](https://nodejs.org/en/download/package-manager/) for installing Nodejs via a package manager. Installing Nodejs enables the use of npm commands, which will be necessary for installing mq-cli. The third command to run is **`sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin`**. This command will give the user write permissions to two directories whose write permissions are necessary for the installation of mq-cli. Finally, the command **`npm install -g mq-cli`** installs mq-cli. You have now created the step that installs mq-cli and enables mq-cli commands within your container. **Your step should look like the below**.

        - run:
            name: Install mq-cli
            command: |
              curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
              sudo apt-get install -y nodejs
              sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin
              npm install -g mq-cli

5. Now that you have access to mq-cli commands, you can create a subsequent step of your own to perform a task with these commands. The following sub-instructions breakdown **how to write a step that uploads your app to MoQuality** using mq-cli commands.

        - run:
            name: Upload to MoQuality
            command: |
              mq login -a {API_KEY}
              mq user
              mq upload -f {APK_PATH} -a {APP_ID}
              mq apps
        
    1. The first two lines create a step called `Upload to MoQuality`.

    2. As before, the line `command: |` indicates that you are going to issue multiple lines of commands.

    3. `mq login -a {API_KEY}` logs you in using your API key. Your API key uniquely identifies your account. To find your API key, run `mq login` and follow the prompts to log in to your account. Next, run `mq user` to display user information. Your API key will be in the list of returned information.

    4. `mq user` returns user information, and you can check that your user is correct.

    5. `mq upload -f {APK_PATH} -a {APP_ID}` will upload your app, whose location is provided by `{APK_PATH}`, the path to your apk file. The command uses `{APP_ID}` to determine which app is being uploaded. Your app id uniquely identifies your app. To find your app id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app id in the same row.

    6. `mq apps` returns a list of your apps, and you can confirm that your app version has incremented by one.

7. Now that you have created new steps, integrating MoQuality with CircleCI, **run `circleci build`** in your command line to run the build job. If you added the steps within a job other than build, **add the `--job` flag followed by the name of the job** to the `circleci build` command.

## Notes

We do not recommend running the commands to install mq-cli within a docker image and saving that image for future use. If you do so, and updates to mq-cli are released, your docker image will not be using them. It is best to install mq-cli every time you run the workflow, so you are always using the most up-to-date version of mq-cli. This is what was done within the instructions.

## Troubleshooting

**Write permissions error when installing mq-cli**

Read the error to find the directory to which you cannot write. Add the path of that directory to your `sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin` command. The command will then look like `sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin {DIRECTORY_PATH}`.