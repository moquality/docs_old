# Slackbot Features

## Slash Commands

Slack has CLI-like interactions called [Slash Commands](https://api.slack.com/slash-commands). Slash Commands enable the user to directly interact with Slackbot in a variety of ways. Listed below is the full array of Slash Commands that Slackbot supports.

* [/mq-apps](#/mq-apps)
* [/mq-help](#/mq-help)
* [/mq-schedule](#/mq-schedule)
* [/mq-status](#/mq-status)
* [/mq-subscribe](#/mq-subscribe)
* [/mq-user](#/mq-user)

### **/mq-apps**

Posts a private message as an attachment containing the user's apps.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-apps

### **/mq-help**

Posts a private message as an attachment containing information about MoQuality and Slackbot's Slash Commands.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-help

### **/mq-schedule**

Schedules a test for an app that has been created on MoQuality. The necessary information to perform this Slash Command can be obtained with the [MQ CLI](../integration-ci-cd/mq-cli.md). After scheduling the test, Slackbot posts a private message as an attachment containing the status of the newly scheduled test.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-schedule [app Id] [device group Id] [report name] [test suite Id]

### **/mq-status**

Posts a private message as an attachment containing the statuses of tests for an app that has been created on MoQuality.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-status [app Id]

### **/mq-subscribe**

Subscribes the authorized channel to test updates from the given MoQuality app. After subscribing the channel, Slackbot posts a public message as an attachment containing information about the subscription.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-subscribe [app Id]

### **/mq-user**

Posts a private message as an attachment containing information about the MoQuality user linked with the current Slack account.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Usage**

            /mq-user