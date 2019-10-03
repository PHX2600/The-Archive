## Carrier IQ (Cell fone logging)
Posted by **ArchAngel** on Wed November 30th, 2011 08:00:21 AM

Not sure if anyone else has been following this, but it seems like even MSM is picking up the story now:
<!-- m --><a class="postlink" href="http://www.theregister.co.uk/2011/11/30/smartphone_spying_app/">http://www.theregister.co.uk/2011/11/30 ... pying_app/</a><!-- m -->

Full text of the Register article in case it gets taken down:
[quote:cbn75klq]
An Android app developer has published what he says is conclusive proof that millions of smartphones are secretly monitoring the key presses, geographic locations, and received messages of its users.

In a YouTube video posted on Monday, Trevor Eckhart showed how software from a Silicon Valley company known as Carrier IQ recorded in real time the keys he pressed into a stock EVO handset, which he had reset to factory settings just prior to the demonstration. Using a packet sniffer while his device was in airplane mode, he demonstrated how each numeric tap and every received text message is logged by the software.

Ironically, he says, the Carrier IQ software recorded the “hello world” dispatch even before it was displayed on his handset.
 
Eckhart then connected the device to a Wi-Fi network and pointed his browser at Google. Even though he denied the search giant's request that he share his physical location, the Carrier IQ software recorded it. The secret app then recorded the precise input of his search query – again, “hello world” – even though he typed it into a page that uses the SSL, or secure sockets layer, protocol to encrypt data sent between the device and the servers.

“We can see that Carrier IQ is querying these strings over my wireless network [with] no 3G connectivity and it is reading HTTPS,” the 25-year-old Eckhart says.

The video was posted four days after Carrier IQ withdrew legal threats against Eckhart for calling its software a “rootkit.” The Connecticut-based programmer said the characterization is accurate because the software is designed to obscure its presence by bypassing typical operating-system functions.

In an interview last week, Carrier IQ VP of Marketing Andrew Coward rejected claims the software posed a privacy threat because it never captured key presses.

“Our technology is not real time,” he said at the time. "It's not constantly reporting back. It's gathering information up and is usually transmitted in small doses.”

Coward went on to say that Carrier IQ was a diagnostic tool designed to give network carriers and device manufacturers detailed information about the causes of dropped calls and other performance issues.

Eckhart said he chose the HTC phone purely for demonstration purposes. Blackberrys, other Android-powered handsets, and smartphones from Nokia contain the same snooping software, he claims.

The 17-minute video concluded with questions, including: “Why does SMSNotify get called and show to be dispatching text messages to Carrier IQ?” and “Why is my browser data being read, especially HTTPS on my Wi-Fi?”

The Register has put the same questions to Carrier IQ, and will update this post if the company responds.
[/quote:cbn75klq]

And a link to the YouTube vijeo referenced:
<!-- m --><a class="postlink" href="http://www.youtube.com/watch?v=T17XQI_AYNo">http://www.youtube.com/watch?v=T17XQI_AYNo</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri December 2nd, 2011 12:36:19 PM

[quote:2fmwm298]There is no risk of [Carrier IQ] to ever be shipped as a part of CyanogenMod, period.[/quote:2fmwm298]
Source: <!-- m --><a class="postlink" href="http://www.cyanogenmod.com/blog/cyanogenmod-will-never-have-carrier-iq">http://www.cyanogenmod.com/blog/cyanoge ... carrier-iq</a><!-- m -->

This is a hacking forum so I hope everyone knows about CyanogenMod for your Android phones, but if not...

[size=150:2fmwm298]**GO INSTALL CYANOGENMOD ON YOUR ANDROID PHONE NOW!!!!**[/size:2fmwm298]
(Assuming your phone is supported)

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri December 2nd, 2011 05:00:47 PM

This scratches the surface of the malware out there for the Android (iPhones and Blackberry's have it too, but nowhere near the amount). There are a lot of 'free' apps,' keep your hacker suspicion hat on, after all, we've had that hat on for decades when it comes to this kind of thing. There are even apps that are legitimate, for a while, to bypass any kind of reporting and to get the largest market share. But then there is the dreaded update, to which everyone at that point has the malicious version.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 3rd, 2011 02:40:27 AM

Jeeze, I've been seeing this in the news quite a bit now. Looks like the most notable thing is that it's already on the phone and the most effective way to get rid of it is to root the phone (and then get rid of it).

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 3rd, 2011 03:31:24 AM

Another interesting article (statements from phone companies):

<!-- m --><a class="postlink" href="http://www.engadget.com/update/carrier-iq-which-companies-have-the-smarts/">http://www.engadget.com/update/carrier- ... he-smarts/</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **nak** on Sat December 3rd, 2011 06:57:13 PM

Neat...

Has anyone here run USB debugging on their phone? Is there special hardware?
Why did we not notice this before that nerd from CT?

[url=http://www.youtube.com/watch?v=ofHr8Lv5cNk:4nwfgnra]It seems like carrier IQ are some pretty cool dudes <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->>

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon December 5th, 2011 08:10:48 AM

[quote="nak":gylq1kxe]Has anyone here run USB debugging on their phone? Is there special hardware?[/url][/quote:gylq1kxe]

You can enable USB debugging on (I believe) any android phone from the settings menu.  With that enabled, you can run [url=http://developer.android.com/guide/developing/tools/adb.html:gylq1kxe]Android Debug Bridge (ADB)> on your PC and debug stuff.

--------------------------------------------------------------------------------

Posted by **Urbal** on Mon December 5th, 2011 09:39:34 AM

Is anyone aware of how to check/remove this from a rooted phone?

--------------------------------------------------------------------------------

Posted by **nak** on Tue December 6th, 2011 12:38:27 PM

I don't have an android, or else I would've probably been doing USB debugging when I first got it...  <!-- s:? --><img src="{SMILIES_PATH}/icon_e_confused.gif" alt=":?" title="Confused" /><!-- s:? --> where da haxors?!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue December 6th, 2011 04:29:13 PM

[quote="nak":5kz9rv9v]I don't have an android, or else I would've probably been doing USB debugging when I first got it...  <!-- s:? --><img src="{SMILIES_PATH}/icon_e_confused.gif" alt=":?" title="Confused" /><!-- s:? --> where da haxors?![/quote:5kz9rv9v]

Done tons of USB Debuggin on mine while developing APPS but my phone is an old moto-roll'a so it doesnt have that CIQ junk.

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue December 6th, 2011 09:22:59 PM

[quote="Urbal":djfha70p]Is anyone aware of how to check/remove this from a rooted phone?[/quote:djfha70p]

As Phlak said, installing Cyanogenmod is a surefire way to get rid of it.

<!-- m --><a class="postlink" href="http://www.cyanogenmod.com/">http://www.cyanogenmod.com/</a><!-- m -->

As for an app that searches for CarrierIQ installed on your phone? Not sure. Haven't heard of one, but it might very well exist.

--------------------------------------------------------------------------------

Posted by **ArchAngel** on Wed December 7th, 2011 08:09:35 AM

[quote="AltF4":280vzvlh][quote="Urbal":280vzvlh]Is anyone aware of how to check/remove this from a rooted phone?[/quote:280vzvlh]

As Phlak said, installing Cyanogenmod is a surefire way to get rid of it.

<!-- m --><a class="postlink" href="http://www.cyanogenmod.com/">http://www.cyanogenmod.com/</a><!-- m -->

As for an app that searches for CarrierIQ installed on your phone? Not sure. Haven't heard of one, but it might very well exist.[/quote:280vzvlh]

Trevor Eckhart (firmware h4x0r that lives in CT if I recall) has a good article on this:
<!-- m --><a class="postlink" href="http://androidsecuritytest.com/features/logs-and-services/loggers/carrieriq/">http://androidsecuritytest.com/features ... carrieriq/</a><!-- m -->

The take-away/tl;dr is: CarrierIQ is a rootkit, so you will have to root your fone to get rid of it. 

Specifically to answer the question about whether there's an app to remove Carrier IQ -- I believe the Pro version of Trevor's app does so, but it does cost $1 US and requires root ... so cyanogen is probably still the best/cheapest answer. *shrugz*

--------------------------------------------------------------------------------

Posted by **Urbal** on Wed December 7th, 2011 10:47:34 AM

Unfortunately, CM7 is not available for the Samsung Epic.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed December 7th, 2011 11:52:50 AM

[quote="Urbal":1cuws39a]Is anyone aware of how to check/remove this from a rooted phone?[/quote:1cuws39a]

From what I recall, navigate to Settings -> Applications -> Manage Applications -> All (tab) then look for anything named "CarrierIQ" or "CIQ".  If you see this on your phone then you have it.  As for removing it, I know there's a way to do it via the terminal (app or via ADB), but would have to look that up.

The easy way would be to grab [url=https://market.android.com/details?id=com.keramidas.TitaniumBackup&amp;feature=search_result#?t=W251bGwsMSwyLDEsImNvbS5rZXJhbWlkYXMuVGl0YW5pdW1CYWNrdXAiXQ..:1cuws39a]Titanium Backup> from the market and remove it through there.  I'm not sure, but you may need [url=https://market.android.com/details?id=com.keramidas.TitaniumBackupPro&amp;feature=search_result:1cuws39a]Titanium Backup Pro> (worth the money) to do it.

--------------------------------------------------------------------------------

Posted by **nak** on Mon December 12th, 2011 03:58:22 PM

FBI: Carrier IQ files used for "law enforcement purposes"
<http://www.muckrock.com/news/archives/2011/dec/12/fbi-carrier-iq-files-used-law-enforcement-purposes/>

haha
o wow... pretty sensationalist title... but yeah...
