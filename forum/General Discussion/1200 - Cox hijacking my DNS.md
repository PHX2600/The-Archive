## Cox hijacking my DNS
Posted by **AltF4** on Wed January 27th, 2010 07:15:15 PM

So I noticed recently that Cox has been hijacking DNS queries that don't lead to anywhere, and putting up an annoying Cox web page. 

Normally this would irk me only moderately, but this time they screwed it up. I'm doing a class project in Minix (don't ask), and they're doing this for all of its queries. But I can't for the life of me figure out why.

Any other experiences / gripes / workarounds with this sort of thing?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed January 27th, 2010 10:00:57 PM

You could point your DNS to the Google Public DNS (8.8.8.8 and 8.8.4.4), and that might help.  Or similarly use OpenDNS free and your failed DNS querys will go to their crappy result page.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu January 28th, 2010 07:51:32 AM

Memorize all the ip's for your favorite sites and don't rely on DNS you lazy bastard.

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu January 28th, 2010 05:53:58 PM

Seriously, there has been several times now where I've had an internet connection but no DNS for whatever reason. I should make a list of IP's and keep it around for just such occasions.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri January 29th, 2010 08:28:39 AM

Google Public DNS  - 8.8.8.8, 8.8.4.4

Just plug those into your router as static DNS. I hate relying on my ISP's DNS, it's always slow and goes down all the time.  If not Google, try <http://opendns.org>.  Those are your two best options.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 29th, 2010 02:47:30 PM

[quote="PHLAK":ozdno9hw]Google Public DNS  - 8.8.8.8, 8.8.4.4

Just plug those into your router as static DNS. I hate relying on my ISP's DNS, it's always slow and goes down all the time.  If not Google, try <http://opendns.org>.  Those are your two best options.[/quote:ozdno9hw]



hmm seems like I have heard this before....

--------------------------------------------------------------------------------

Posted by **chespirito** on Sat February 6th, 2010 10:45:52 PM

That sort of thing happens from time to time. I didn't know Google had its own DNS servers that people could use, I'll have to try that some time. But would they then track/log all the info relating to it for their advertising (or other) purposes?

I have used OpenDNS (<!-- m --><a class="postlink" href="http://www.opendns.com">http://www.opendns.com</a><!-- m -->) servers several times with no problems (208.67.222.222, 208.67.220.220)

Here are some others you could use, depending on context:

current Cox cable (residential  &amp;  business):
68.105.28.16
68.105.29.16

old/defunct Cox DNS servers:
68.105.28.11
68.105.28.12
68.105.29.11
68.2.16.30
68.1.208.30
(I was told by a Cox rep that these addresses can still be used, they just forward to the current live DNS servers.)

Qwest DSL:
205.171.3.65
205.171.2.65

~Chesy

--------------------------------------------------------------------------------

Posted by **wendoxin** on Thu June 16th, 2011 12:28:06 AM

How to search Live Connection ie IP address (live DNS server) on LAN ? I use LAN connection in my hostel and DNS server is set. But someone is changing that server(ie IP address).Is there any software that can recognize that live server ?
