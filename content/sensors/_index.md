---
title: Sensors
weight: 1  # sets order
---

# Sensors

Depending on your robots, you should have a set of 3 or 4 different sensors contemporarily recieving data about your robots location and it's environment. The possible sensors you may have are: magnetometer, encoders, external positioning, lidar.
There might be also an option to include an accelerometer in your code if you wish so. 

Some sensors will have a much higher reliability than others. For example, the external positioning is likely to be far more accurate than the encoders, as it is always observing the robot from a fixed, external reference frame. 

The encoders, even if the easiest to code, as there is a continuos feedback about how much the motors have moved, can be thought to be not as reliable as they have to work on the no-slip asumption. On the current code, an assumption about their turn radius has also been made. Causing a slight varience if the robot actually has a turn radius which differs from the one assumed. 

Here is an example of the robot moving in a square path based upon encoder readings and a basic navigation solution.

{{< vimeo 740325079 >}}