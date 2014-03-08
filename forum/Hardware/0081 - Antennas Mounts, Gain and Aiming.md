## Antennas: Mounts, Gain and Aiming
Posted by **Ugly** on Tue March 18th, 2008 05:57:51 PM

I haven't been slacking off (too much) since you all saw me last. I've built a
new mount and aiming system for my high gain dish antenna as well as stumbled
across information regarding "legal" antenna limits. First the new mount:

![](http://members.cox.net/timothy.russ/New%20Sight%20scaled.JPG)

Here you can see my nice Crosshair for aiming:

![](http://members.cox.net/timothy.russ/crosshairs.JPG)

As this antenna's gain drops by half (about 3db) when it's misaligned by 4
degrees, I worked out what spread that would translate to over the distance from
the peep sight at the rear of that frame to the  back of the dish itself. At
that distance, the 8 degree field of view is approximately the size of the
window in that paper CD holder I cannibalized. The whole thing is bolted to a
cymbal stand from my drum kit and the sighting frame was built from a small
hinge, thin square metal rod, zip ties and nylon bushings.

Around the same time I came across an explanation of allowed antenna gains and
transmission power for wifi. The power going into an antenna is limited to no
more than 30db. This is what many people refer to when they mention the 1 watt
limit for unlicensed transmission. When outputting 30db, this can be put into an
antenna of up to 6db, giving an effective radiated power of 4 Watts. If using an
omnidirectional antenna (which are usually omnidirectional in 2 dimensions
instead of all 3), increasing the antenna gain 1db requires that the input power
be reduced 1db. This means that the effective power will always be limited to
36db for an omnidirectional antenna. If the antenna is directional though,
confined in 2 dimensions instead of just 1 like an omnidirectional antenna, the
input power must only be dropped 1db for every 3db of antenna gain, as shown in
this fourmula:

    30db-(antenna_gain-6)/3=max_input_power

This means that, while the input will always be 30db or less, the limitation of
effective radiated power with directional antennas is one of practical antenna
size and cost. This dish is rated for 24db of gain. Were it an omnidirectional
antenna I would be limited to 12db input power and be stuck at 4 Watts effective
power. Being directional though, this gain allows me to input 24db for a total
effective power of 48db or 63 Watts. It is also important to note that you can
account for line losses when working out your input power. If your coax drops
2db off your transmitter signal power, you are allowed to increase your
transmitter output to make up the difference.

I was glad to find this out as I had thought previously that my use of these
antennas with netstumbler would put me above transmission limits when it
requested beacon responses from Access Points. Now I realize that I could
actually purchase 300mW (24.7db) wireless cards and still be within spec after
accounting for my coax losses.

Oh, and I finally got around to testing these over a long distance. Aiming my
dish from south mountain without that reticle, while my friend did the same from
sunnyslope, I was able to pull 3 bars of signal from his Airlink+ Wireless AP.
It's my hope that the accuracy afforded by this reticle will allow me to do much
better than that next time. Once we learn how to bypass the MAC level timing
restraints that are preventing successful frame transmission at that distance,
I'll get back to you guys.

--------------------------------------------------------------------------------

Posted by **nak** on Thu March 20th, 2008 10:43:36 AM

:D cool!

I saw a dish similar to that one at a ham fest for $50, I almost bought it...

My grandpa wasn't sure about the dish, just because the slates were so far apart
for 2.4ghz

but I had already built a sweet directional waveguide lol:

![](http://www.wetwarehacks.com/2600/cantenna.jpg)

It actually works pretty good, just to bring in the signal from my own router,
it is quite temperamental though.

Have you ever just stuck your card in monitor mode and sniffed for interesting
information?  I was thinking of writing a program to parse aim convos and just
sit on top of a mountain with an antenna.  Even without an antenna once you get
on top of a mountain you could pick up ~10 APs, a couple could even connect o.o

--------------------------------------------------------------------------------

Posted by **Ugly** on Fri March 21st, 2008 05:45:40 PM

I've got Warlinux running off a livecd on my HP laptop right now. This could be
the one thing that finally pushes me into actually doing something with linux;
the output from prismsniff just continually scrolls so I need to figure out how
to mount a device to save it to and pipe it to a file, preferably after running
it through a script to parse it a bit. I found out why my old prism card wasn't
working and got some new ones as well so I might throw ubuntu back on there and
see if Kismet will play nice now. I'm also drawing up schematics for a 3 axis
mount that will allow me to scan around a given area while logging orientation
data. If all goes well I can use that along with the locations of known networks
scraped from wigle.net to determine general locations of the new networks I
find. If things go really well, I might be able to make a panoramic photo with
the points mapped out on it, but laziness might stop that.

Hiking up on the mountain behind my office I was able to find about 1100
networks with netstumbler in about 10 minutes. With Kismet and more time (I was
there after hours and worried about getting gated in the park or ticketed) I'd
imagine I can find a lot more than that. Anyone interested in helping me hike
that gear up a mountain?

From
[this spot](http://maps.google.com/maps?f=q&hl=en&geocode=&q=33.36711,-111.979568&ie=UTF8&ll=33.367435,-111.979394&spn=0.008584,0.016608&t=h&z=16&iwloc=addr),
the only place you don't have visibility is the far back side of south mountain
and stuff across the valley behind other ranges.

Also, those dishes I have go for $50-60 new at a
[few places](http://www.hyperlinktech.com/web/hg2424g.php)

--------------------------------------------------------------------------------

Posted by **nak** on Sat March 22nd, 2008 01:54:08 AM

Wow, neat :D 1100 APs in 10 minutes, thats quite nice!

The mountain you were on is about half an hour south of where I live.  I'd be
interested if hiking the equipment up a mountain if the mountain wasn't that far
:P

--------------------------------------------------------------------------------

Posted by **Ugly** on Sun March 23rd, 2008 02:57:51 AM

well considering how much of the valley is hidden from view behind mountains,
I'd be willing to take it up on shaw butte as well. Is that a little closer to
you? If we're lucky the gate will be open and we can drive up.

If the hardware store is open I should be able to spend my otherwise wasted
Sunday building a functional 3-axis mount for my dish.

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Mon March 24th, 2008 02:02:05 AM

Dude, I am not entirely sure what you are doing but I can help you trek that
gear up there on a Saturday. Just PM me and I can make arrangements to meet you
somewhere around mid day, or after 12. It is only going to get hotter as the
days pass so I would assume sooner is better. Need not worry I will have space
for beer in my pack.
