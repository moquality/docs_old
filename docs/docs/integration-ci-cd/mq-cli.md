# MoQuality CLI

## Introduction

The MoQuality CLI (MQ CLI) is a Command Line Interface that enables users to interact with MoQuality through their command line.

## Installation

The MQ CLI can be installed using either yarn or npm. The respective command for either method is below.

``` shell
        yarn global add mq-cli
        npm install -g mq-cli
```

For a list of the MQ CLI's commands, type `mq help` in your command line.

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

``` shell
        mq apps
```

### **help**

Displays the version, usage, and commands for the MQ CLI.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

``` shell
        mq help
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Arguments**

            COMMAND  command to show help for

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -all                     see all commands in CLI

### **login**

Logs the user in with either their email and password or their API key.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

``` shell
        mq login
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -e, --email=email        email of user
            -p, --password=password  password of user
            -a, --api_key=api_key    api_key of user

### **tests**

Show tests recorded for a particular app project.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

``` shell
        mq tests
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id

### **upload**

Uploads a new version to an app project on MoQuality.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

``` shell
        mq upload
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Options**

            -a --app=app             app id
            -f, --file=file          location of app

### **user**

Displays current user information.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

``` shell
        mq user
```

## Troubleshooting

### Undocumented Error

If you encounter an error that is not documented, please open an issue on our [public GitHub repository](https://github.com/moquality/devcenter/issues). Alternatively, you can report your error to <hello@moquality.com>.