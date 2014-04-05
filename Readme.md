#Guided install and configuration for Raspberry Pi Debian


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


These scripts are designed to support @geekscape's Embedded Network Robots workshop at the Melbourne
Connected Community Hacker Space. They should be generally useful.

After following this process you should have

1. A fully updated Raspian system
2. The [Robot Operating System](http://www.ros.org/wiki/) installed and ready to use (optional)
3. Working WiFi
4. Working [Zero Conf](http://en.wikipedia.org/wiki/Avahi_(software) (to access your Pi by hostname instead IP address)
5. Java development kit installed (optional -- larger SD card recommended)
6. Installation of lm-sensors and [i2c](http://en.wikipedia.org/wiki/I%C2%B2C) software
7. [WiringPi](http://wiringpi.com/) library 
8. Raspian configured for your environment (location, language etc)
9. A few select development tools installed (Vim, Emacs, Git, GNU Screen, tmux, ack-grep and Subversion)
10. [Arduino](http://arduino.cc/en/Main/Software) development environment (optional)
11. [NodeBots](http://nodebots.io/) (optional). Will also install Arduino and Java SDK.
12. The default user account renamed to something of your own choice (optional)

<!--
13. A optional script is provided to install Minecraft and set up the API for development. It is *not* depenedent on the other scripts. To install Minefraft type the following at the terminal

`wget http://tinyurl.com/MinecraftOnPi -O - | bash`

-->

Assumes you are using Raspian Linux

ROS installed as per [http://www.ros.org/wiki/groovy/Installation/Raspbian]
## Instructions

* Write  the Raspian image to an SD card in the normal way. 4Gb is is big enough (leaves about 1Gb free)
* Boot the Pi from the new SD image and log in as the default user (initially `pi`)
* If the Raspi Config menu utility appears then configure your keyboard and exit back to the command prompt
* Make sure your Pi has access to the Internet
 * If you have a supported WiFi adapter you can configure it as follows:
  `wpa_passphrase <SSID> <WPA_PASSWORD> | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf`
   then reboot and log as the default user again

* Now run the following command.

`wget http://tinyurl.com/RasPiIoT-1 -O - | bash`

Pi computer now reboots

* Log in as the default user and run the following commands

`wget http://preview.tinyurl.com/RasPiIoT-2 -O - | bash`

This is a long process and will require user input at various stages.

At the end the Pi will reboot


You can use the already existing default user account for development or feel free to create a different user account if you want. The rest
of these notes should be run as that development account. 
  * Edit `~/.bashrc` and add the line `source /opt/ros/groovy/setup.bash` (if you are using the default user account this has already been done for you)
  * Logout and login again
  * Read and review [http://www.ros.org/wiki/ROS/StartGuide]
  * Run the following ROS tutorials

   [http://www.ros.org/wiki/ROS/Tutorials/InstallingandConfiguringROSEnvironment#Create_a_ROS_Workspace]

   [http://www.ros.org/wiki/ROS/Tutorials/NavigatingTheFilesystem]

  * Run the ROS tutorials. E.g. This requires that you have X running as you will need to run multiple terminals at once and display an image.

  Terminal session 1: Run the command `cd catkin_ws; roscore`

  Terminal session 2: Run the command `cd catkin_ws; rosrun roscpp_tutorials talker`

  Terminal session 3: Run the command `cd catkin_ws; rosrun roscpp_tutorials listener`

  Terminal session 4: Run the command `cd catkin_ws; rosrun rqt_graph rqt_graph `

You should now have a correctly installed, tested and configured ROS on Linux system
Now continue Andy’s notes at ``http://tinyurl.com/enr-workshop-1n``

Additional Notes

* This image is _possibly_ missing following Occidentalis [http://learn.adafruit.com/adafruit-raspberry-pi-educational-linux-distro/occidentalis-v0-dot-2] features:
  * Kernel modules for: DS1307, AD626 I2C digipots, HMC6352, BMP085, ADS1015

* Run the command `sudo apt-get update && sudo apt-get dist-upgrade` on a regular basis
(e.g. once a week) to keep the software up to date

* These scripts can be re-run as needed. There is not need to re-image your SD card beforehand.

#TO DO

1. Ask user all questions at the start and then perform an unattended install
2. Provide an activity log
3. Better error detection
