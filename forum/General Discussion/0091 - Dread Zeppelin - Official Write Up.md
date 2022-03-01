## Dread Zeppelin - Official Write Up
Posted by **Ugly** on Mon April 7th, 2008 01:32:21 AM

I've written up a summary of my proposed build for the Kismet Blimp project. It can be viewed [http://www.hackerscouts.com/wiki/index.php/Main_Page](Here)

--------------------------------------------------------------------------------

Posted by **nak** on Fri May 30th, 2008 12:48:41 AM

*bump*
Any new progress on this? Sounds pretty interesting, a Defcon debut?

--------------------------------------------------------------------------------

Posted by **Ugly** on Fri May 30th, 2008 01:15:41 PM

It's looking a lot less likely. I've found new info on how balloons are classed by the FAA and it would seem that I would need to moor the balloon with multiple lines in a stationary location. Make it much more simple but less functional as well. It would provide me a way to do a high ground radio survey in a given area but for the amount of work, I'll just climb on stuff <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Sat May 31st, 2008 01:22:12 AM

Maybe you can build something like this intead.

[img:pt7i5ttl]http://www.rctoys.com/images/products/DF-SAVS_1.jpg[/img:pt7i5ttl]

The police use a similar model that is more heavy duty with a larger heavier camera and video glasses.

--------------------------------------------------------------------------------

Posted by **nak** on Sat May 31st, 2008 09:04:23 AM

Oh yeah those quad-copter things are awesome, Ive seen some videos from the [http://events.ccc.de/camp/2007/Home](CCC camp) I guess they are a popular thing there.

This might be a good page to look at for balloon stuff:
<!-- m --><a class="postlink" href="http://www.ansr.org/index.php?title=Main_Page">http://www.ansr.org/index.php?title=Main_Page</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Ugly** on Sat May 31st, 2008 05:45:16 PM

We're looking at needing to lift a lot more than just a camera. I would imagine we'd need to be able to lift 10 pounds at the bare minimum. I don't think it's reasonably going to happen for a free-flying platform.

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Sun June 1st, 2008 03:51:48 AM

Well I have a small 2300 Averatec if you need a small laptop to borrow for the blimp project to cut down on weight. I think it weighs about 4lbs.

--------------------------------------------------------------------------------

Posted by **Ugly** on Mon June 2nd, 2008 11:39:23 AM

As it stands, we're stuck doing a fully moored operation unless we can get the volume under 115ft^3, that gives us about 7 pounds of lift to play with. With that kind of load, we could do 1 directional antenna and a pocket pc. Since 4 antennas are required for proper counterweighting when rotated, it just doesn't seem like it's worthwhile.

We've gone from rotating, sectorized diversity coverage from a free flying vehicle to running one antenna straight up on a tether.

I think I'm going to fall back to my original project of a 3-axis mount for my parabolic dish. I'm going to create some positional sensors to read off the orientation of the antenna and dump that in with the data stream from kismet. That should allow me to triangulate the position of networks I pick up scanning from high ground.

--------------------------------------------------------------------------------

Posted by **Ugly** on Wed July 23rd, 2008 12:20:11 AM

Looks like someone implemented the idea, though on a smaller scale than I was thinking.
<http://defcon.org/html/defcon-16/dc-16-speakers.html#Hill>

I plan on checking that out.
