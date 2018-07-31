# Getting Started with Slackbot

## Introduction

MoQuality enables you to schedule tests when you deploy a new build of your app. However, these tests take time, and so does monitoring their success. Rather than watch and wait for your tests to complete, Slack users can install the MoQuality bot to their workspace. This bot will send a notification with test results to your desired Slack channel when a chosen app's test has completed. In order to utilize MoQuality bot's services effectively, there are several steps to follow.

## Prerequisites

* Slack account & workspace: In order to use Slackbot, you will, of course, need to have created a [Slack account](https://slack.com/get-started) and a [workspace](https://slack.com/create).
* MoQuality account: Slackbot will need to link your Slack account to your MoQuality account, which you can create [here](https://app.moquality.com/signup).
* MoQuality app: For the purpose of receiving an app's status updates from Slackbot, ensure that you have already uploaded the first version of your app through the [MoQuality website](https://app.moquality.com/).

## Installation

Install Slackbot from your **[MoQuality account page](https://app.moquality.com/account)** under the `Integrations` tab. Slack will prompt you to authorize the bot for a channel. There is one permission that the bot requires. Said permission is the ability to *Send messages as MoQuality*. This permission is necessary for Slackbot to post messages as a bot user.

## Setup

Once Slackbot is integrated with your workspace, your MoQuality and Slack accounts are linked, and you or anyone else in your workspace can invoke one of Slackbots many [Slash Commands](features/#slash commands). By typing `/mq` in your Slack workspace, you should see a list of the available Slash Commands. The first Slash Command you may want to use is `/mq-subscribe [app Id]`. This command subscribes the authorized channel to test updates from the given MoQuality app. After subscribing the channel, Slackbot posts a public message as an attachment containing information about the subscription.

## Troubleshooting

If you encounter an error, please report it **[LINK NEEDED]**.