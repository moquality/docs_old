# PTBot Features

## Upload App Reminder

When a story is in the `Delivered` state, that is, when the story is ready to be accepted or rejected, PTBot will post to the story a comment, reminding you to upload the new version of your app to MoQuality.

## Status Updates

If PTBot has been [configured correctly](getting-started.md#setup), it will post updates from tests to the comments of a story. These updates may also contain screenshots, visualizing the pages on which a test failed or succeeded.

## Future Features

In the future, PTBot could be capable of identifying links to a GitHub pull request in a Pivotal Tracker story. If the user has [configured Gitbot correctly](../../gitbot/getting-started), PTBot could automatically post updates to a GitHub pull request with only the URL to the Pivotal Tracker story, if the bot had been configured to do so.

## Feature Request

Do you have a request for a new feature? Open an issue on our [public GitHub repository](https://github.com/moquality/devcenter/issues) with your feature request! Alternatively, you can send your feature request to <hello@moquality.com>.