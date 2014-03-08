## NAND Flash memory recovery/reading
Posted by **nak** on Sat February 11th, 2012 05:04:08 PM

Hi everyone

A friend of mine sent me his flash drive in the mail so I could try and get his
data off of it. I couldn't get ANYTHING off by imaging the drive to a file using
dd and then using scalpel (I decided to try that instead of foremost, seems like
the same config file, but I guess the internals are more efficient? Thanks logic
for dropping that name) -- I looked at the image file and it was 4 gigabytes
worth of \x00 as far as the eye could see.

So I began doing research on how to read a NAND chip directly, it seems pretty
difficult and requires a bunch of equipment I don't have.

TL;DR: I have a TSOP-48 sandisk NAND flash chip and if someone has the equipment
to poke around on it, that would be fun and I would like to play.  I might even
try and get the equipment to do that someday :)

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat February 11th, 2012 09:05:53 PM

Yeah, if your .dd image is nothing but \x00's, there's no forensics tool that is
going to make anything of your dd. You could put a line in your .conf file as
such:

    lol    y    1337    \x00\x00\x00

That way you get a massive amount of 1337 byte .lol files full of nothing, I'm
sure your looking form "something" instead of "nothing" though, just my guess.

Good luck at the lower level read of the NAND

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 12th, 2012 11:28:11 PM

hehe yeah :)

And, I don't think I'll do it, but I thought of a way to **maybe** make a test
clip out of a bunch of razor blades and doubleside sticky tape... the space
between the pins on tsop48 is reaaaaaly small, but I don't know.  It's not THAT
interesting or easily feasible for me at the moment :-o

I could get something like that: <http://flash-extractor.com/shop/>

...but the data's not worth more than $30 to said friend :P

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon February 13th, 2012 08:54:46 AM

> **nak wrote:**
>
> I looked at the image file and it was 4 gigabytes worth of \x00 as far as the
> eye could see.

I agree with XlogicX here.  It sounds like that drive has been zeroed, meaning
ZERO data recovery for you or anyone else, but good luck.

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 19th, 2012 12:46:33 AM

just an update for this thread: I wrote an NTFS header to the drive and the nand
memory took it and I was able to read the changes in a 2nd dump, so that removes
the possibility (that I was hoping for) that the flash memory controller was
bork... it looks like maybe the perfect static zap or ??something?? wiped the
data, so weird.

At least I learned about NAND and NOR memory, which was neat.

Maybe I'll send the drive in to a professional company, and if they recover any
data I'll front the cash (if its not too redic) for my friend and ask them what
they did, because as far as I'm concerned they'd have to be some dark wizards
(or the controller was really broken... somehow)

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 23rd, 2012 06:01:33 PM

> **nak wrote:**
>
> Maybe I'll send the drive in to a professional company, and if they recover
> any data I'll front the cash (if its not too redic)

I seriously doubt a professional company will help in this case.  See
[The Great Zero Challenge](http://hostjury.com/blog/view/195/the-great-zero-challenge-remains-unaccepted)
for more insight into my reasoning.

--------------------------------------------------------------------------------

Posted by **Junker** on Sat February 25th, 2012 02:04:12 AM

> **PHLAK wrote:**
>

> I seriously doubt a professional company will help in this case.  See
> [The Great Zero Challenge](http://hostjury.com/blog/view/195/the-great-zero-challenge-remains-unaccepted)
> for more insight into my reasoning.

Honestly the $100 prize is a joke, and the rule not to disassemble the drive
rules out the easiest ways to do it (If only 2 files existed on the drive, scan
it with an electron microscope and look for slight variations which would
indicate where the previous files were and what they contained). It can be
recovered, but it's neither cheap nor easy to do so. If the read heads can be
directly accessed from the board and you interface them with a true voltage
sensing device, and if they are sensitive enough, you may be able to do it
without opening the drive, but it's gonna be a lot of work. It will also depend
on the type of HDD, if you use a serial/USB -> TTL adapter, jump it to the
unlabeled pins, and telnet into the drive, some drives have some pretty neat
options. I don't know if any can be used to get real sector readings rather than
TTL thresholds, but that's the first place I would start before trying to figure
out how to interface directly to the board.

As far as flash, never tried anything beyond simple recoveries, might be fun to
play with some day

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat February 25th, 2012 05:50:30 AM

I just made a comment on that page :)

> XlogicX Says:
> Sat, 25 February 2012, 12:39
>
> Dude, I don't know what you guys are talking about, I found all kinds of files
> when using scalpel or foremost with the following line in my .conf file:
>
>     trol y 1337 \x00\x00\x00
>
> It was so many files it started to fill up my other drive. They all appeared to
> be about 1.3k. I'm not too sure what program opens a .trol file though :(

Anybody care to make some similar comments. Shit, sorry guys, I just started
listening to too much PLA recently.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sun February 26th, 2012 05:13:53 AM

Hmm, looks like my comment has been removed, I wonder why...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun February 26th, 2012 11:41:11 AM

> **XlogicX wrote:**
> Hmm, looks like my comment has been removed, I wonder why...

Haha Hilarioussss.
