## MS HTTP server running on port 2869
Posted by **fightgar** on Sat May 28th, 2011 11:40:40 PM

I'm on someone else's network and I type this in and I get a listing of my own files... I am not .100, I am .104 at the moment.

Server: Microsoft-HTTPAPI/1.0

What gives? (those are my files btw, I had filesharing enabled, but turned it off, maybe samba yoinked it, but I've never... will continue research and post results

[code:46q5r542]$GET / 192.168.1.100 2869
<HTML>
<HEAD>
<TITLE>Directory /</TITLE>
<BASE HREF="file:/">
</HEAD>
<BODY>
<H1>Directory listing of /</H1>
<UL>
<LI><A HREF="./">./</A>
<LI><A HREF="../">../</A>
<LI><A HREF="bin/">bin/</A>
<LI><A HREF="boot/">boot/</A>
<LI><A HREF="cdrom/">cdrom/</A>
<LI><A HREF="dev/">dev/</A>
<LI><A HREF="etc/">etc/</A>
<LI><A HREF="home/">home/</A>
<LI><A HREF="initrd.img">initrd.img</A>
<LI><A HREF="initrd.img.old">initrd.img.old</A>
<LI><A HREF="justsomesniff">justsomesniff</A>
<LI><A HREF="lib/">lib/</A>
<LI><A HREF="lost%2Bfound/">lost+found/</A>
<LI><A HREF="media/">media/</A>
<LI><A HREF="mnt/">mnt/</A>
<LI><A HREF="opt/">opt/</A>
<LI><A HREF="proc/">proc/</A>
<LI><A HREF="root/">root/</A>
<LI><A HREF="sbin/">sbin/</A>
<LI><A HREF="selinux/">selinux/</A>
<LI><A HREF="srv/">srv/</A>
<LI><A HREF="sys/">sys/</A>
<LI><A HREF="tmp/">tmp/</A>
<LI><A HREF="usr/">usr/</A>
<LI><A HREF="var/">var/</A>
<LI><A HREF="vmlinuz">vmlinuz</A>
<LI><A HREF="vmlinuz.old">vmlinuz.old</A>
</UL>
</BODY>
</HTML>[/code:46q5r542]

--------------------------------------------------------------------------------

Posted by **nak** on Mon May 30th, 2011 05:19:09 PM

lol.
man GET:

[quote:3bbkd653]DESCRIPTION
       This program can be used to send requests to WWW servers and your local
       file system. The request content for POST and PUT methods is read from
       stdin.  The content of the response is printed on stdout.  Error
       messages are printed on stderr.  The program returns a status value
       indicating the number of URLs that failed.[/quote:3bbkd653]

whoops >.<

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue May 31st, 2011 02:59:45 PM

whoa so it saw GET / and decided to do a directory listing of your local disk.

Niceeee.
