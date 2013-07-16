#Creating a working ROS Image for @geekscape's Embedded Network Robots workshop
##Date : 13/July/2013

 Copyright (c) 2013 All Right Reserved  Alec Clews

 author: Alec Clews
 alecclews@gmail.com

    This document is free documentation; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This material is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License along
    with this program; if not, write to the Free Software Foundation, Inc.,
    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.



Based On Raspian and ROS installed as per http://www.ros.org/wiki/groovy/Installation/Raspbian
## Instructions

* Write  the Raspian image to an SD card in the normal way. 4Gb is is big enough (leaves about 1Gb free)
* Boot the Pi from the new SD image.
* Make sure your Pi has access to the Internet
* Log in and run the following commands

`wget http://tinyurl.com/runme1st -O - | bash`

Pi now reboots

* Log in and run the following commands

`wget http://tinyurl.com/runme2nd -O - | bash`

* Now run sudo raspi-config interactively and set following options

  * Default  Locale: (e.g. en_AU.UTF-8)
  * Local Time Zone
  * Keyboard: 105 Int Generic English US  (also suggest CTRL_ALT_BKSPC kills X)
  * Enable camera (optional)
  * Clock set HIGH -- 950MHz ARM 250MHz core 450MHz SDRAM 6 overvolt (suggested)
  * Memory Split:   16MB for GPU (suggested)

* Run command

`sudo shutdown -rF now # reboots`

You can use the already existing pi user account for development or feel free to create a different user account if you want. The rest of these notes should be run as that development account. 
Edit ~/.bashrc and add the line source /opt/ros/groovy/setup.bash
Logout and login again
Read and review http://www.ros.org/wiki/ROS/StartGuide
Run the following ROS tutorials

http://www.ros.org/wiki/ROS/Tutorials/InstallingandConfiguringROSEnvironment#Create_a_ROS_Workspace
http://www.ros.org/wiki/ROS/Tutorials/NavigatingTheFilesystem

Run Andy’s demo. This requires that you have X running as you will need to run multiple terminals at once and display an image.
Terminal session 1: Run the command `cd catkin_ws; roscore`
Terminal session 2: Run the command `cd catkin_ws; rosrun roscpp_tutorials talker`
Terminal session 3: Run the command `cd catkin_ws; rosrun roscpp_tutorials listener`
Terminal session 4: Run the command `cd catkin_ws; rosrun rqt_graph rqt_graph `

You should now have a correctly installed, tested and configured ROS on Linux system
Now continue Andy’s notes at http://tinyurl.com/enr-workshop-1n

Additional Notes

* This image is missing following Occidentals features:
  * avahi daemon
  * Realtek RTL8188CUS wifi support
  * One wire support on GPIO #4 when loaded
  * Kernel modules for: DS1307, AD626 I2C digipots, HMC6352, BMP085, ADS1015

* Run the command `sudo apt-get update && sudo apt-get dist-upgrade` on a regular basis
(e.g. once a week) to keep the software up to date
* To install Java JDK (optional) see http://elinux.org/RPi_Java
* If you have a WiFi adaptor and want to use the local wireless
  * Edit the file /etc/network/interfaces (needs sudo access)
  * Make sure the file contains a stanza similar to the following
    ```auto wlan0
    allow-hotplug wlan0
    iface wlan0 inet dhcp
            wpa-ssid "SSID"
            wpa-psk "WIFI_PASSWORD"
```
  N.B. you will nee to know the correct values for the SSID and WIFI_PASSWORD for your site
  * Run the command `sudo /etc/init.d/networking restart`

