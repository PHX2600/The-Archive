## RAPED BY SERVICE PACK 3
Posted by **zaphraud** on Mon September 15th, 2008 05:16:33 PM

[img:dxmzwwpv]http://i33.tinypic.com/n4tmd5.jpg[/img:dxmzwwpv]

Yeah, OK so apparently some jackass at Microsoft made that change in the last few years. Whatever.

But its not just RIAA-backdoors on Audio CDs. The SanDisk Cruzer's AUTORUN.INF is also executed, regardless of the fact that it is most definitely <b>not</b> an audio CD. So, you don't even need to burn an Audio CD full of trojans and viruses to ruin some poor Windows computer, it would seem that autorun is being shoved down the user's throat in many other cases, regardless of group policy settings.

<!-- m --><a class="postlink" href="http://www.dougknox.com/xp/tips/cd_autoplay_pro.htm">http://www.dougknox.com/xp/tips/cd_autoplay_pro.htm</a><!-- m -->
seems pretty widely referenced as a method of preventing the hideous problems associated with autio CD's containing back doors.

It says:
_To Disable CD autoplay, completely, in Windows XP Pro

1) Click Start, Run and enter GPEDIT.MSC

2) Go to Computer Configuration, Administrative Templates, System.

3) Locate the entry for Turn autoplay off and modify it as you desire.
This page last updated 11/25/2005 21:16
All material © 2003 Doug Knox _

Sorry Doug, that apparently doesn't work anymore. Your work has been copied here for the purpose of fair use reporting - namely, to mention the fact that it doesn't work. NOTE: Yes, I am aware the JPG doesn't show "Computer Configuration". The section for "Computer Configuration" and "User Configuration" are identical in this respect, and neither of them disables autoplay on audio CDs according to Microsoft's own documentation.

Doesn't seem to disable autoplay on USB drives either <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( -->
**It appears that what one has to do to is mark the USB filesystem where you have the disable-proof autoplay stored as being CDFS rather than, say, FAT32. Then, Windows gleefully assumes its dealing not with USB Flash, but rather a CDROM hooked up over USB.**

Basically, because of the DMCA and Microsoft's willingness to allow "turn off autoplay" to be labeled as "copy protection circumvention", every windows box with an unsecured USB port is now apparently open for complete rape.

I'd never had a problem with AUTORUN - not since I started turning it off back in 1996 - until today, and I put service pack 3 on yesterday. I have a feeling I got screwed into accepting some update I had previously declined. Fucking piece of shit.

--------------------------------------------------------------------------------

Posted by **dxh** on Mon September 15th, 2008 10:20:19 PM

Might be time to switch to an OS that does not include RAPE by default.  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **nak** on Tue September 16th, 2008 10:59:14 AM

[quote:1wgb2k3f]Fucking piece of shit.[/quote:1wgb2k3f]
QFT

Those U3 drives are annoying, I know penguin was messing around with changing what they execute <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **Evil1** on Thu September 25th, 2008 06:58:00 AM

Hold the phone nak....you still buy CDs? I haven't paid for music in years.

--------------------------------------------------------------------------------

Posted by **nak** on Fri September 26th, 2008 01:45:19 PM

[quote="Evil1":1uhcotfy]Hold the phone nak....you still buy CDs? I haven't paid for music in years.[/quote:1uhcotfy]
Yeah I support unsigned artists etc, but I was talking about thumbdrives <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->
[img:1uhcotfy]http://www.systemaxdev.com/productmedia/htmlimages/cten/Flash%20Drives/109091-front.jpg[/img:1uhcotfy]

--------------------------------------------------------------------------------

Posted by **Ugly** on Sun September 28th, 2008 03:39:26 AM

Does the Shift Key trick work under SP3?

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed December 3rd, 2008 10:19:26 PM

Which trick is that?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu December 4th, 2008 12:30:39 AM

[quote="CultLeadr":1khe4v3s]Which trick is that?[/quote:1khe4v3s]

I think he means holding down the Shift key while inserting a CD to manually disable auto play for that CD.  Personally, I haven't tried it, but will sometime to find out.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu April 30th, 2009 09:46:01 AM

"Microsoft is planning to disable autorun in the next Release Candidate of Windows 7 and future updates to Windows XP and Vista. In order to maintain a 'balance between security and usability,'"

All for you zaph.
