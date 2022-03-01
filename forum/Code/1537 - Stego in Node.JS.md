## Stego in Node.JS
Posted by **nak** on Tue January 17th, 2012 05:29:44 PM

K got this working today: <http&#58;//abovesobelow&#46;com&#58;3000/>

Upload a picture and a file you want to hide (the secret) and then it'll get converted to a bmp, cheaply stego'd and then returned, save the file and the offset, then someone can extract the data using the decoder side.

It is very young of course... so be gentle, and no hacking allowed <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

PS:
Keep the file you want to hide smallish, or else the algo I'm using (at the moment) will clobber the bitmap header

PPS:
Here's the code on github: <https&#58;//github&#46;com/naked/node-stego>

PPPS:
Don't worry about clobbering the file anymore, I've got checks in place, and the technique is completely different.  This project is pretty much cast aside at the moment though.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed January 18th, 2012 06:11:14 PM

Cool, I'll have to check that out when I get a sec.

--------------------------------------------------------------------------------

Posted by **nak** on Fri January 20th, 2012 09:59:24 PM

<http&#58;//abovesobelow&#46;com&#58;3000/demo&#46;htm> -- here's a video demo so people aren't confused, and I found some more issues that need fixing while recording the demo the first time, had to tweak the file width for the 2nd run /me patches

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat January 21st, 2012 10:23:21 AM

I tried it. Awesome.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat January 21st, 2012 12:04:38 PM

Impressive. I hear jpg is a pain in the ass to work with for that.

--------------------------------------------------------------------------------

Posted by **nak** on Sat January 21st, 2012 10:20:18 PM

Yes xlogicx, JPG would be a pain to work with, even PNG is difficult (the first format I studied).  Penguin linked me to this the other day:
<http&#58;//www&#46;darkside&#46;com&#46;au/gifshuffle/>

Which is a stego application for GIF files, it doesn't let you hide a lot, but still a very interesting concept.

I just fixed the program so it takes the least significant nibble correctly, and wow you can't even tell the image has been modified! Yay, got it working <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> Should be live very soon.

I saw this tweet while looking around: <http&#58;//twitter&#46;com/#!/AdmiralA/status/159763277767913472> and made me think of the twitter stego application, maybe I'll work on that next, make a fake &quot;teen twerp&quot; account that is constantly updating with information, I'd want it to be practical though, maybe a P2P network tracker or something?  Just an interesting idea <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sun January 22nd, 2012 06:00:24 AM

Yeah, in theory, if you have a byte for red, green, and blue, that's 256 shades of each. If you just changing the LSB of blue, your changing it by 1/256th of a shade. That should be very hard to see.

And I'm totally going in a different direction on the stego topic for the later presentation, I PM'd you about it. Let me know if you have any ideas on that theme. Even though the twitter one would be a good example of a less common technique.

--------------------------------------------------------------------------------

Posted by **nak** on Sun January 22nd, 2012 12:16:06 PM

I'm taking the lowest significant nibble (4 bits) and its barely noticeable <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> -- and I've read the PM, just haven't responded, maybe I will today <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat February 18th, 2012 03:54:23 PM

Is the demo retired Nak?

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 19th, 2012 12:03:59 AM

[quote=&quot;CultLeadr&quot;:3vf5d3yv]Is the demo retired Nak?[/quote:3vf5d3yv]

wow! good catch, I shut it down last night (I've been working on this: <http&#58;//mindsforge&#46;com/dotty/> and I needed to close one of the old node projects I had open so I could use a port.

I hopefully just started it again.  The server clears out the &quot;working&quot; folders every day with a cron script, so any files that are uploaded shouldn't be on the server for more than a day... however don't use this for anything sensitive <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> I hope I don't need to write a disclaimer ^.^;

Again, very quick catch, I'm surprised/glad  <!-- s:oops: --><img src="{SMILIES_PATH}/icon_redface.gif" alt=":oops:" title="Embarrassed" /><!-- s:oops: -->
