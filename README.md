# Creston-to-Netatmo-Integration

Special thank you to bitm0de's [HTTPS Utility](https://github.com/bitm0de/HttpsUtility) which made all of this possible!

This is a module created for the integration of Crestron' 4-Series controllers to Netatmo devices. Currently the 3 main devices implemented (4 if you include the gateway) are the NLL light switch, NLFN dimmer, and NLLV shuter.   

# Known Limitations:
* For the shutter and dimmer, after setting the slider level, a digital confirm needs to be sent in order to send the command to the API.
* This module doesn't work in local network, internet is required for this to work. This is an issue from Netatmo themselves and not from this project.
* This doesn't regenerate the refresh token automatically, and you'll have to automate that process.
# How to Add to SIMPL Windows
1. Download the Home + Control app and sign up.
2. Configure your gateway and add all of your devices into your home.
3. Go to https://dev.netatmo.com/apidocumentation/control and use the same account as the Home + Control app to make a dev account.
4. Go to My Apps and create a new app. You'll find the client ID and the client secret created. Those will be put into their respective places in the Main SMW file's Multiple Serial Send.
5. Go back to the https://dev.netatmo.com/apidocumentation/control and then go down to the homesdata command. Click "Try it out" and choose the NLG type before executing the command. You'll find the home_id in the result. Insert that into the SMW as well.
6. In the Netatmo dev page go to the next command homestatus and insert the home ID. You'll get the device IDs of al of your devices. Insert those into the respective modules.
7. Once you upload the project to your controller, you'll need to manually create the first refresh token. Go back to your dev app and for the scopes choose read_magellan and write_magellan and generate the token. Insert the refresh token into your running program as stimulus in the refresh_token signal and send the refresh token command through the controller. Now you should work.
