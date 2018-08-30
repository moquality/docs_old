# Barista Feature List

## Assertions
Add an assertion to your test, to force-check expected outcomes such as checking for specific text or UI element. For example, at the login screen, incase of incorrect username or password, you can add an assertion in Barista to check for the 'Invalid login credentials' text message.

<img src="../android/assertion.gif" style="max-width:800px;max-height:600px" />

## API Requests
Make API requests to your testing environments through the app. Barista allows API requests at any screen of the app. This is most helpful when you might want to initialize user setup before testing the login screen or make an API call to clean out the test data at the end of test flow. 


<img src="../android/api_request.gif" style="max-width:800px;max-height:600px" />

## Explore Tab

You can interact with the hierarchy of your app in the *Explore Tab*. Here you can view widget properties and also add assertions for any screen in your app.

<img src="../android/explore.gif" style="max-width:800px;max-height:600px" />

## Keyboard Input

To enter text input, click the keyboard button below the phone screen

<img src="../android/keyboard.gif" style="max-width:800px;max-height:600px" />

## Recording

When you press record button, the app's cache is automatically cleared, and your app is launched. Auto-launch can be turned off in Settings. While in record mode, all interactions on the phone projection will be recorded. If you unintentiionally clicked an item, you can delete the action from the action list on the right pane. If you delete an action on which the next steps are dependant, the subsequent attempts to run the test can fail.

<img src="../android/record.gif" style="max-width:800px;max-height:600px" />

## Test Editing

To edit a previously recorded test, go into the Tests tab. Open the test and go to the step that you would like to edit. Click the edit icon to open the editor.  Here you can edit the step's description, select a new widget to target, or add a sleep time. Sleep time is helpful when you want the test run to wait until the screen loads completely.

<img src="../android/editing.gif" style="max-width:800px;max-height:600px" />

## Test Replay

After you have a recorded a successful test, proceed to the Tests Tab and replay your test.

<img src="../android/replay.gif" style="max-width:800px;max-height:600px" />
