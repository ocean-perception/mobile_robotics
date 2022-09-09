---
title: Sensors
weight: 20  # sets order
---

# Sensors

Depending on your robots, you should have a set of 3 or 4 different sensors contemporarily receiving data about your robots location and it's environment. The possible sensors you may have are: magnetometer, encoders, external positioning, lidar.
There might be also an option to include an accelerometer too.

Some sensors will have a much higher reliability than others. For example, the external positioning is likely to be far more accurate than the encoders, as it is always observing the robot from a fixed, external reference frame.

The encoders, even if the easiest to code, as there is a continuous and simple feedback about the motor distance; can be thought to be not as reliable as they have to work on the no-slip assumption. On the current code, an assumption about their turn radius has also been made. Causing a slight variance if the robot actually has a turn radius which differs from the one assumed.

For more information about how the main body of code incorporates the code, proceed to the programming section

## Sensor Code Structure

The code was made in order to attempt to make the combination of information between the sensors as easily as possible

To do this, a structure, seen below was created.

![instance](static/instance.png)

The BaseLoggable class, creates separate message format that both sensors and motors (actuators) will inherit, (and records everything that is sensed or occurred). The sensors class will then configure the sensor by using the *YAML* file.

Working through the tree, the BaseLogger class logs any data it receives, and initially sets the message format for both the BaseSensor and Motors. The BaseSensor the configuration of the sensor, (given in the yaml file), and will configure the correct message type, driver etc.. to the current sensor being recorded. Finally the Sensor records the data, given the message structure and driver.


# Types of sensors

## Lidar

The lidar works by via laser triangulation. It releases very fast pulses of light towards a target and measures the amount of time it takes for the light to travel back.

The message will be saved in the form of a LaserScanMessage:

```python
class LaserScanMessage:
  stamp_s: float
  angle_min_rad: float # start angle of the scan [rad]
  angle_max_rad: float # end angle of the scan [rad]
  time_increment_s: float # time between measurements [seconds]
  range_min_m: float # minimum range value [m]
  range_max_m: float # maximum range value [m]
  ranges: List[float] # range data [m]
  angles: List[float] # angle data [m]
  intensities: List[float] # device-specific units
```

Here is an example scan that the lidar made of it's surrounding space in an office.

![rplidar](static/videos/rplidar.gif)

Of course the information is still contains a fair amount of noise, as students, you will have to filter the information to then be able to use it in order to understand where the robot is with respect to neighbouring walls and maybe other rovers.

## External Localisation

The external localisation is a way to simulate gps or other external positioning methods by using camera vision. The camera recognises the tags, and to due to the nature and distinctiveness of the tags, it is able to very effectively understand both the position and rotation of the tags.

![aruco_example](static/videos/aruco_example.gif)
```python
class RobotStateMessage:
  stamp_s: float  # acquisition time [seconds]
  x_m: float  # x position of the robot [m]
  y_m: float  # y position of the robot [m]
  z_m: float  # z position of the robot [m]
  roll_rad: float  # roll of the robot [rad]
  pitch_rad: float  # pitch of the robot [rad]
  yaw_rad: float  # yaw of the robot [rad]
  vx_mps: float  # linear velocity in x [m/s]
  vy_mps: float  # linear velocity in y [m/s]
  vz_mps: float  # linear velocity in z [m/s]
  wx_radps: float  # angular velocity in x [rad/s]
  wy_radps: float  # angular velocity in y [rad/s]
  wz_radps: float  # angular velocity in z [rad/s]
  ax_mpss: float  # linear acceleration in x [m/s^2]
  ay_mpss: float  # linear acceleration in y [m/s^2]
  az_mpss: float  # linear acceleration in z [m/s^2]
```

## Rotary Encoders

The encoders are electromechanical devices that detects the angular position or motion of a shaft. The Pi-top was configured in such a way that the encoders return angle travelled. As a result the velocity calculated won't be as accurate as other sensors.



## Compass/magnetometer

The magnetometer is a device that measures magnetic field. This sensor will return the yaw of the vessel or vehicle.


## Actuators

```python
class SpeedRequestMessage:
  stamp_s: float # request time [seconds]
  vx_mps: float # linear velocity in x [m/s]
  vy_mps: float # linear velocity in y [m/s]
  vz_mps: float # linear velocity in z [m/s]
  wx_radps: float # angular velocity in x [rad/s]
  wy_radps: float # angular velocity in y [rad/s]
  wz_radps: float # angular velocity in z [rad/s]
```