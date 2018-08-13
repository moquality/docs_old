# MoQuality CLI

## Introduction

MoQuality CLI (MQ CLI) is a Command Line Interface that enables users to interact with MoQuality through their command line.

## Installation

MQ CLI can be installed using either yarn or npm. The respective commands for either are below.

        $ yarn global add mq-cli
        $ npm install -g mq-cli

For a list of MQ CLI commands, type `mq help` in your command line.

## Usage

The standard usage of MQ CLI commands is `mq [COMMAND]`, where COMMAND is one of the commands listed by the `mq help` command and below.

## Commands

* [apps](#apps)
* [help](#help)
* [login](#login)
* [tests](#tests)
* [upload](#upload)
* [user](#user)

### **apps**

Displays a list of the current user's apps.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq apps

### **devices**

Displays a list of the current user's devices. Use these devices while scheduling test runs.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq devices

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id

### **get-recorder**

Downloads or updates the recorder.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq get-recorder

### **help**

Displays the version, usage, and commands for MQ CLI.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq help

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -all                     see all commands in CLI

### **login**

Logs the user in with either their email and password or their API key.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq login

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -e, --email=email        email of user
            -p, --password=password  password of user
            -a, --api_key=api_key    api_key of user

### **schedule**

Schedules test runs for a particular app project. Runs are scheduled on the last uploaded version.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq schedule

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a, --app=app            app id
            -s, --suite=suite        suite id 
            -d, --device=device      device group id

### **status**

Displays status on all test runs for the latest version uploaded for a particular app project.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq status

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id

### **suites**

Displays test suites created for a particular app project.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq devices

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id

### **tests**

Show tests recorded for a particular app project.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq tests

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id

### **upload**

Uploads a new version to an app project on MoQuality.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq upload

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id
            -f, --file=file          location of app

### **user**

Displays current user information.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            $ mq user

## Troubleshooting

### Undocumented Error

If you encounter an error that is not documented, please open an issue on our [public GitHub repository](https://github.com/moquality/devcenter/issues). Alternatively, you can report your error to <hello@moquality.com>.