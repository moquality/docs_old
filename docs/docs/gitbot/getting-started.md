# Getting Started with Gitbot

## Introduction

MoQuality's services provide an invaluable advancement to QA testing, but those advancements are only as powerful as their accessibility. It's difficult to practice continuous integration when you have to manually monitor test statuses after, for example, deploying a new version of your product to a staging environment. MoQuality understands this and has created a GitHub app, referred to as Gitbot, to automatically notify you of test statuses for the new version of your app. Follow the steps below to integrate MoQuality's GitHub app into your development workflow.

## Prerequisites

* GitHub accounts & respository: In order to use Gitbot, you will, of course, need to have created a [GitHub account](https://github.com/join) and a [repository](https://github.com/new).
* MoQuality account: Gitbot will need to link your GitHub account to your MoQuality account, which you can create [here](https://app.moquality.com/signup).
* MoQuality app: For the purpose of test status notifications for a new version of your app, ensure that you have already uploaded the first version of your app through the [MoQuality website](https://app.moquality.com/).

## Installation

Install Gitbot from from your [MoQuality account page](https://app.moquality.com/account) under the `Integrations` tab. Follow the prompts to authorize Gitbot and install it to your desired repository or repositories. You will see that Gitbot will be given ***Read*** *and **write** access to pull requests*. This does not give Gitbot access to the code. It only allows Gitbot to interact with the high-level interfaces such as comments. See the [GitHub API](https://developer.github.com/v3/apps/permissions/#permission-on-pull-requests) for more detailed permissions information.

## Setup

To recieve testing updates in the comments of a pull request, enter your pull request URL when you press the `Generate Tests` button on your MoQuality app's page. This will tell Gitbot where to post status updates from those tests. You can also enter the pull request URL on the test report's page.

## Troubleshooting

If you encounter an error, please open an issue on our [public GitHub repository](https://github.com/moquality/devcenter/issues). Alternatively, you can report your error to <hello@moquality.com>.