# Integrate with CircleCI

## Introduction

CircleCI is a Continuous Integration and Continuous Delivery platform that allows developers to automate the build, test, and deployment of software for mobile, enterprise, and web applications. MoQuality integrates with CircleCI by simply adding a step to a job. This step enables devleopers to use MQ CLI within their container. The following instructions walk through how to integrate MoQuality with CircleCI.

## Prerequisites

* CircleCI: If you have not yet installed CircleCI, follow the instructions [here](https://circleci.com/docs/2.0/local-cli/).
* MQ CLI: [Install MQ CLI](mq-cli.md#installation).
* MoQuality app: If you intend to upload a new build of an app using MQ CLI, ensure that you have already uploaded the first version through the [MoQuality website](https://app.moquality.com/).

## Instructions

### Open `config.yml`

Open your `config.yml` file in an editor.

### Add Installation Step

Under `steps: ` in your job, add a run step called `Install mq-cli` by using `name:`. Beneath `name:`, add `command: |`. This indicates that you are going to issue multiple lines of commands. Your step should look like the below.

``` YAML
- run:
    name: Install MQ CLI
    command: |
```

### Add Commands to Step

There are four commands you must run to install MQ CLI within your container. The first two are `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -` and `sudo apt-get install -y nodejs`. These commands are based off of [these instructions](https://nodejs.org/en/download/package-manager/) for installing Nodejs via a package manager. Installing Nodejs enables the use of npm commands, which will be necessary for installing MQ CLI. The third command to run is `sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin`. This command will give the user write permissions to two directories whose write permissions are necessary for the installation of MQ CLI. Finally, the command `npm install -g mq-cli` installs MQ CLI. You have now created the step that installs MQ CLI and enables MQ CLI commands within your container. Your step should look like the below.

``` YAML
- run:
    name: Install MQ CLI
    command: |
      curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
      sudo apt-get install -y nodejs
      sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin
      npm install -g mq-cli
```

### Add Login and Upload Step

Now that you have access to MQ CLI commands, you can create a subsequent step of your own to perform a task with these commands. The following sub-instructions breakdown how to write a step that uploads your app to MoQuality using MQ CLI commands.

``` YAML
- run:
    name: Login and Upload to MoQuality
    command: |
      mq login -a [API_KEY]
      mq user
      mq upload -f [APK_PATH] -a [APP_ID]
      mq apps
```

1. The first two lines create a step called `Upload to MoQuality`.

2. As before, the line `command: |` indicates that you are going to issue multiple lines of commands.

3. `mq login -a [API_KEY]` logs you in using your API key. Your API key uniquely identifies your account. To find your API key, run `mq login` in your command line and follow the prompts to log in to your account. Next, run `mq user` to display user information. Your API key will be in the list of returned information.

4. `mq user` returns user information, and you can check that your user is correct.

5. `mq upload -f [APK_PATH] -a [APP_ID]` will upload your app, whose location is provided by `[APK_PATH]`, the path to your apk file. The command uses `[APP_ID]` to determine which app is being uploaded. Your app id uniquely identifies your app. To find your app id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app id in the same row.

6. `mq apps` returns a list of your apps, and you can confirm that your app version has incremented by one.

### Run the Build

Now that you have created new steps, integrating MoQuality with CircleCI, run `circleci build` in your command line to run the build job. If you added the steps within a job other than build, add the `--job` option followed by the name of the job to the `circleci build` command.

## Notes

We do not recommend running the commands to install MQ CLI within a docker image and saving that image for future use. If you do so, and updates to MQ CLI are released, your docker image will not be using them. It is best to install MQ CLI every time you run the workflow, so you are always using the most up-to-date version of MQ CLI. This is what was done within the instructions.

## Troubleshooting

### Write permissions error when installing MQ CLI

Read the error to find the directory to which you cannot write. Add the path of that directory to your `sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin` command. The command will then look like `sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin [DIRECTORY_PATH]`.
