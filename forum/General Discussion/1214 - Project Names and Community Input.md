## Project Names and Community Input
Posted by **Automated Penguin** on Mon February 22nd, 2010 11:36:47 AM

It looks like I'm going to be moving my Ethernet project to the word-press system on this site but before I can do that I have to come up with a suitable name for my project and I'm looking for some input from fellow tinkerers, experimenters, and hackers.

At this point basically what I have is a uC(PIC24) connected by SPI bus to an Ethernet controller (enc28j60) and an sd/transflash card.

This board has the ability to remotely control things via a web interface, host content from the sd card via the web, run multiple types of internet based services (telnet, ftp, dns, etc), it can also act as a passive device logging communications to the SD card. It has many possibilities.

It has a full TCP/IP stack so its compliant with many many protocols, ARP, DNS, DHCP, ICMP, HTTP, etc etc.

I would like to make this a community project if anyone is interested. All the coding is in Microchip C and the TCP/IP stack and file system stack are publicly available from Microchip.

names I have considered include &quot;Aether Tap&quot;, &quot;EEuC&quot; as in Ethernet enabled micro controller and &quot;EXP&quot; as in Experimental Ethernet Platform&quot;

Any input or thoughts would be appreciated,

Thanks.


Edit:
If anyone from Heatsync Labs is interested in this project I would gladly hear your input as well.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon February 22nd, 2010 01:52:37 PM

I like Aether Tap has a nice ring to it 
very interested in this project as im trying to work on something similar

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon February 22nd, 2010 03:22:24 PM

[quote=&quot;TerrorDrone&quot;:aizvd9tz]I like Aether Tap has a nice ring to it 
very interested in this project as im trying to work on something similar[/quote:aizvd9tz]

Maybe ill just keep the original name then for now... Ill start moving over content to the main word press  blog here then, that way people can see what I'm talking about.

Right now I'm working on creating a telnet service for it so i can configure the device remotely.

Thanks for the input.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon February 22nd, 2010 03:29:50 PM

what im trying to do is be able to control remotely from any mobile device be it send an email or twitter message have the micro controller see that and then follow a subroutine based on the command sent 
and if i remember correctly you,re working on a way for it to send a message to you 
an example of what im talking about would be like (email to an account set up for mc) make coffee now
the mc turns on the coffee pot and after another sensor detects coffee is done send message back to me letting me know coffee is done

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon February 22nd, 2010 04:19:22 PM

Stay tuned to the posts I'll be making on the front page then, you may be very interested in what you see.

I have posted a good amount of content on the front page now, I will continue to post as I can.

--------------------------------------------------------------------------------

Posted by **Rax** on Mon February 22nd, 2010 07:52:03 PM

So, what's the project page?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue February 23rd, 2010 08:43:59 AM

[quote=&quot;Rax&quot;:35znj6an]So, what's the project page?[/quote:35znj6an]

I have been told that we no longer have an actual project page D:

only a &quot;project&quot; category under the word press blog on the front page.

I think it would be cool to start an actual project wiki for this thing somewhere on this site but I guess I'm not cool enough to be an admin so I dot have the POWER to do such things.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed February 24th, 2010 06:18:50 PM

Is a Wiki something you actually want?  I may be able to make that happen.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu February 25th, 2010 08:22:22 AM

[quote=&quot;PHLAK&quot;:3kz2sxnk]Is a Wiki something you actually want?  I may be able to make that happen.[/quote:3kz2sxnk]

I'm not sure,

I guess it depends, if no one seems very interested in this then I will just keep working on it solo.

Having a wiki for just one or two contributors would be pretty silly.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri February 26th, 2010 01:45:21 PM

Well, if enough people want to use the wiki (whether for Aether Tap or their own projects), it could become very useful and a good place to collaborate on projects and more.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon March 22nd, 2010 10:20:47 AM

Thank you so much for publishing this project with so much how-to detail. The whole poor-man's PCB start-to-finish instructions are GREAT!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon March 22nd, 2010 01:51:51 PM

Well with any luck ill be posting more later, on a kind of project-overload hiatus right now.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Thu March 25th, 2010 09:35:11 AM

Penguin this project looks great and travels along the same path for a device i want to cook up 
will you be there for april meeting want to pick your brain about this

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu March 25th, 2010 12:45:22 PM

should be there, I was just thinking though that there is only wireless at the meet location so I'm gonna want to figure out how to use my laptop as a bridge or something.

Ill definitely bring something to demo.

See you there.
