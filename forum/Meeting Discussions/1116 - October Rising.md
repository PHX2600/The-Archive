## October Rising
Posted by **Automated Penguin** on Tue September 22nd, 2009 09:10:13 PM

I'm feeling assembly at this meeting, I know logic has some things in the works and I could pull together some of my PIC work.

Anyone else interested?


Any other Ideas?

I could also bring some dextrin glue for anyone who wants a bit, I don't wanna give it all away but I have enough to give out some samples, enough for you to do a few transfers anyway.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue September 22nd, 2009 11:32:30 PM

I could pay attention to that.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Tue September 22nd, 2009 11:52:18 PM

I got the essentials of my audio driver working (the assembly stuff I've been working on), but it's just a driver. 

I still need to: 
   -get the small quirks worked out (shouldn't be nearly as hard)
   -write an API, or something that makes it easy to communicate with the driver in high level code, also not hard, but will take a little bit of time
   -write some high level code (music), this way you can actually hear what I've done, instead of looking at a complicated and meaningless driver.

The cool thing about the driver is that it is 4-channel. Writing a 1 channel was easy (well, still hard), but writing a 4-channel driver was a completely different approach, I also ended up using 3 (of the 8) processors at once. I am still considering over clocking the chip though. I will attempt to optimize code first (like expanding out loops...hmm, looks like I got another post to make in the code section). If I over clock, I will be able to hit higher frequencies (as in notes) (though I am happy with the range I have now).

I'm not slowing down with the coding, so I will have much more done by the meeting, but I may not have it all done.

-------------------------------
Edit: Ok, just made the compulsive post to to the code section.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed September 23rd, 2009 10:01:25 AM

Would love to see it but prolly won't make next meeting.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed September 23rd, 2009 12:17:12 PM

Well we don't have to limit it to Assembly, we could talk about other machine language level stuff like endianness (<!-- m --><a class="postlink" href="http://en.wikipedia.org/wiki/Endianness">http://en.wikipedia.org/wiki/Endianness</a><!-- m -->) and shellcode (<!-- m --><a class="postlink" href="http://en.wikipedia.org/wiki/Shellcode">http://en.wikipedia.org/wiki/Shellcode</a><!-- m -->) but I don't know if we have anyone who's an expert at that stuff, unless we consider metasploit a part of our group.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed September 23rd, 2009 11:09:32 PM

yeah, the endian model for the propeller is all jerked around, but only really if you look directly at the memory, you can address it fairly normally. It is kind of backwards though, I forget which model that is. I do remember that Intel was backwards too, and most Motorola was normal looking (I first learned assembly on Motorola, the MC68HC11 controller).
