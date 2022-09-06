---
title: pi_configuration
bookCollapseSection: true
weight: 70 # sets order
---

# Raspberry Pi Configuration

In theory ***your raspberry pi's should be already configured***, if so please do not go through this page.
If your pi unfortunately got it's memory erased, or you were handed one with nothing on it, then read ahead.

# Installing the Main Code

You can install the main code by writing:

To install your main code you will first need to install the git installer, to do this write the following in your pi's terminal, (following code is for linux):

```sudo apt-get install git```

once it has finished install, type the following command in the terminal, this will install the repository to your pi:

```git clone https://github.com/ocean-perception/mobile_robotics_python```

if this does not work, please ask for a member of staff for help.


# Chrony Configuration
Chrony is an implementation of NTP, it allows for the pi's to synchronize their time even if internet is not connected to one of them. It acts as a daemon in the background. So when setup it should never need to be reconfigured or edited with afterwards.


## Server Configuration (Camera system Pi)
1. Install an editor of your choice (nano, vim, gedit), for example for `vim` you would write

```
sudo apt install vim
```

2. Install chrony with

```
sudo apt install chrony
```

3. TBD


## Client Configuration (student Raspberry Pi)
1. Install an editor of your choice (nano, vim, gedit), for example for `vim` you would write

```
sudo apt install vim
```

2. Install chrony with

```
sudo apt install chrony
```

4. Find or ask the IP address of the chrony server in the local network (the wifi router network). It should be something like `192.168.0.X`, where the last `X` will change for a number 0-254.
5. Edit chrony configuration, and add the following line at the top of the file

```
server 192.168.0.X
```

where `X` has to be changed for the correct IP. The file is located at `/etc/chrony/chrony.conf`. To edit it, you will need to use `sudo`, for example:
```
sudo vi /etc/chrony/chrony.conf
```
6. Verify that you can get the updates. First restart chrony with

```
sudo systemctl restart chrony
```

and now verify that chrony is using your IP by running the command

```
chronyc sources
```
