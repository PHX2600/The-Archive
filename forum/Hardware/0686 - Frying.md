## Frying
Posted by **Valveritas** on Mon December 1st, 2008 11:52:56 PM

:)

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon December 1st, 2008 11:57:27 PM

D:

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue December 2nd, 2008 03:02:44 PM

what output did you use on your amp?

my crate amp has a lineout which i learned the hard way is to be used a preamp
not a direct line feed to something containing its own pre amp like a sound card
would prolly have and that much amp signal would toast most smaller electronics

bet it sound cool for a bit though

--------------------------------------------------------------------------------

Posted by **Valveritas** on Tue December 2nd, 2008 03:21:05 PM

Well, first I used the Stereo-Out ... which only fried in partially. Then I
later I looked at my amp manual, and read about how I could hook to external
speakers using the 70RMS jacks, which normally plug into the speakers that come
with the amp.   So I did that...  :roll:

I read a story earlier about someone using their line-out on their amp going
into the line-in in their sound card, which fried it.  Apparently this is
somewhat common.

So I bought a new sound card online.

Still don't know know how to properly hook my amp into my sound card, to do
recording though...without destroying it anyway.

In the event I learn more... I'll post it right here!

:cry:

--------------------------------------------------------------------------------

Posted by **Ugly** on Tue December 2nd, 2008 04:20:38 PM

Using the "Stereo Line Out" jack on the back of the amp with your line-in on the
soundcard should not fry anything. Line level has very well established voltage,
current and impedance specifications. If that is happening, it could indicate a
significant issue with your amp and you may want to stop using it in general. As
for why the speaker out fried your card, let's do the math:

Your amp is rated for 140 watts total (I'm guessing it's stereo at 70 watts per
channel)

The manual for that amp says that it will push 100 watts into a 4 Ohm speaker
load. Wattage is Voltage * Current (P=E*I)and Voltage is just Current *
Resistance (E=IR) so wattage can be found as P=(E*I)*I or P=I^2*R

We know Power (P) is 100 watts and Resistance (R) is 4 Ohms, so we can
substitute those and determine the current being pushed. 100=I^2*4 or 25=I^2

Basically, at full power into a 4 ohm load, the amp is pushing out 5 amps of
current. Now, knowing that it's 100 watts at 5 amps, we can tell that the
voltage is 20 volts.

Now, some things to consider: sound cards typically work in the range of
microwatts to miliwatts on the inputs. You can take the output from a guitar's
magnetic or piezoelectric pick-ups and run it directly into your sound card but
it will be fairly quiet. Having looked at the output from both of those types of
pick-ups on an oscilloscope, I can tell you that those max out at about 1 volt
peak- to-peak and put out microamps of current. While the input to your
soundcard is probably a higher impedance than a 4 ohm speaker load, when you're
trying to push a thousand to a million times as much power into it, something is
going to give.

Now, if you want to tap off audio from the high power output of your amp, you'll
need to make what is called a hotplate. It's basically a group of high wattage
resistors that total to near what your preferred speaker load is. They can be
bought at fry's electronics. They're white ceramic and usually rated for 5 to 50
watts each. Sometimes the selection is fairly limited and you may end up having
to get several different values to put together in series. If you need help
picking appropriate ones and configuring them, let me know. Just remember that
most speakers are not the exact impedance they say, especially at different
frequencies - so close is good enough as long as it's a high enough total
wattage.

Once you've built that dummy load, you'll need to put a voltage divider in
parallel with it. Just a ballpark, but I'd imagine a 4k potentiometer should be
good enough for what you're doing. Even at full power, it would only pass 5
milliamps of current at about 20 volts so it would only need to dissipate 1/10th
of a watt of power in the worst case. Hook it up with the full resistance legs
on opposites sides of the dummy load. Your signal will be the voltage difference
between one side of the dummy load and the wiper pin.

When setting your levels, start with the amp turned all the way down for it's
volume, your pot wiper turned all the way toward the pin you're using for your
signal input and the levels on your soundcard up where you want them. Start
putting out audio from your amp and then slowly turn the pot wiper. If you reach
the end of it's movement before you get the level you want, turn it all the way
back and then turn your amplifier up a little. Repeat these 2 steps until you
get the sound level you're looking for. Keep in mind that the lower you run the
amp the less power you'll be wasting.

I've build a system like this before for testing tube amps. If I can get there,
I'll head over to the meeting with it to show anyone who's interested.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Tue December 2nd, 2008 06:08:58 PM

Very thorough explanation Ugly. I don't understand electronics theory so well,
but this was very interesting.

I'm pretty sure my amp is UNSAFE at this point, as I think it was responsible
for destroying an old stereo system of time as well. I had plugged into the aux.
Eventually it died.   The amp was a display model when I originally bought it,
and I've had it repaired before.

Some [dumb] questions, if you don't mind:

I'm afraid I don't understand this part of your math:  P=I^2 Power = Current to
the second power?  Where did you get 25 for 25=I^2?

I don't see how you got 5 amps from that. :?

As far as the hotplate... gotta reboot right now...so can't finish my post.

--------------------------------------------------------------------------------

Posted by **Ugly** on Tue December 2nd, 2008 08:56:54 PM

You have 4 terms at work. Voltage (Either E or V), Current (I),
Resistance/Impedance (R or Omega) and Power (P or W).

Ohm's Law relates Current, Voltage and Resistance as E=I*R and Power through a
resistor is just Voltage times Current or P=I*E

Now you'll note that one of the terms in the power formula (E) is what ohm's law
is solved for. So we can substitute the other side of the Ohms Law equation in
for E - P=I*E becomes P=I*I*R or P=I^2*R

Substituting what we know we have 100=I^2*4

Divide both sides by 4 and we get 25=I^2

Take the square root of both sides and we get 5=I

Now we know P is 100, we know I is 5 and we know R is 4, the only one left is E
which we can get through solving the power formula  (100=5*E) Or though ohms law
(E=5*4)

If you've got anymore questions, feel free to throw them out as you need. If we
both make it to the meeting, perhaps I can take a look at the amp and see what
might be wrong. I know my friend's Crate amp kept frying a resistor on the
lineout so it could be a similar failure.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed December 3rd, 2008 02:44:23 PM

:idea Ahhh... ok.  Now I remember how to do some algebra. I'm so glad it
:actually has some uses from time to time... ;P

So I think I understand all that fairly well. Thanks!

Unfortunately I will not make the meeting as there's a work party on friday I
have to go to.  The amp is somewhat large to for carrying around anyway, though
I can imagine it might be amusing to see what kind of electronics it could fry.

An old friend of mine who plays regularly was telling me that he use to use the
headphone jack from a multi effects pedal before plugging into his sound card.
Nowadays though he uses a m-box mini with ProTools LE.  That's $378 though.

A hotplate sounds like a cheaper solution (assuming I could make it).

What do you think of this?
[op-amp circuit](http://www.facstaff.bucknell.edu/mastascu/eLessonsHtml/Labs/Lab6OpAmpIsoAmp.html)

--------------------------------------------------------------------------------

Posted by **Ugly** on Wed December 3rd, 2008 09:23:12 PM

That op-amp circuit is for taking output from your soundcard and putting it into
other things. Won't really help you.

I was at Fry's electronics tonight and they have 25 watt 15 ohm resistors for
$0.99 a piece. 4 of those in parallel would make a hotplate that runs about 3.75
ohms. They have 1, 2 and 4 Ohms as well but none were in stock.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed December 3rd, 2008 10:31:02 PM

Can you draw up a schematic for this? But keep in mind, other than a little
electronics in college and constructing a beige box with a switch to mute the
transmitter, and some other piddly stuff, I have minimal electronics skill.

--------------------------------------------------------------------------------

Posted by **Ugly** on Thu December 4th, 2008 07:42:06 PM

![](http://members.cox.net/timothy.russ/diagram.PNG)

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat December 6th, 2008 06:08:14 PM

Thanks.  But that doesn't fix my sound card. ;)

Here's a picture of it:

[![](http://img122.imageshack.us/img122/2600/1001881circlevd2.jpg)](http://img122.imageshack.us/my.php?image=1001881circlevd2.jpg)
[![](http://img122.imageshack.us/img122/1001881circlevd2.jpg/1/w1354.png)]http://g.imageshack.us/img122/1001881circlevd2.jpg/1/)

I circled the scorch marks.  It was an Audigy 2 ZS.

It's worth about $40 to $80 on the resell market if you think you can repair it.
I'll give it to you for $20.  <!-- s;) --><img
src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

Edit:

But more seriously, thanks.  I will have to try making the hotplate sometime.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sun January 18th, 2009 12:40:31 PM

I have an unfortunate update for you, and it gives me reason to believe your
previous schematic would not work right, because the cause of the problem may
have been incorrectly identified.  First of all, **I have lost another amp and
damaged another sound card.  **

I got a new amp in the mail the other day.  It was a Line 6 Spider III 75 watt.
This amp allows you to record with a headphone/Direct out jack.  Specifically,
the Line 6 website says " With POD® 2.0 style direct out on board, the best way
to record the Spider III will be to connect the headphone/Direct Out connector
to your mixer or I/O box."

My basic knowledge of electronics tells me that it is OK to connect a line-out,
or even a headphone out, to a line-in on a sound card as long as you don't jack
the volume too high.  With the Line 6 Spider III  completely OFF (but plugged
in), I connected a standard 1/8" stereo audio cable from the line-in on my
computer to the Line 6 headphone/Direct Out on the Line 6 Spider III.  As soon
as I did this, I heard a burst and a loud pop.

I unplugged the audio cable and turned the Line 6 Spider III on - it no longer
worked.   The sound card, per what typically happens, no longer has a working
line-in or mic input.  There is still audio playback, but it has noticeably
changed.

The Line 6 met a similar fate as my Crate.  The Crate still works, but only
because it had has two pre-amps (I only a made a connection with one of them).
The second pre-amp is  'blown'.

I am at a total loss as to what is going on here.  This is what bothers me the
most.   I have to  get another sound card, and another amp, but that's not quite
as bad as being ignorant as to what is happening here.

I've been trying to pinpoint the problem, but I can't.  I was wondering if my
computer is somehow putting out too much voltage.  But I've had this computer
since 2003 - nothing has ever failed on it, except a video card I bought for it.
It was replaced twice but the current one has lasted a couple of years. Same
model.  I don't have a voltage meter, but maybe I should get one and check.

The other bizarre thing, is that I've connected CD players, cassette players and
mp3 players to the line-in of the sound card and nothing has ever happened to
those devices or to the sound card.

I just can't wrap my head around what is going on here.  Apparently some surge
of voltage is coming out of nowhere when my sound card/computer connects with
any pre-amp circuit; even if it's OFF.  Incidentally, if it matters, the master
volume was also turned fully down at the time.

Something else I've noticed several times: if I'm holding the line-in audio
cable or touching the headphone jack on my speakers, and I then touch my guitar
strings or amplifier with my hand, I'll get a substantial shock, as if I was
jamming a fork into an outlet.  I'm pretty sure this is the same burst of
electricity that is damaging the amps and sound cards... but where is this
voltage coming from?   Shouldn't the line-in have very little or negligible
voltage, if any?   And if an amplifier is off shouldn't it also have very little
or negligible voltage?

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sun January 18th, 2009 05:12:28 PM

I thought there might be a problem with the outlets (e.g. lack of grounding) so
I decided to test them.  I bought a digital multimeter  and an outlet tester
from Home Depot today.  Both outlets are grounded - no problems - and delivering
120-121 VAC.

I guess that possibility is eliminated.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sun January 18th, 2009 07:57:47 PM

Curiously, I've come across several instance of people doing what I did on Yahoo
answers, and not having any problems.  One even reads in answer to a question on
recording:

> you cannot just plug the guitar straight into the Pc, well, you can, but it
> wills sound terrible.
>
> You need a Pre-Amp, somthing like a line6 POD or Behringer V-amp, there
> provide a preamp to give the sound abit of tone and depth, and also provide
> effects, distortion, tuner etc.....
>
> Simply plug the output of your pre-amp into your PC's souind card, and away
> you go.
>
> Software wise, it depends what you want to do? just record a little bit, maybe
> do a bit of multitracking? somthing like Steinberg wavelab will work.
>
> p.s. when you plug it into your sound card, dont plug it into your microphone
> socket as the impedence is different, and you could damage your soundcard, if
> you have a line in socket, use that, if not, use your mic, put make sure you
> turn down the volume

That's exactly what I did.  Yet, when I do it, everything blows up.

--------------------------------------------------------------------------------

Posted by **Ugly** on Wed January 28th, 2009 11:53:21 AM

There's nothing wrong with running a headphone, line-level or proper pre-amp
level into the mic or line-level input of your soundcard, My schematic was just
a way to get a signal of similar level from the much higher power speaker output
of an amp. It's possible that you may have a floating ground issue with the
amps, your computer or both. Are they on the same outlet/AC Circuit? Have you
checked for a voltage difference between the ground-cuff on the audio jack and
the ground of the outlet? Is there a voltage difference between a black wire
coming from your computer power supply and the ground of the outlet? In any
case, you may consider using an audio isolation transformer. They can be bought
at radioshack. It allows the AC audio signal to get through but won't let any DC
current from a voltage differential get through.

*Edit I didn't notice the part about getting shocked if you touch them
*simultaneously. It sounds like something isn't properly grounded even if the
*outlets are. That isolation transformer should make it work, but it's better to
*fix the problem itself. PM me if you'd like me to help you with that.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed January 28th, 2009 04:30:57 PM

shocks will touching strings is a ground issue

you may not find an issue using the meter

i had the same problem once when playing a show and the amps were on a different
ground than the mics so very time i stepped up to dobacking vocals i woudl get
shocked on my lips

but was your amp and computer plugged into the same outlet?

some time outlets dont share a a ground and that will cause this

if they were plugged into the same outlet then one of the devices has a ground
issue

if it was running thru a surge protector then it could have a ground issue

lots of variables with this problem

too badd it is too expensive to really get down to whats happening

buying a new card and amp a week would be killer on the pocket book

--------------------------------------------------------------------------------

Posted by **Ugly** on Wed January 28th, 2009 04:45:17 PM

It can be isolated using only a meter though it can take time. Hell, I'd be
willing to test it all as is just to get it isolated. Something has a floating
ground level.

I'm free tonight and have my multimeter handy if you want to nip this in the
bud.

*Edit*

Also, you may also consider just using a pedal to output to your computer. I
bought a cheap digitech at Guitar Center. Had something like 120 effects and a
headphone out. runs off a wall wart so it shouldn't have any problem connecting
to a device with a floating ground issue (Most older guitar amps included a
"lift" switch to disconnect the circuit from ground to remove hum)

--------------------------------------------------------------------------------

Posted by **Ugly** on Thu January 29th, 2009 12:25:09 PM

tell you what, plug a 3 pronged cord into each outlet (Computer cord or 3
pronged extension cord). Connect the ground ends and only the ground ends
together. See if you still get a shock when touching the guitar and a grounded
part of the computer at the same time. If not, you probably only have a ground
differential between outlets and not a floating ground in one of your devices.
You might even consider testing continuity from one ground to the other and
seeing if there's any AC or DC voltage difference between them.

I just got done grounding a test rack at work. A computer on one circuit is
connected to a serial device on another circuit. the computer is on the wood
desk top the device was on an ungrounded rack. When I got out of my seat to work
on them. If I touched the rack, nothing would happen but if I touched the serial
device, I'd kick a static discharge. I grounded the rack to the ground the
serial device is in, but when I'd discharge it would disrupt the serial
connection momentarily. I had to ground the computer to the rack as well before
it stopped happening.

In summation, common ground is good.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Thu January 29th, 2009 01:02:47 PM

Thanks guys.  I didn't get a chance to update this thread.  I called an
electrician to come out a few days back.   He checked all my cables, including
the surge protectors, and both outlets.

You had asked if the computer and amplifier were on different outlets - they
were.   He said there is absolutely nothing wrong with the house circuitry.   In
his view, the sound card and amp fried because one is primarily a chipped
circuit (i.e., the sound card) and the amp is primarily transistors, and that
they use completely different voltages.   Also, he said the manner in which I
was getting shocked was completely normal.  He said I was grounding myself.

I'm not sure if that all makes sense.  English wasn't his first language, so I
might have missed something, or he may have missed something.

Anyway, for $45 (home warranty charge) that's what I got from him.

> Have you checked for a voltage difference between the ground-cuff on the audio
> jack and the ground of the outlet? Is there a voltage difference between a
> black wire coming from your computer power supply and the ground of the
> outlet?

I have not checked these.  Still think I should?

> I'm free tonight and have my multimeter handy if you want to nip this in the
> bud.

You're welcome to come over and take a look.   At this point though, I'm unwilling to connect the sound card to the amp, lol.  Others have been recommending a "middle-man" circuit to control the voltages.  Even the electrician suggested that.   I think that was essentially your idea as well, by building something.


> Also, you may also consider just using a pedal to output to your computer.

This has been proposed to me as well. This is probably really paranoid, but at
this point I feel I almost need a separate setup just in case something goes
wrong.   Like a cheap amp, a cheap sound card, et cetera.

> tell you what, plug a 3 pronged cord into each outlet (Computer cord or 3
> pronged extension cord). Connect the ground ends and only the ground ends
> together.

Kind of amusing, because I was thinking of doing something just like that before
I called the electrician.  But I was concerned it might damage the outlets, or
lead to other problems.  Of course, I wasn't completely sure what I  would've
done with the results.

> In summation, common ground is good.

That may very well be what's going on here... a lack of common ground.  After
all, the outlets are really just grounded to themselves individually.  There is
no cable going back to the common ground like there are in newer houses.

And as you may have been saying,  I also suspect there is some DC AC
incompatibilities going on.  My guess would be the line-in cable is carrying
some DC, and the amp is carrying some AC (even when off) and when they come
together they don't get along too well.

--------------------------------------------------------------------------------

Posted by **Ugly** on Thu January 29th, 2009 08:51:01 PM

You getting shocked when touching the guitar and a grounded part of the machine
is *not* normal. All of the electric guitars I've torn down, have soldered the
lead from the ground cuff of the audio plug onto metal that is common to the
strings, grounding them. Usually the ground pin of each outlet/circuit should be
at the same potential, giving no voltage to produce a shock. So either those are
at different potentials (which would be visible as voltage measured with a
multimeter between ground pins) or the grounded part of one device - probably
the computer, but no garauntee - is not actually grounded and is building a
charge then dumping it through the ground connection to the other device.

If the multimeter doesn't show a significant voltage between the ground pins
alone, that indicates a floating ground problem in a device on one of the
circuits. If it shocked you as significantly as you indicated, you're probably
looking at at least 30V if not more. PM me and we can setup a time for me to
stop by.
