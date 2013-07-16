## MS HTTP server running on port 2869
Posted by **fightgar** on Sat May 28th, 2011 11:40:40 PM

I'm on someone else's network and I type this in and I get a listing of my own files... I am not .100, I am .104 at the moment.

Server: Microsoft-HTTPAPI/1.0

What gives? (those are my files btw, I had filesharing enabled, but turned it off, maybe samba yoinked it, but I've never... will continue research and post results

[code:46q5r542]$GET / 192&#46;168&#46;1&#46;100 2869
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;TITLE&gt;Directory /&lt;/TITLE&gt;
&lt;BASE HREF=&quot;file&#58;/&quot;&gt;
&lt;/HEAD&gt;
&lt;BODY&gt;
&lt;H1&gt;Directory listing of /&lt;/H1&gt;
&lt;UL&gt;
&lt;LI&gt;&lt;A HREF=&quot;&#46;/&quot;&gt;&#46;/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;&#46;&#46;/&quot;&gt;&#46;&#46;/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;bin/&quot;&gt;bin/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;boot/&quot;&gt;boot/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;cdrom/&quot;&gt;cdrom/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;dev/&quot;&gt;dev/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;etc/&quot;&gt;etc/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;home/&quot;&gt;home/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;initrd&#46;img&quot;&gt;initrd&#46;img&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;initrd&#46;img&#46;old&quot;&gt;initrd&#46;img&#46;old&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;justsomesniff&quot;&gt;justsomesniff&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;lib/&quot;&gt;lib/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;lost%2Bfound/&quot;&gt;lost+found/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;media/&quot;&gt;media/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;mnt/&quot;&gt;mnt/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;opt/&quot;&gt;opt/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;proc/&quot;&gt;proc/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;root/&quot;&gt;root/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;sbin/&quot;&gt;sbin/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;selinux/&quot;&gt;selinux/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;srv/&quot;&gt;srv/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;sys/&quot;&gt;sys/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;tmp/&quot;&gt;tmp/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;usr/&quot;&gt;usr/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;var/&quot;&gt;var/&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;vmlinuz&quot;&gt;vmlinuz&lt;/A&gt;
&lt;LI&gt;&lt;A HREF=&quot;vmlinuz&#46;old&quot;&gt;vmlinuz&#46;old&lt;/A&gt;
&lt;/UL&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;[/code:46q5r542]

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

whoops &gt;.&lt;

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue May 31st, 2011 02:59:45 PM

whoa so it saw GET / and decided to do a directory listing of your local disk.

Niceeee.
