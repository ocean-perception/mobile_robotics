---
title: External localisation
weight: 1  # sets order
---

# External localisation

## ArUco setup Checklist 

### Before Turning on the Pi 

Ensure Camera is in centre of tank and is facing the tank, (and is connected to the pi) 

Ensure No ArUco Markers Are visible in the Camera frame (flip them upside down to ensure they can’t be seen) 

Ensure that the Router is turned on and that it’s Wifi led is on, (doesn’t need to be connected to the internet) 

Turn On the Rasberry pi, (may take a while, if no monitor attached wait 1 minute to ensure everything has booted up before configuring) 

 

When booting the Pi, the ArUco code should start automatically, therefore it is not necessary to connect a keyboard or mouse to the Pi. If desired, a monitor may be connected to transmit all the Pi’s Information, (recommended). 

 

### When Pi is turned on 

To newly calibrate the origin location, place the Calibration tag (#0) where desired, (ensure it is flat and not moving), the origin will be located in the centre of this marker. Then Show the ‘OK’ (#49) tag in frame. Only when the 2 tags are recognised in frame will the code save the position. 

If you want to use the old Calibrated Origin, then the previous step can be skipped by only showing the ‘OK’ (#49) in frame. 

If the step was done incorrectly, proceed to show the Shut-down tag (#40) together with the ‘OK’ (#49) tag in frame. WAIT 1 minute (to ensure that pi properly switches off), then proceed to turn the pi’s power off then on. (This should reboot the program) 

***The Setup-phase is now completed ***

## Broadcast Frequency,
(frequency at which the Server Pi will send the coordinates to the Client Pi’s) has a possible configuration of ‘logging speed’ (~10th of a second), 1s, 2s, 5s, 10s and never. On boot the pi will be initially setup to send the information every 1s. 

To change the show the desired Broadcast Frequency tag (shown in table below) in frame, with the ‘OK’ tag (#49). 

 

At logging speed 

1s 

2s 

5s 

10s 

Never 

#30 

#31 

#32 

#33 

#34 

#35 

 

If a Display is connected to the Pi, the broadcast frequency will be visible as a frame will blink around the screen at every broadcasted interval, (when an ArUco marker is being shown). 

The Server Pi should Now be all set! 

To Turn Off the Pi show the Shut-down tag (#40) together with the ‘OK’ (#49) tag in frame. WAIT 1 minute (to ensure that pi properly switches off).  

The Pi will Log all the ArUco tag information in a csv file of which’ name will be ‘#.csv’ where # is the ArUco Tag’s ID. All these files will be stored in a folder named after the exact time the Pi was booted up, example: ‘2022_07_25_12_34_18’, where is in this order: (‘Year_Month_Day_Hour_Minute_Second’).  

All information will be saved on the ssd card connected separately. This can be disconnected when the Pi is of to read the information from another computer. (there will be a long usb extension so that it is easily accessible). 

 

## Setting up the Client Pi’s, (Robots) 

Make sure all packages have been installed and the Chrony configuration have been made. 

Open the Python file  

Run the file  

 

 

 

 

## Debugging 

If robot is not receiving information 

Uncomment the ‘print(broadcast_data) line’: 

If nothing the Robot is still not reading anything when any ArUco tag is shown in the camera frame then, (recognised when frame frown around Tag):  

Remember position data will only be broadcasted from the Server Robot once the setup phase is complete) 

Ensure The Client (Robot) Pi is connected to local Router, (called: ArUco) 

Ensure the Port to the one shown on screen from the Rasberry pi, (if so change variable called port to one shown on Server Pi display) 

Ensure no Other code has been altered other than what has been instructed.  

If nothing is still being received please change rasberry pi. 

 

 