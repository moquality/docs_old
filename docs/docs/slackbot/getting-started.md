# Getting Started with Slackbot

## Introduction

MoQuality enables you to schedule tests when you deploy a new build of your app. However, these tests take time, and so does monitoring their success. Rather than watch and wait for your tests to complete, Slack users can install the MoQuality bot to their workspace. This bot will send a notification with test results to your desired Slack channel when a chosen app's test has completed. In order to utilize MoQuality bot's services effectively, there are several steps to follow.

## Prerequisites

* Slack account & workspace: In order to use Slackbot, you will, of course, need to have created a [Slack account](https://slack.com/get-started) and a [workspace](https://slack.com/create).
* MoQuality account: Slackbot will need to link your Slack account to MoQuality account, which you can create [here](https://app.moquality.com/signup).
* MoQuality team: **NEED THIS!**
* MoQuality app: For the purpose of receiving an app's test updates from Slackbot, ensure that you have already uploaded the first version of your app through the [MoQuality website](https://app.moquality.com/).

## Installation

Download Slackbot from **[HERE]**. Slack will prompt you to authorize the bot for a channel. There are two permissions that the bot requires. The first permission is the ability to *Access information about your public channels*. This permission is necessary for proper onboarding, as the bot must acccess your channel's list of users in order to send them onboarding messages. The second permission is the ability to *Send messages as MoQuality*. This permission is necessary for Slackbot to post messages as a bot user.

## Setup

Once Slackbot is installed to your workspace, there is a **critical step** you must take to enable proper interaction with Slackbot. Enter `/mq-link [API KEY]`, where [API KEY] is your API key, the unique identifier to your MoQuality account. **TEAM ID OR USER ID????**