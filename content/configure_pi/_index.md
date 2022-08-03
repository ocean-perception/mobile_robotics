---
title: configure_pi
bookCollapseSection: true
weight: 50 # sets order
---

# Chrony Configuration
Chrony is an implementation of NTP, it allows for the pi's to synchronize their time even if internet is not connected to one of them. It acts as a daemon in the background. So when setup it should never need to be reconfigured or edited with afterwards.
## Client Configuration (student Pi)
Go in the Pi terminal
type 'sudo apt-get install vim-y' to install vim, (a unix text editor)
make sure you are connecting to the correct router on the rasberry pi, then to find your ip type 'ip a | grep inet', and copy the third line with 'inet', (may differ: should read something such as '10.10.20.153/24', only copy the fist section, in this case that would be '10.10.20.153'
type 'vim /etc/chrony/chrony.conf'

Below the initial comment, (above all other code) write in a new line: 'server <copied_ip> iburst prefer' where <copied_ip> is the item you have just copied
then finally save the document by pressing Ctrl + C, typing ':x' and pressing Enter. 
(you should have now returned to the original terminal window)
then type 'systemctl restart chrony'
to check if the server is working, type: 'chronyc sources'

## Server Configuration (Camera system Pi)

