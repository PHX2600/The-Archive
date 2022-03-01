## More about microcontrollers: Rant
Posted by **XlogicX** on Fri December 11th, 2009 02:38:57 AM

I feel like such an elitist, but here it is; I don�t like the Arduino. Some of you may know what this is, and this is the only community I know of where I can rant about something so obscure. For those that haven�t heard of it, the Arduino is a low cost open source microcontroller (computer in a chip). With that description it sounds pretty cool. By low cost, you can buy an Arduino system for about $20-$30. The hardware is open source; so you can build your own and sell it (under a similar name) and not have to worry about royalties. And the development software is free and similar to C.

Why wouldn�t I like something like this? Too much hype for too little power, especially since I can find all of it�s other �open source� and inexpensive perks elsewhere.

Hardware � The most popular board; the Duemilanove, uses an Atmel ATmega168 chip as its processor. This thing is 8-bit, 20 Mhz, 4-16K of flash memory, 256-512 bytes of EEPROM, and 1K of SRAM.

Open Source � It�s a design based on a proprietary chip (ATmega), where the chip is still the brains of the system. The design only adds features like a voltage regulator, some I/O headers, an external clock, and a serial or USB programming interface.

For $20-$30, I can just by a propeller system. It has 8 processors in one chip that are all 32-bit and run at 80Mhz each. It has 32K of program memory, 32K of ROM, and 2K per processor. The company that makes the chip makes their development board schematics available, and you can also purchase 3rd party versions. So price is the same, it still has the same open source advantages (when the processor is proprietary in both cases), and the hardware smokes the Arduino (160 MIPS vs. 20 MIPS). To not sound like I�m completely partial to Parallax; you can get a microcontroller with similar specs to the Atmel from Microchip (the PIC chip) for around $1 (prepare to learn assembly for the good stuff, though that�s what I did for the propeller anyway; though you can use high level for all of them).


So the Arduino is geared to a different demographic, maybe that�s where the elitism starts to come in. It is aimed at the beginner. The language is very simple and the documentation is geared to someone that has never used electronics. In theory, I think this is really cool and I suppose you don�t need insane hardware to teach basic concepts. But in practice, I think there needs to be a segway into the more advanced. I have an RSS feed to hack-a-day, makezine, and instructables. There is a disproportionate amount of posts on how many different ways you can blink a stupid LEDs with an Arduino. It�s no surprise, when programming with such a high level language with such weak hardware. I get the feeling that when the beginner gets past the point of not knowing anything, they do not progress any farther. 

Arduino fanatics sound just as bad as Linux fanatics, except that Linux actually has something going for it. The hype isn�t centered around the system being a beginners chip. The hype is centered around how �powerful� it is, how it�s �open-source� (which makes it saint-like somehow), and how it is practically the cheapest thing around. I find this hype to be false, is what it comes down to for me. And I feel conflicted that I like MAKE magazine so much, but can�t stand how much the Arduino is promoted.

I�m sure there are those that would argue with me. I don�t mean to disrespect the creator of the Arduino, that Italian guy sounds pretty cool, its just the culture that seems to be surrounding it is annoying me. I feel like the old person complaining about kids these days  <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( --> .

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri December 11th, 2009 09:41:59 AM

I'm pretty sure I understand your position here,

For instance I started out with a parallax basic stamp (~80 bucks for the basic Dev board), which was totally cool and blinked led's like no other but one day I hit a wall, I was building a robot with several sensors and servos for locomotion and the basic stamp was so slow there was noticeable lag between sensor pulses and servo motion, anyway my first thought was simply &quot;oh ill just get ANOTHER basic stamp and run them in parallel&quot; which was super newb but all I knew at that time was p-basic so what else could I do? 

I ended up doing some research and investing in a JDM PIC programmer (less than 20 bucks) and a few beginner level chips( 40-80 cents each) but when they arrived I realized I didn't know anything about assembly, purchasing those chips and that programmer forced me to start learning PIC asm and step into the low level world because I knew that those chips had more power than that basic stamp could ever give me and cost one hundredth of the price.

Anyway I think the arduino is a great beginners platform and I'm happy its open source but when I see a project on hackaday or MAKE that uses 5 arduino boards to do something silly when it could have used a single PIC and some basic electronics knowledge it bothers me a lot because it seems like the person has failed the &quot;do the most with the least&quot; clause in the hacker ethic, it also seems like they probably aren't interested in whats actually happening in the chip at all which was the most fascinating part of learning assembly for me seeing the flipflops, multiplexers, ALU's, and buffers doing their thing to create a coherent and programmable device, such things excite me more than internet porn.

Tl;DR: I think your rant is probably justified.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri December 11th, 2009 09:46:05 PM

Do they do anything on hack a day anymore that isn't arduino based?

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri December 11th, 2009 11:58:31 PM

Thanks penguin, you touched a few points that I forgot to mention, some important ones:

I think people fail to appreciate the hardware that they are using. I read the whole &quot;Getting started with the Arduino&quot; book; it seems to have an animosity towards engineers. The way the author defines tinkering and hacking, and they way it is portrayed against engineering, I would have to say I identify myself as an engineer more than a hacker. However, I don't see things like the author of that book; I'm an engineer that hacks. I also see much more similarities between hackers and engineers.

As far as tinkering goes, its cools as a start, but a sad place to stop.

Ah, and I would unfortunately compare the basic stamp to the aurdiono, in power and simplicity. I say unfortunately because I really liked and extensively used the basic stamp. But in my case, it served it's purpose; it was a starting point (and I didn't stop there). And a note about the Basic Stamp, the BS2 a system designed around a PIC (some of them use Ubisoft processors too I think). The chip just adds some voltage regulators, memory, and such. In other words:
Atmel ATMega168 + peripheral hardware + easier programming language = Arduino
Microchip PIC16E57 + peripheral hardware + easier programming language -&gt; Basic Stamp

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon December 14th, 2009 02:21:43 PM

Ok, what kind of microcontroller [i:3i3xixwo]do[/i:3i3xixwo] you like? Is there one that works well for robotics that is still cheap, or are you guys just talking about retro-game microcontrollers? We guess it would depend on the intended use, so:

We are building an alcohol still. A microcontroller is needed to automate and optimize the various stages of the distillation process. This requires several IO devices: temperature sensors, pressure sensors, valve controls, etc. Cheap is good, but we also don't want to have to program the thing in BrainF**k. What kind of microcontroller is good for THAT sort of thing?

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon December 14th, 2009 02:25:33 PM

D'oh! Just saw [url=http://www.phx2600.org/forum/viewtopic&#46;php?f=11&amp;t=1170:34sas1g5]this thread[/url:34sas1g5] after posting here.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon December 14th, 2009 06:43:54 PM

[quote=&quot;Medicine Storm&quot;:3tl8tw6w]Ok, what kind of microcontroller [i:3tl8tw6w]do[/i:3tl8tw6w] you like? Is there one that works well for robotics that is still cheap, or are you guys just talking about retro-game microcontrollers? We guess it would depend on the intended use, so:

We are building an alcohol still. A microcontroller is needed to automate and optimize the various stages of the distillation process. This requires several IO devices: temperature sensors, pressure sensors, valve controls, etc. Cheap is good, but we also don't want to have to program the thing in BrainF**k. What kind of microcontroller is good for THAT sort of thing?[/quote:3tl8tw6w]
relevant to my interest as i i would liek to automate beer brewing process. 
IMHO Just about any micro controller should work for that 
arduino prolly be the easiest as there is some write ups using it in beer brewing floating around the net with source code that code prolly be easy to modify to exactly what you want but then again pic would work great to. As for propeller i haven't really worked with it out side of sumobots but i can't imagine it having any problems working. What it really comes down to is personnel preference. I have both arduino and pic programmers to flash chips that i can bring to a meeting so you can flash without having to purchase one if you don't want too.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon December 14th, 2009 07:30:33 PM

In reply to L0g1c 
I recently read an article about arduino and It gave me a better understanding of it. Arduino by design is meant to be a cheap easy board for students to begin learning about MC. I do agree its very over-hyped but lets hope it maintains it original ideas and gets some kids into hacking/making/engineering and they grow from there.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed December 16th, 2009 12:55:38 AM

Yeah, I would hope for it being the catalyst into a world of hacking. I am just afraid of an analogy of Arduino to normal microcontrollers as script kiddies are to hackers. In other words, script kiddies often call themselves hackers, Arduino users may think they have more ability then they actually do; they may not even realize that there is something more advanced out there.

I know I�m making myself sound pretty elitist, but it�s not even that, I actually would encourage all of the Arduino users to take it to the hacker level. It just seems like there are a lot of �LED blinkers� out there calling themselves robotics engineers. I wouldn�t even consider myself a robotics engineer. Heh, maybe I�m just saying people should know their place, and the Arduino is a false sense of elitism  <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> 
In response to Medicine Soup and general robotic and servo stuff; it depends on the hardware software trade-off. If the software capabilities are pretty weak (i.e. Arduino), then you will want hardware support; a servo/motor controller board that does all the PWM and other brainy stuff for you; you just tell it to jump and it asks how high (in a matter of speaking). If you don�t want to purchase extra hardware, or you like the challenge, then go with highly capable quickly clocked MC�s. Mostly, you�re looking for something fast enough to be able to do Pulse Width Modulation (since most servos respond to this kind of communication), fortunately, many MC�s have built in PWM functions.  The software end may not even be too advanced either; since most MC companies or communities have example software or object code already made for your motor needs.

However, I should say that my motor skillz are limited to only a few experiments. Although I intend to work with them more in the future.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed December 16th, 2009 09:29:30 AM

Yeah that's an interesting talking point also, talking about hardware vs software ability.

For instance most higher level languages (pbasic, pic-basic, arduino, etc.) implement software functions instead of taking advantage of the built in massively superior capabilities of the chip, for instance using p-basic on a 20mhz PIC you can &quot;bit bang&quot; like 9600 baud serial which is pretty ok but it takes up all your CPU time just to do that where you could be using the pic's built in UART hardware to do 15000+ baud no sweat and have it throw an interrupt or a flag when its done, that way you're not saturating your CPU with intensive software tasks, its the same for PWM, you can implement software PWM and take up a ton of cpu time or you can get a chip with Hardware PWM that can do it all for you.

Basically there's a lesson to be learned in implementing low level hardware functionality in your designs for simplicity and efficiency.

This is a fun thread.

P.S.
I showed my professor your audio driver on the prop, he went on a rant about how back in HIS day you had to write 1000 lines of assembly uphill in BOTH directions to get audio out of a machine and how we are spoiled now with high level object oriented languages. Then we got into a conversation about lisp, Then python, and then we went back to talking about micro-controllers and then he lit up his pipe and I hate pipe/cigarette smoke so I was like &quot;later bro&quot; and went and took my finals, yay.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Wed December 16th, 2009 12:13:11 PM

Yeah. We were thinking that might be the case. We like it easy when possible, but &quot;the challenge&quot; is preferable to not being able to get the pic to do what we want it to. Cheap is probably more important than easy as well. We have a budget of $0.00 to $40.00 for this, and we would prefer the entire budget was not eaten by the MC alone. This is mostly a scavanger project (which always seem more fun. MacGyvering something together out of &quot;garbage&quot; that is also productive just seems so awesome) so most of the parts are $0.00, though.

A quick MC is not that big a concern. Alcohol processing, from fruit to fuel, takes anywhere from 32 to 72 hours. If the MC takes a whole 60 seconds to determine that it needs to open a valve, that is well within the time accuracy constraints. Lots of memory is nice. We like doing lots of fancy pants code, but it's hard to fill almost any MC when you are doing it in assembly. Making hardware and IO easier and robust is definitely attractive. Any you could recommend that meet them's descriptions?

@Penguin: Your professor doesn't have the right to give the &quot;back in my day&quot; speech to you or anyone else that has posted on this topic! We have all done those same things the hard way on purpose and we all did just fine! For hackers, this IS back in the day.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed December 16th, 2009 12:20:12 PM

[quote=&quot;Medicine Storm&quot;:153em9o1]@Penguin: Your professor doesn't have the right to give the &quot;back in my day&quot; speech to you or anyone else that has posted on this topic! We have all done those same things the hard way on purpose and we all did just fine! For hackers, this IS back in the day.[/quote:153em9o1]

Right on, but he still hasn't graded my final yet so I'm not gonna contradict him.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed December 16th, 2009 08:32:08 PM

I love scavenge engineering. I had a real issue for a while where i tended to over engineer everything and now try to keep things done in the simplest fashion. I think that is the one thing I really like about the arduino is the fact that it is so simple. Butit is not the superman of MCs so  it definitely does not suit all my needs that why i have PIC and logic has got my interest in propeller since the nintendo controller bass guitar and so I am on my way to learning a new chip?
Since I'm old enough to remember when 56k was the bees knees does that mean i can do the back in my day thing?
epic thread btw!

--------------------------------------------------------------------------------

Posted by **XlogicX** on Thu December 17th, 2009 07:25:02 AM

So on the uphill both ways crap. There are really only a few luxuries that I had with the prop, some of which added complexity. The main luxury I had as regarding audio is that there is built in PWM hardware. But if you look at my change notes at the beginning, my first few versions didn�t even use that, because I didn�t even know it existed. I soft coded the PWM, and soft coding PWM is not that much code (it was maybe 10 lines or more).

I laugh at how �hard� audio is to electronically do. You can output convincing audio with just a 555 timer. (not perfect sine waves, but still, it�s sound none the less).

As far as another luxury that added complexity, I have 7 extra processing cores to fool with. Programming for multiple cores in assembly is nice to have around, but it adds many extra concepts to think about.

Which brings me to another point that you brought up about wasting soft resources on something like PWM when you can transfer it to hardware. The cool thing about the propeller is that it has so many cores. So say it didn�t have built in PWM hardware, I could just program one of the cores to do all of my PWM stuff and treat it like PWM hardware. But yes, without the extra cores, I also prefer to offload on hardware when possible and leave the �smart stuff� to the MC.

Yeah, beyond that, I�m not so sure I understand the professor�s arguments. It is still a RISC based assembly language with minor changes to the �old stuff.� Granted, the prop has no stack and no interrupts, but this doesn�t make anything easier, it makes you have to think differently about how you code, and actually adds a little more coding, but also gives more headroom for clever hacks and indirect addressing. There are even old MC�s and ASM instructions for divide, DIVIDE!!! You don�t have multiply or divide with the ASM on the prop, you make a subroutine with clever adds and shifts, or some custom hack.

Bah, now I�m all worked up.  <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **jargon** on Thu December 17th, 2009 06:58:11 PM

I will get back to You on an improved PWM method I came up with myself of the Reimann trapezidal sum. My method extrapolates by a quarter modulation rate the expanse above and below actual source signal. This results in a superior average signal area as the calculated integral of above/below source signal trend. This also results in superior replication of a signal even when using a variable sample rate.

This method of mine is solely for the intent of when the pulse-modulation frequency itself is also variable.

I will get back to this in a bit when I verify a bit more the proper terminology in-addition to coming up with a method to use variable pulse-modulation frequency implementations with your specific microcontroller rig.

The theoretical improvement to such a system therein is via the ability to ramp up or down modulation sampling rate to conserve drain surplus and/or deficiencies from logical gates for when using complex circuitry involving an abnormal load between cycles of multiple microcontrollers within both parallel and serial pipelines within a single unified circuit completion.

This is one of the main hurdles within quantum tunneling pipelines due to lack of an endlessly compounding voltage source.

As I stated, I will get back to you on this when I brush up on my terminology and study your specific microcontroller configuration and specifications in greater depth.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu December 17th, 2009 10:09:01 PM

Haha, I don't think his rant was meant to knock your stuff, I think he was just reminiscing about his past, he probably identifies with your struggles more than I let on in my previous post.

that's also a pretty good point you made  about the 8 cores, how you can use one or two to add hardware-like functions without sucking up all the chips time doing software stuff.

I would let my professor know about your passionate defense of your coding and architecture choice but at this point I'm pretty much hoping to never see him again, at least not for another year or so.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Thu December 17th, 2009 11:56:44 PM

@penguin: yeah, I wouldn't fret about it. and I guess the 'back in the good old days' context puts some perspective to it. 

@jargon: I'm a little bit confused at your ideas regarding the PWM stuff. We may be talking about different concepts. Don't worry about the terminology so much, concepts are fine. This is for you (and everyone else interested), so we can be on the same page here:
[quote:3xuc9v0e]
PWM 101:

PWM stands for Pulse Width Modulation. It is actually way simpler than it sounds. I�ll explain why it�s used, how it works, and how that would translate into code.

Why it�s used: Not all microcontrollers and hardware have analog capabilities; just digital I/O. That is a pretty big limit if you want to do anything like motor control, general signal processing, and also audio. Sure, you can add extra dedicated hardware to do this kind of stuff (a ADC or DAC), but what if you wanted analog signals on a single digital line with software tricks. PWM does just that.

How it works: Changes in voltage are not quantum, meaning that they are not instantaneous; it takes time (however small) to change from 5 volts to 0 volts (or whatever voltages used). This is exploited. For example, If I were to blast 5 volts then 0 volts back and forth for an equal amount of time, very, very, very quickly, a multi-meter would read it as 2.5 volts, especially if you have the right resistor-capacitor filter hooked up to the output (makes the voltage levels take even longer to change). If you had an LED hooked up to the output, you would see it half as bright as it would be with a constant �on� voltage.

To take it a step farther, what if you only had the 5 volts on for 10% of the cycle, and 0 volts for the other 90%? You may guess that you would have about half a volt, you would be right (assuming it is all cycled quickly enough). Seriously, that�s all there is too PWM; pulse the values at the correct �duty-cycle� and you will emulate an analog voltage using digital signals.

The Code: The code is really simple too. You must have a subroutine that keeps a pin HIGH, then turns it LOW. The routine must have a way of keeping track of timing separately for the HIGH and LOW, using delays or countdowns or whatnot. Beyond that, the only other thing you need is a way of translating your �analog value� to the HIGH and LOW timings and you�re good to go. That�s it. This is why it only takes a few lines of code. Not to say you don�t still need a quickly clocked MC though, remember, the cycle has to be going very fast for it to work.[/quote:3xuc9v0e]

So, even if you�ve found a more efficient way to do PWM, it�s almost trivial, because PWM stuff is so simple already. Again, don�t worry about getting terminology correct, I think the use of lingo will just muddy the discussion; talk in concepts and rough implementation as you can. To be more specific, I find it odd that you mention quantum tunneling pipelines for something that is already as dead simple as PWM already is. You mention variable frequency for PWM; the only way frequency is relevant is relating to increased quality, meaning that cycling the highs and lows at a slower rate will start to muddy your results, though, there is a certain point of a high frequency where you results at a higher frequency than that would not achieve any better results. My point is that I don�t see any relevance for a variable frequency, in order to make PWM better. The whole first paragraph of your explanation totally threw me off too, sounds like something complicated for sure�and complicated is not something that needs to come into PWM. But again, we may be talking about different things. Some advice, if you�re going to use terms such as Reimann trapezoidal sum or �endlessly compounding voltage source� (never ran into a problem like that with a 0-5V I/O pin), try defining them as well, or just refer to them in a more tangible way; in how it�s actually implemented. For example, I even used the word �quantum� in my PWM explanation (to make a point), however, I didn�t just leave it at a �smart� sounding buzz word. In the context of my explanation, quantum just meant an instantaneous change (this is not inaccurate), I also made a point that this is what I meant to say as well.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri December 18th, 2009 11:25:33 AM

Great defining of PWM but your math is off a multimeter read half cycles at RMS for an AC signal so it would read 3.535V for 5 and 0 for 0 and you would have a very fast bounce between the two( most likely faster than your meter could keep up)
but then again the device receiving the signal does read it as half voltage. I'm just ranting too.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 19th, 2009 12:54:39 AM

Actually, RMS wouldn�t apply to a PWM signal. RMS is a measurement of the �average� voltage of a sine wave (under the curve). There is moderate calculus used to derive the value under such an irregular curve such as a sine wave. However, PWM is just a �square-wave,� actually; it is more of a rectangular wave at most times. But you can literally use simple averaging math for these calculations. I have also verified the math from both my DMM and O-Scope.

WikiAnswers explains it slightly more elegantly than I though: <!-- m --><a class="postlink" href="http://wiki.answers.com/Q/What_are_the_peak_and_RMS_values_of_the_voltage_of_a_pulse-width-modulated_signal">http://wiki.answers.com/Q/What_are_the_ ... ted_signal</a><!-- m -->

The funny thing is I almost completely forgot about RMS from my AC classes, but I can assure you, if RMS came into the picture for PWM, I would have been having even more nightmares trying to code my audio driver, fortunately, the results (audio, and visually on the o-scope) were completely consistent with a simple average.

--------------------------------------------------------------------------------

Posted by **jargon** on Sat December 19th, 2009 04:45:54 AM

[quote=&quot;XlogicX&quot;:yv110dy2]Actually, RMS wouldn�t apply to a PWM signal. RMS is a measurement of the �average� voltage of a sine wave (under the curve). There is moderate calculus used to derive the value under such an irregular curve such as a sine wave. However, PWM is just a �square-wave,� actually; it is more of a rectangular wave at most times. But you can literally use simple averaging math for these calculations. I have also verified the math from both my DMM and O-Scope.

WikiAnswers explains it slightly more elegantly than I though: <!-- m --><a class="postlink" href="http://wiki.answers.com/Q/What_are_the_peak_and_RMS_values_of_the_voltage_of_a_pulse-width-modulated_signal">http://wiki.answers.com/Q/What_are_the_ ... ted_signal</a><!-- m -->

The funny thing is I almost completely forgot about RMS from my AC classes, but I can assure you, if RMS came into the picture for PWM, I would have been having even more nightmares trying to code my audio driver, fortunately, the results (audio, and visually on the o-scope) were completely consistent with a simple average.[/quote:yv110dy2]

My idea is just for greater fine tune control of the fall offs involved with the result as noticed when plotted.

By &quot;quantum tunneling&quot; I am just referring to systems in which there is very little loss of signal such as biologically embedded systems.

Also, you need an analog signal probe, not just a digital logic probe in-order to properly measure the result of pulse width modulation from exterior to the circuit.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sat December 19th, 2009 08:56:06 AM

ctually you are right and I am wrong I checked It last night with dmm and oscope and found the average voltage to display on dmm not rms. I stand corrected. I just never checked it before. Just always assumed it would read rms and the load always functioned correctly.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 19th, 2009 10:48:14 AM

@Jargon:
[quote:3lrx05l2]Also, you need an analog signal probe, not just a digital logic probe in-order to properly measure the result of pulse width modulation from exterior to the circuit.[/quote:3lrx05l2]
Absolutely correct. I used an O-scope for just about all measurements, fortunately, the O-scope is analog.

@TerrorDrone:
Lol, yeah, you actually caught me a little off guard with the RMS stuff. When I read you're post, I was rethinking if I had made a mistake or not. But then I thought about my actual results and realized that they were still quite consistent with conventional averages. So I did some research/review and discovered that RMS was mostly for sine waves. Just goes to show, you re-learn something every day  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sat December 19th, 2009 04:06:06 PM

@logic yeah i realized after writing i never tried to read a PWM with a dmm before always used an oscpoe. so look like a learned something new.
