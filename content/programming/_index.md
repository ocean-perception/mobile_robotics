---
title: Programming
weight: 7  # sets order
---

# Setting Up 

Now that you have tested that the robot functions correctly. We will begin to go through the main body of code that you will be using thoughout your project. 
It is highly suggested to install VS code, (a code editor like spyder and Jupyter Notebook), as it will show all the python files that you need to work with on the side. 

{{< button href="https://code.visualstudio.com/Download" >}}Install VSCode{{< /button >}}

Both the Land Rover and the Robotic vessel will use the same code. Depending on your robot, you will need to configure it in the "configuration.yaml" file.

The installation will take you to a github repository. To install, click on the code button then install the code by clicking the 'download zip' in the dropdown menu 

{{< button href="https://github.com/ocean-perception/mobile_robotics_python" >}}Main Code{{< /button >}}

![github_repo](static/github_repo.png)

Once installed, extract the folder and open mobile_robotics_python in vs code within mobile_robotics_python-main/mobile_robotics_python-main/src open the folder mobile_robotics_python. Once opened the folder should look something like this:
![initial_folder](static/initial_folder.png)

# Folder Introduction

This folder will be where you will write your code throughout the project. Although the code might look a little intimidating at first. Most of the files withing the folder will work in the background and therefore will not need to be tampered with. 

The objective of your course will be to create new localization_solutions and navigations_solutions so that the robot is able to navigate autonomously to its best ability.

## How the code is structured

When the the code is run, it will got through the main loop within robot.py, the loop follows a sense, think, act structure.


```
while not self.mission_control.finished:
            # Read sensors
            measurements = []
            if self.compass is not None:
                msg = self.compass.read()
                measurements.append(msg)
            if self.encoder is not None:
                self.encoder.yaw_rad = self.compass.yaw_rad
                msg = self.encoder.read()
                measurements.append(msg)
            if self.external_positioning is not None:
                msg = self.external_positioning.read()
                print(msg)
                #measurements.append(msg)
            if self.lidar is not None:
                msg = self.lidar.read()
```


---

# diagram

plantuml
@startuml
  class Example {
    - String name
    - int number 
    
    +void getName()
    +void getNumber()
    +String toString()
  }
@enduml


---
Next slide

---
