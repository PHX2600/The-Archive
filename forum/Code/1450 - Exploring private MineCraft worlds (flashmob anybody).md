## Exploring private MineCraft worlds (flashmob anybody?)
Posted by **XlogicX** on Fri September 2nd, 2011 10:54:05 PM

I know this is borderline for being code, but here's my bash script&#058;

[code:2gmfpdfp]
nmap -p 25565 -PN --excludefile scanned_so_far&#46;txt -oG current_scan&#46;txt -iR 1000 | grep open -B 4
cat current_scan&#46;txt | grep Up | awk '{print $2}' &gt; current_scan_sanitized&#46;txt
cat scanned_so_far&#46;txt current_scan_sanitized&#46;txt &gt; temp&#46;txt
cp temp&#46;txt scanned_so_far&#46;txt
rm temp&#46;txt
grep open current_scan&#46;txt &gt; mc_current_scan&#46;txt
cat mc_current_scan&#46;txt | awk '{print $2}' &gt; mc_current_scan_sanitized&#46;txt
cat motherload&#46;txt mc_current_scan_sanitized&#46;txt &gt; temp&#46;txt
cp temp&#46;txt motherload&#46;txt
rm temp&#46;txt
[/code:2gmfpdfp]

I'm sure of it that I am inefficiently using the cat, cp, rm combo a couple of times (could just be one line of code instead of 3). But this script get'sthe job done. The number after the -iR (random) switch could be changed from 1000. 1000 takes about a minute to complete. The only reason I pipe to grep on the first line is to kind of watch things as they progress, it's not actually a critical part of the script at all.

This script can be run several times and keeps track of which IP's it's already scanned as not to repeat. There's some deduping I probably need to do to the final result file (motherload.txt) though.

Although, I gotta say, scanning random IP's is giving me lots of false positives, even though the correct port is open. I have gotten much better results just scanning some /16's in the 68. range. Actually, 100% no false positives, each and every IP returned open for port 25565 is a legit minecraft server.

------------------------------------------------

I will leave this thread open as the &quot;Minecraft flashmob&quot; idea thread. Although, I plan on refraining from posting any actual IP's here, that could just be some bad etiquette.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue September 6th, 2011 10:31:29 AM

Hexelent,

I was hoping you would post that code.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue September 13th, 2011 09:00:44 AM

Do you have a personal server?

If so are you going to reset it for 1.8?

I would love to get on there and play some time if so.

-Peng

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue September 13th, 2011 10:23:28 AM

Dude Logic.

I accidentally your whole code.

<!-- m --><a class="postlink" href="https://github.com/PHX2600/MineScan">https://github.com/PHX2600/MineScan</a><!-- m -->

Check it out!

Functionality is basically the same just all commented up n shite

I hope you don't mind my unilateral collaboration.

-Peng

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed September 14th, 2011 02:53:53 PM

Found a few on ASU's network. FUN!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu September 15th, 2011 11:46:38 AM

If you want access to that repo Logic, give me your Github account name and I'll give it to you.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue September 20th, 2011 03:59:51 PM

I think we can eliminate false positives by including a little more code to attempt a login.

<!-- m --><a class="postlink" href="http://mc.kev009.com/Protocol#Login_Request_.280x01.29">http://mc.kev009.com/Protocol#Login_Request_.280x01.29</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri October 7th, 2011 05:39:02 AM

1.8 may be more interesting, was looking at wireshark and it passes mod info and such. It may also be passing how many people are online as well, it would have to somehow with the new network setup. I would really love to try writing an NSE script, but I'm way noob at that, so if anybody has any NSE experience, I'd love to talk about it at the meeting or even here works.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon October 10th, 2011 09:02:21 AM

Compelling,

An NSE would let us do service detection right from NMAP right?

I think that would be pretty fun to play with, maybe if I get bored at work.

--EDIT--

Found a sweet intro vid covers use and development of scripts.

<!-- m --><a class="postlink" href="http://www.youtube.com/watch?v=yC7AGLEYq4o&amp;feature=player_embedded">http://www.youtube.com/watch?v=yC7AGLEY ... r_embedded</a><!-- m -->

--EDIT--

Another productive day at work!

<!-- m --><a class="postlink" href="https://github.com/Penguin2600/Minecraft-NSE/blob/master/minecraft.nse">https://github.com/Penguin2600/Minecraf ... ecraft.nse</a><!-- m -->

Works pretty great!

And now I can say I have experience with LUA. Cool.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon October 10th, 2011 10:31:23 PM

Cool!

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Fri October 14th, 2011 09:20:05 AM

If we do end up doing a virtual flashmob, we should all use skins that make us look like endermen.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat October 15th, 2011 12:45:09 AM

Endermen aren't scary enough yet though...perhaps though, as we will be scary

--------------------------------------------------------------------------------

Posted by **nak** on Fri October 21st, 2011 07:24:10 PM

(sl)endermen
