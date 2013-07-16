## Defcon Toolkits
Posted by **Konshu** on Tue May 12th, 2009 10:06:42 AM

I have opened this topic in hopes to collaborate on developing some toolkits before we head off to defcon. I will be bringing along the netbook and will be working on a test environment using ubuntu 9.0.4.  I will update this thread with used software packages, configuration changes and custom scripts as time allows. If you got some input drop it in and lets work as a team!

--------------------------------------------------------------------------------

Posted by **Konshu** on Tue May 12th, 2009 11:48:43 AM

My current setup is:
Ubuntu Desktop 9.0.4  (may customize to netbook version)

My packages of choice to start with are:
openssl-0.9.8k
nmap-4.85BETA8
ncat-0.10rc3
hping3-20051105
yersinia-0.7.1


(Updating as needed)

--------------------------------------------------------------------------------

Posted by **fightgar** on Tue May 12th, 2009 11:57:45 AM

Can't forget ettercap!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue May 12th, 2009 12:12:21 PM

more like etterCRAP amirite? 

j/k! I liek ettercap

Ill be bringing hardware stuff, a bs2 protoboard, soldering iron, pickset, ham radio.

laptop with windows 7 and no security... I guess they call that a &quot;honeypot&quot;

hmm

precooked bacon

A fedora partition loaded to the gillz with junk i probably wont even touch. 

I bet there will be a lot of ssl stripping going on this year with the tool release at blackhat so don't trust anything over the wire pretty much D: poor internet always getting raped by haxors.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue May 12th, 2009 12:50:52 PM

[quote=&quot;Automated Penguin&quot;:dj0g5wkq]...poor internet always getting raped by haxors.[/quote:dj0g5wkq]

Wouldn't be Defcon otherwise.

--------------------------------------------------------------------------------

Posted by **Konshu** on Tue May 12th, 2009 03:26:03 PM

[quote=&quot;PHLAK&quot;:11ky3lw8][quote=&quot;Automated Penguin&quot;:11ky3lw8]...poor internet always getting raped by haxors.[/quote:11ky3lw8]

Wouldn't be Defcon otherwise.[/quote:11ky3lw8]


Maybe we should do a tunneling project and see if anyone can break it <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **Konshu** on Thu May 14th, 2009 02:56:19 PM

Still working on some automation with the installs, for those of you who want the custom tweaks. Will release the scripts when its fully completed.

--------------------------------------------------------------------------------

Posted by **Konshu** on Tue May 26th, 2009 11:13:22 AM

Spent a lot of time playing around with the Ubuntu 9.04 LPIA image at work and will be upgrading the netbook to use this instead of the standard build, which I highly recommend for those of you who are using the Atom based processors. I am also cross comparing my build against the Backtrack 4 beta to see if there is anything of interest that I can add into my build.

--------------------------------------------------------------------------------

Posted by **Konshu** on Fri June 12th, 2009 05:27:07 PM

Updated Config:


[size=150:1n7rm2ai][b:1n7rm2ai]Eeepc 1000HE [/b:1n7rm2ai][/size:1n7rm2ai]
[i:1n7rm2ai]Ubuntu 9.04 Kernel 2.6.30 (custom)[/i:1n7rm2ai]

Currently loaded:
[list:1n7rm2ai]
nmap 4.76
wireshark 1.0.7
aircrack-ng-1.0-rc3
ncurses-5.7
gtk+-2.16.2
glib-2.20.3
DirectFB-1.4.0
openssl-0.9.8k
[/list:u:1n7rm2ai]

Still working out the issue with bluetooth and tweaking some encryption stuff. Then I will start applying the aesthetics and whatnot into it. So far everything else seems solid and I think i got this netbook going as fast as its gonna get.

--------------------------------------------------------------------------------

Posted by **Ghostshell** on Thu June 25th, 2009 12:06:01 PM

laptop w/ Backtrack, also bringing WHAX &amp; Ubuntu along and a Windows Bootable CD, have an app that automates finding wireless keys thats win based, also have a win VM setup using QEMU
