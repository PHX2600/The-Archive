## GPSD for GPS on Linux
Posted by **Automated Penguin** on Tue December 30th, 2008 03:57:26 PM

For a long time now I have been looking for a way to convert from rockwell/zodiac binary to an NMEA format so I could use my GPS with software besides DeLorme , today I am proud to say I have discovered a linux service which does just that

Its called GPSd and it comes with another tool called gpsprof, both are available on repositories in the gpsd-devel package.

Heres a snapshot of the download/installation

[code:9w9znr48]
&#91;root@The_God_Damn_Batman Penguin&#93;# yum install gpsd-devel
Loaded plugins&#58; refresh-packagekit
Setting up Install Process
Parsing package install arguments
Resolving Dependencies
There are unfinished transactions remaining&#46; You might consider running yum-complete-transaction first to finish them&#46;
--&gt; Running transaction check
---&gt; Package gpsd-devel&#46;i386 0&#58;2&#46;37-2&#46;fc9 set to be updated
--&gt; Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package             Arch          Version                Repository       Size
================================================================================
Installing&#58;
 gpsd-devel          i386          2&#46;37-2&#46;fc9             fedora           73 k

Transaction Summary
================================================================================
Install      1 Package(s)         
Update       0 Package(s)         
Remove       0 Package(s)         

Total download size&#58; 73 k
Is this ok &#91;y/N&#93;&#58; y
Downloading Packages&#58;
gpsd-devel-2&#46;37-2&#46;fc9&#46;i386&#46;rpm                           |  73 kB     00&#58;00     
============================== Entering rpm code ===============================
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     &#58; gpsd-devel                                               1/1 
=============================== Leaving rpm code ===============================

Installed&#58;
  gpsd-devel&#46;i386 0&#58;2&#46;37-2&#46;fc9                                                  

Complete!
[/code:9w9znr48]

Next plug in your gps device, my device is an older serial version so I plug it into a usb to serial converter first and then into a usb port on my fedora laptop

Then run the gpsd service taking into account what port you're using (USB0 For me)...

[code:9w9znr48]&#91;root@The_God_Damn_Batman Penguin&#93;# gpsd -N -n -D 2 /dev/ttyUSB0
gpsd&#58; launching (Version 2&#46;37)
gpsd&#58; listening on port gpsd
gpsd&#58; successfully connected to the DBUS system bus
gpsd&#58; running with effective group ID 0
gpsd&#58; running with effective user ID 0
gpsd&#58; opening GPS data source at '/dev/ttyUSB0'
gpsd&#58; speed 9600, 8N1
gpsd&#58; garmin_gps not active&#46;
gpsd&#58; gpsd_activate(1)&#58; opened GPS (5)
gpsd&#58; ntpd_link_activate&#58; 0
gpsd&#58; Software version&#58; 01&#46;98
gpsd&#58; ntpd_link_activate&#58; 1
gpsd&#58; ntpd_link_activate&#58; 1
[/code:9w9znr48]

and then in a separate terminal, run the profiler like so....

[code:9w9znr48]&#91;Penguin@The_God_Damn_Batman ~&#93;$ gpsprof -f cycle
gpsprof&#58; looking for fix&#46;&#46;&#46;first fix in 108&#46;89sec, gathering samples&#46;&#46;&#46;&#46;&#46;&#46;(157&#46;01 sec) done&#46;
Cycle report Tue Dec 30 15&#58;45&#58;23 2008, Zodiac binary 01&#46;98, 9600N1, cycle 1sThe sentence set emitted by this GPS is&#58; 1003 1002 1000
1002&#58; is emitted once a second&#46;
1000&#58; is emitted once a second&#46;
Send cycle is once per second&#46;
[/code:9w9znr48]

the profiler will connect to gpsd, activate the gps and look for a &quot;fix&quot; after that it will gather samples and important information on the GPS, as long as it gets a &quot;fix&quot; then you are ready to go!

here's a snapshot from a program called xgps which is a test program that displays sat info.

[img:9w9znr48]http&#58;//blastwavelabs&#46;com/Media/Uploads/gpsshot&#46;jpg[/img:9w9znr48]


*EDIT*

I posted this here mostly so I don't forget how I did it but also for anyone else who might be interested

--------------------------------------------------------------------------------

Posted by **fightgar** on Tue December 30th, 2008 05:43:43 PM

Yeah forums are searched by google so that's very nice of you <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->
I remember when you were trying to do that, this seems pretty neat... have any plans for a GPS project yet?
