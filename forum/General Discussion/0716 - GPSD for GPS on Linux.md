## GPSD for GPS on Linux
Posted by **Automated Penguin** on Tue December 30th, 2008 03:57:26 PM

For a long time now I have been looking for a way to convert from rockwell/zodiac binary to an NMEA format so I could use my GPS with software besides DeLorme , today I am proud to say I have discovered a linux service which does just that

Its called GPSd and it comes with another tool called gpsprof, both are available on repositories in the gpsd-devel package.

Heres a snapshot of the download/installation

[code:9w9znr48]
[root@The_God_Damn_Batman Penguin]# yum install gpsd-devel
Loaded plugins: refresh-packagekit
Setting up Install Process
Parsing package install arguments
Resolving Dependencies
There are unfinished transactions remaining. You might consider running yum-complete-transaction first to finish them.
--> Running transaction check
---> Package gpsd-devel.i386 0:2.37-2.fc9 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package             Arch          Version                Repository       Size
================================================================================
Installing:
 gpsd-devel          i386          2.37-2.fc9             fedora           73 k

Transaction Summary
================================================================================
Install      1 Package(s)         
Update       0 Package(s)         
Remove       0 Package(s)         

Total download size: 73 k
Is this ok [y/N]: y
Downloading Packages:
gpsd-devel-2.37-2.fc9.i386.rpm                           |  73 kB     00:00     
============================== Entering rpm code ===============================
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : gpsd-devel                                               1/1 
=============================== Leaving rpm code ===============================

Installed:
  gpsd-devel.i386 0:2.37-2.fc9                                                  

Complete!
[/code:9w9znr48]

Next plug in your gps device, my device is an older serial version so I plug it into a usb to serial converter first and then into a usb port on my fedora laptop

Then run the gpsd service taking into account what port you're using (USB0 For me)...

[code:9w9znr48][root@The_God_Damn_Batman Penguin]# gpsd -N -n -D 2 /dev/ttyUSB0
gpsd: launching (Version 2.37)
gpsd: listening on port gpsd
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
gpsd: garmin_gps not active.
gpsd: gpsd_activate(1): opened GPS (5)
gpsd: ntpd_link_activate: 0
gpsd: Software version: 01.98
gpsd: ntpd_link_activate: 1
gpsd: ntpd_link_activate: 1
[/code:9w9znr48]

and then in a separate terminal, run the profiler like so....

[code:9w9znr48][Penguin@The_God_Damn_Batman ~]$ gpsprof -f cycle
gpsprof: looking for fix...first fix in 108.89sec, gathering samples......(157.01 sec) done.
Cycle report Tue Dec 30 15:45:23 2008, Zodiac binary 01.98, 9600N1, cycle 1sThe sentence set emitted by this GPS is: 1003 1002 1000
1002: is emitted once a second.
1000: is emitted once a second.
Send cycle is once per second.
[/code:9w9znr48]

the profiler will connect to gpsd, activate the gps and look for a "fix" after that it will gather samples and important information on the GPS, as long as it gets a "fix" then you are ready to go!

here's a snapshot from a program called xgps which is a test program that displays sat info.

[img:9w9znr48]http://blastwavelabs.com/Media/Uploads/gpsshot.jpg[/img:9w9znr48]


*EDIT*

I posted this here mostly so I don't forget how I did it but also for anyone else who might be interested

--------------------------------------------------------------------------------

Posted by **fightgar** on Tue December 30th, 2008 05:43:43 PM

Yeah forums are searched by google so that's very nice of you <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->
I remember when you were trying to do that, this seems pretty neat... have any plans for a GPS project yet?
