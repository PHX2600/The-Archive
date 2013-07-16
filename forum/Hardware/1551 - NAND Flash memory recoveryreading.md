## NAND Flash memory recovery/reading
Posted by **nak** on Sat February 11th, 2012 05:04:08 PM

Hi everyone

A friend of mine sent me his flash drive in the mail so I could try and get his data off of it.
I couldn't get ANYTHING off by imaging the drive to a file using dd and then using scalpel (I decided to try that instead of foremost, seems like the same config file, but I guess the internals are more efficient? Thanks logic for dropping that name) -- I looked at the image file and it was 4 gigabytes worth of \x00 as far as the eye could see.

So I began doing research on how to read a NAND chip directly, it seems pretty difficult and requires a bunch of equipment I don't have.

TL;DR:
I have a TSOP-48 sandisk NAND flash chip and if someone has the equipment to poke around on it, that would be fun and I would like to play.  I might even try and get the equipment to do that someday <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat February 11th, 2012 09:05:53 PM

Yeah, if your .dd image is nothing but \x00's, there's no forensics tool that is going to make anything of your dd. You could put a line in your .conf file as such:
	lol	y	1337	\x00\x00\x00
That way you get a massive amount of 1337 byte .lol files full of nothing, I'm sure your looking form &quot;something&quot; instead of &quot;nothing&quot; though, just my guess.

Good luck at the lower level read of the NAND

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 12th, 2012 11:28:11 PM

hehe yeah <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

And, I don't think I'll do it, but I thought of a way to [b:2off3wu5]maybe[/b:2off3wu5] make a test clip out of a bunch of razor blades and doubleside sticky tape... the space between the pins on tsop48 is reaaaaaly small, but I don't know.  It's not THAT interesting or easily feasible for me at the moment <!-- s:-o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":-o" title="Surprised" /><!-- s:-o -->

I could get something like that: [url:2off3wu5]http&#58;//flash-extractor&#46;com/shop/[/url:2off3wu5]

...but the data's not worth more than $30 to said friend <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon February 13th, 2012 08:54:46 AM

[quote=&quot;nak&quot;:25c4cgbt]I looked at the image file and it was 4 gigabytes worth of \x00 as far as the eye could see.[/quote:25c4cgbt]

I agree with XlogicX here.  It sounds like that drive has been zeroed, meaning ZERO data recovery for you or anyone else, but good luck.

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 19th, 2012 12:46:33 AM

just an update for this thread: I wrote an NTFS header to the drive and the nand memory took it and I was able to read the changes in a 2nd dump, so that removes the possibility (that I was hoping for) that the flash memory controller was bork... it looks like maybe the perfect static zap or ??something?? wiped the data, so weird.

At least I learned about NAND and NOR memory, which was neat.

Maybe I'll send the drive in to a professional company, and if they recover any data I'll front the cash (if its not too redic) for my friend and ask them what they did, because as far as I'm concerned they'd have to be some dark wizards (or the controller was really broken... somehow)

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 23rd, 2012 06:01:33 PM

[quote=&quot;nak&quot;:jrxz23gb]Maybe I'll send the drive in to a professional company, and if they recover any data I'll front the cash (if its not too redic)[/quote:jrxz23gb]

I seriously doubt a professional company will help in this case.  See [url=http&#58;//hostjury&#46;com/blog/view/195/the-great-zero-challenge-remains-unaccepted:jrxz23gb]The Great Zero Challenge[/url:jrxz23gb] for more insight into my reasoning.

--------------------------------------------------------------------------------

Posted by **Junker** on Sat February 25th, 2012 02:04:12 AM

[quote=&quot;PHLAK&quot;:3umueuwg]I seriously doubt a professional company will help in this case.  See [url=http&#58;//hostjury&#46;com/blog/view/195/the-great-zero-challenge-remains-unaccepted:3umueuwg]The Great Zero Challenge[/url:3umueuwg] for more insight into my reasoning.[/quote:3umueuwg]

Honestly the $100 prize is a joke, and the rule not to disassemble the drive rules out the easiest ways to do it (If only 2 files existed on the drive, scan it with an electron microscope and look for slight variations which would indicate where the previous files were and what they contained). It can be recovered, but it's neither cheap nor easy to do so. If the read heads can be directly accessed from the board and you interface them with a true voltage sensing device, and if they are sensitive enough, you may be able to do it without opening the drive, but it's gonna be a lot of work. It will also depend on the type of HDD, if you use a serial/USB -&gt; TTL adapter, jump it to the unlabeled pins, and telnet into the drive, some drives have some pretty neat options. I don't know if any can be used to get real sector readings rather than TTL thresholds, but that's the first place I would start before trying to figure out how to interface directly to the board.

As far as flash, never tried anything beyond simple recoveries, might be fun to play with some day

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat February 25th, 2012 05:50:30 AM

I just made a comment on that page <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

[quote:1krpxye8]
XlogicX Says:
Sat, 25 February 2012, 12:39

Dude, I don't know what you guys are talking about, I found all kinds of files when using scalpel or foremost with the following line in my .conf file:

trol y 1337 \x00\x00\x00

It was so many files it started to fill up my other drive. They all appeared to be about 1.3k. I'm not too sure what program opens a .trol file though <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( -->
[/quote:1krpxye8]

Anybody care to make some similar comments. Shit, sorry guys, I just started listening to too much PLA recently.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sun February 26th, 2012 05:13:53 AM

Hmm, looks like my comment has been removed, I wonder why...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun February 26th, 2012 11:41:11 AM

[quote=&quot;XlogicX&quot;:2evvqm48]Hmm, looks like my comment has been removed, I wonder why...[/quote:2evvqm48]

Haha Hilarioussss.
