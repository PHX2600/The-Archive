## NON-BABY RELATED THREAD!
Posted by **Automated Penguin** on Mon November 17th, 2008 03:06:05 PM

Counteracting baby overdose with hardware hacking 

One of the things that bugged me about having a ham radio is that the average person cant listen in without buying a scanner or a transceiver for a couple hundred bucks. 

So.. 

I modded my [http://www.icomamerica.com/en/products/amateur/mobile/2200h/default.aspx](ICOM IC-2200H) to transmit from 118-175MHz instead of the standard 2 meter 144-148MHz Ham band. which happens to cover the 162-163MHz Weather Channel band. As you may know you can get a simple weather band receiver for under 20 dollars from many places.

So I found a weather channel frequency that wasn't in use in mesa 
(Channels 3 and 6 are completely empty and channel 1 is only partially audible)
And played it over the transmitter on 162.450(wx band channel 3), tuned in channel 3 on my weather band radio and enjoyed a stroll around the park listening to my own private radio station, 5 watts carries pretty far but I could probably cover much of the city at 65 watts which is the peak output of the transmitter I have 

Brief Vid of Me all excited and testing my setup:
<!-- m --><a class="postlink" href="http://blastwavelabs.com/Media/Uploads/MVI_0314.avi.MPG">http://blastwavelabs.com/Media/Uploads/MVI_0314.avi.MPG</a><!-- m -->
(double extentions due to conversion  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) --> )

The circuit you see in the video uses a PIC 16f88 to convert serial data sent from a python program into signals that control the radio.

Cant play it for very long maybe only several minutes at a time unless I want the FCC tracking me down and asking me how my radio ended up so far off ham bands and why i'm using it to transmit music  <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **nak** on Mon November 17th, 2008 03:15:54 PM

You're gonna get V&amp; <!-- s8-) --><img src="{SMILIES_PATH}/icon_cool.gif" alt="8-)" title="Cool" /><!-- s8-) -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue November 18th, 2008 08:49:43 AM

Update:

Just finished printing a pcb for this setup, gonna put it in a project box and fix it up all nice.

Here's some pix of the PCB after printing but before drilling and soldering.

<!-- m --><a class="postlink" href="http://blastwavelabs.com/Media/index.php?dir=Uploads/RcBoard/">http://blastwavelabs.com/Media/index.ph ... s/RcBoard/</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue November 18th, 2008 10:54:00 AM

i love rf hacks
hopefully get my damn license before years end

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed November 19th, 2008 02:02:02 PM

ITS COMPLETE, well mostly.

[http://www.youtube.com/watch?v=SjS5bn3ol4w](Here's a vid demo of a few of the functions.)

At the last minute it kicked me in the wang, I thought I burnt out the microcontroller but it turns out the compiler I was using was just spewing out bad hex code, what a relief! <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat January 31st, 2009 10:39:36 PM

That was pretty awesome.  I haven't a fucking clue how you did that though.   <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->  Too bad the FCC might come after you if you transmitted for too long.  The mind wanders with possibilities.
