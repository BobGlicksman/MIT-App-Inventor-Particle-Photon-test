# MIT-App-Inventor-Particle-Photon-test
Hardware and software to learn to develop apps on MIT app inventor to interact with a Photon over the Internet.

The hardware for this app uses the WLD backlit pushbutton and servo for testing out apps developed with MIT app
inventor 2, albeit an LED on pin D5 and a servo on pin A5 are all that are needed for this testing. The Test_MIT.ino file
is flashed to the Photon for testing.  

You load the ParticleTest.aia file into MIT app inventor 2 in order to work with the app.  This is a source code file and you must
enter your device ID and access token where indicated in order to communicate with your Photon.

The resulting app has three buttons. A pair of buttons is used to turn the Photon D5 LED ON and OFF. 
The return value from the Particle web function "on-off" causes the appropriate button to turn green and 
the other button to turn white, indicating the actual state of the LED connected to the Photon.

The third button (SET) sends a servo angle command to the Photon to control the servo position.  
The servo angle sent is the number displayed in the text box (command) next to the slider control. This command 
text box can be populated with the servo angle number either by typing the number into it or by using the slider 
adjacent to it. The text label next to the SET button displays the actual servo position using the return value from
the "move" web function call to the Photon.

A String variable (�message�) is exposed to the cloud.  This variable contains information about the firmware version and the last reset time (in UTC) for the device.  The app reads this variable at startup and displays a notification to the user to verify that the Photon is on-line and running the expected version of the firmware.

As of this release, the following items work:
- Opening the app displays the firmware version number, time of last reset of the Photon, and OK http status code in a dismissible notification box.  This demonstrates use of the Particle GET to obtain the value of cloud variables.
- the LED ON and LED OFF buttons send commands to the Photon to turn the LED on and off, respectively.  This demonstrates use of Particle POST to call a cloud function.
- the slider sets its value into a text box (command), overwriting any value in it.  
- pressing the SET button sends the number in the text box (command) to the Photon to move the servo.  This also demonstrates use of Particle POST to call a cloud function and how two web �objects� may be used in the app to distinguish the return values from more than one cloud function call.

- the servo response text box displays the return value from the "move" function (the servo command on the Photon).
- the LED "on-off" Photon web function response colors the ON or OFF button green according to the LED state on 
    the Photon via the return value from this web function.

The following additional work is planned:
- clean up procedures calls to get rid of globals and use arguments instead.
- process a file(s) with a list picker to select the device to use (i.e. device ID and access token are in file(s)
    and not hardcoded).
- Change the opening notification.  Wait for the user to select the device and ten perform a cloud query to Particle to see if the device is on line or not and notify the user accordingly.

