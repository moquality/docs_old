# Recorder Feature List

## Assertions
Add an assertion to your test, to force-check expected outcomes such as checking for specific text or UI element. For example, at the login screen, incase of incorrect username or password, you can add an assertion in the recorder to check for the 'Invalid login credentials' text message.

<img src="../android/assertion.gif" style="max-width:800px;max-height:600px" />

## API Requests
Our recorder allows to make API requests. It is useful in many scenarios where a user has to record a step and make an API request.
You can send API requests from within the app to set up your testing environment.

<img src="../android/api_request.gif" style="max-width:800px;max-height:600px" />

## Explore Tab

You can interact with the hierarchy of your app in the *Explore Tab*. Here you can view widget properties and add assertions for any screen in your app.

<img src="../android/explore.gif" style="max-width:800px;max-height:600px" />

## Keyboard Input

To enter keyboard input, you must go through the keyboard button below the phone screen

<img src="../android/keyboard.gif" style="max-width:800px;max-height:600px" />

## Recording

When you press record, you app's cache will automatically cleared, and your app launched. You can turn auto-launch off in Settings. While in record mode, all interactions on the phone projection will be recorded. If you accidentally misclick an item, or an action wasn't intentional, you can delete the action from the action list to the right. Be warned! If you delete an action upon which later actions are dependant, such as a click that causes the app to change screens, subsequent attempts to run the test will fail.

<img src="../android/record.gif" style="max-width:800px;max-height:600px" />

## Test Editing

To edit a previously recorded test, go into the Tests tab. Open up the test you would like to edit and hover over the specific step. Click the edit icon to drop down into the editor.  Here you can edit the step description, select a new widget to target, and add a sleep action to happen after the step runs. This can be helpful if your app is taking too long to process a specific screen, and the replay algorithm has already moved on.

<img src="../android/editing.gif" style="max-width:800px;max-height:600px" />

## Test Replay

After you have a recorded a successful test, proceed to the Tests Tab and replay your test!

<img src="../android/replay.gif" style="max-width:800px;max-height:600px" />
