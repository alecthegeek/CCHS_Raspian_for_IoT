#Guided install and configuration for Raspberry Pi Debian


 Copyright (c) 2013-2015 All Right Reserved  Alec Clews
 
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/alecthegeek/CCHS_Raspian_for_IoT?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge) or [IRC] irc://irc.gitter.im/alecthegeek\/CCHS_Raspian_for_IoT

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


These scripts were originally designed to support @geekscape's Embedded Network Robots
workshop at the Melbourne Connected Community Hacker Space. They should now be
generally useful for people working on Internet of Things projects
(.e.g mesh networking, robotics, Arduino, etc etc) and wanting to do
general development on a Raspberry Pi using Node, Java, Go etc.

After following this process you should have

1. Raspian configured for your environment (location, language etc)
2. The default user account renamed to something of your own choice and your own choice of hostname (optional)
5. A fully updated Raspian system
7. A few select development tools installed (Vim, GNU Screen, tmux, ack-grep and Subversion)
9. The [Robot Operating System](http://www.ros.org/wiki/) installed and ready to use (optional)
10. [Arduino](http://arduino.cc/en/Main/Software) development environment (optional)
11. [NodeBots](http://nodebots.io/) (optional). Will also install Arduino, ino, Firmata from SimpleBots and Java SDK
12. Robotnik
13. Golang and the [Gobot](http://gobot.io) libraries (otional)
14. Additional support to change network config by editing a text file (/boot/machine.local) on a workstation (optional)


NB These scripts assume you are using the current version of Raspian Linux (Debian Linux)

## Instructions
* Write  the Raspian image to an SD card in the normal way. 4Gb is is big enough
for the basics
* Boot the Pi from the new SD image and log in as the default user (initially `pi`)
* If the Raspi Config menu utility appears then configure your keyboard and exit
back to the command prompt
* Make sure your Pi has access to the Internet
 * If you have a supported WiFi adapter you can configure it as follows:
  `wpa_passphrase <SSID> <WPA_PASSWORD> | 
          sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf`
   then reboot and log as the default user again

* Now run the following command.

`script log1 -c "time bash <(wget https://tinyurl.com/RasPiIoT-1 -O -)"`

  Log file in `log1`


Pi computer now reboots

* Log in as the default user and run the following commands

`script log2 -c "time bash <(wget https://tinyurl.com/RasPiIoT-2 -O -)"`

  Log file in `log2`

This can be a long process and will require user input at various stages.

At the end the Pi will reboot

There is also an optional script to install support for [M9Design](http://www.m9design.co/)'s MeshThing IPv6 mesh networking platform. After running the `RasPiIoT-1` and `RasPiIoT-2` (see above) run

`script log3 -c "bash <(wget -O - https://tinyurl.com/meshthing)"`

#Note

* Run the command `sudo apt-get update && sudo apt-get dist-upgrade` on a regular basis
(e.g. once a week) to keep the software up to date

* These scripts can be re-run as needed. There is not need to re-image your SD card beforehand.

#TO DO

1. Ask user all questions at the start and then perform an unattended install
2. Provide an activity log
3. Better error detection
