# iOS

In order to use the recorder with iOS devices, some configuration is necessary. This page documents that configuration.

Note: These steps were gathered via repeated attempts to determine the code signing process. It is possible that earlier attempts affected the steps determined, meaning that these may not work on a clean setup. Further testing is necessary.

### Log in to Apple Developer Portal

First, log into [the Apple Developer Portal](https://developer.apple.com/). Click the Account link at the top of the page to access your account info. In the sidebar on the left, you should see the following links:

<img src="../img/01.png" width="270px">

Click the "Certificates, IDs & Profiles" link.

If you already have a valid certificate, skip to step 3 (Alternate).

## Generate a certificate

Above the certificate list on the next page, click the `+` button to generate a new certificate.

<img src="../img/02.png" width="320px">

Select "iOS App Development".

<img src="../img/03.png" width="680px">

The next page should give you instructions on how to generate a CSR. Follow those instructions before continuing.

<img src="../img/04.png" width="680px">

<img src="../img/05.png" width="680px">

## Import the certificate

Download the newly generated certificate.

<img src="../img/06.png" width="680px">

If you already have a certificate generated, navigate to the certificate list, find your certificate, click on it, and then click the download button in the expanded panel.

<img src="../img/07.png" width="680px">

Once the certificate is downloaded, locate it in Finder and double-click it. This should open the Keychain Access app with the certificate newly imported into the "System" keychain. To find it, click System in the sidebar, and then Certificates.

<img src="../img/08.png" width="200px">

The certificate needs to be moved to the "local" keychain. To do so, simply drag it from the list of certificates on the local keychain in the sidebar. Once this is done, it should appear under "My Certificates", rather than just under "Certificates".

## Generate an App ID

Back in the developer portal, click "App IDs" on the sidebar.

<img src="../img/10.png" width="200">

Click the `+` button at the top, much like when generating a certificate.

<img src="../img/09.png" width="450px">

Name the ID something reasonable for its use, such as "Recorder".

<img src="../img/11.png" width="450px">

Select "Wildcard App ID" and enter a single asterisk as the ID.

**Take note of the Team ID listed under the "App ID Prefix". You'll need it.**

<img src="../img/12.png" width="450px">

Click "Done".

## Generate a mobile provisioning profile

Click "All" under "Provisioning Profiles" in the sidebar. You may need to scroll down to see it.

<img src="../img/13.png" width="200px">

Click the `+` button to generate a new profile, and then select "iOS App Development".

<img src="../img/14.png" width="450px">

Select the App ID that you generated in the previous step.

<img src="../img/15.png" width="450px">

Select the certificate generated in step 2, or your existing certificate if you did not generate one.

<img src="../img/16.png" width="600px">

Click the "Select All" checkbox on the device list.

<img src="../img/17.png" width="600px">

Enter a name for the profile.

<img src="../img/18.png" width="550px">

You do *not* need to download the profile. That will be handled automatically.

<img src="../img/19.png" width="550px">

## Set up environment variables

The final step is to set the `$DEVELOPMENT_TEAM` environment variable to the Team ID from step 4. There are several ways to do this, but one of the simplest is to add the variable to the `.bash_profile` file in your home directory.

Open the `$HOME/.bash_profile` file in an editor of your choice and add the following line to the end of it:

```
bash export DEVELOPMENT_TEAM=<Team ID>
```

Replace `<Team ID>` with the your team ID.

Once this is done, you will need to log out and back in. Then simply run the recorder as normal.

## Ensure xcode is in system path

Go to `Xcode > Preferences > Locations`, and assign the Command Line Tools to XCode.
