## Top my weekend
Posted by **Automated Penguin** on Sun October 17th, 2010 06:19:10 PM

Weekend hacker activities plz.

Tore myself away from Minecraft long enough to do this:

<!-- m --><a class="postlink" href="http://www.youtube.com/user/Penguin2600?feature=mhum#p/a/u/0/3R9FWn2AhJA">http://www.youtube.com/user/Penguin2600 ... R9FWn2AhJA</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Sun October 17th, 2010 11:56:10 PM

The stuff you do blows my mind!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon October 18th, 2010 07:49:48 AM

This is the beginning of my graduate work at ASU

Still a long way to go before its really presentable.

So don't be too impressed yet!

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue October 19th, 2010 05:05:05 PM

looking good so far 
are you using the relay to control power to the lamp or to trigger the light switch?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue October 19th, 2010 05:46:52 PM

Controlling power to the lamp.

I didn't want to tear into the lamp also i wanted to make it more universal so I could plug in other things.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Tue October 19th, 2010 07:59:50 PM

<!-- s:shock: --><img src="{SMILIES_PATH}/icon_eek.gif" alt=":shock:" title="Shocked" /><!-- s:shock: -->

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Tue October 19th, 2010 08:24:46 PM

You know whats even more bad ass is that you can lock your doors, turn on your alarm, feed your pets, deter burglaries, or just about anything with android phones with this awesomeness. I know Iphone has had similar software/hardware for a while, but have yet to see it for android phones.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 20th, 2010 08:06:47 AM

[quote="ThatGuy":yje8p44n]You know whats even more bad ass is that you can lock your doors, turn on your alarm, feed your pets, deter burglaries, or just about anything with android phones with this awesomeness. I know Iphone has had similar software/hardware for a while, but have yet to see it for android phones.[/quote:yje8p44n]

Yeah its pretty open ended.

The External IO channels are digital and analog, and being connected to the web it could  send out email alerts or sms or whatever. It is even able to monitor Ethernet traffic promiscuously and save packet data to the SD card, or host web content from the SD card. I already did some servo control via a uart interface to the little pololu controller you can see in the vid,  that was pretty fun.

[quote="CultLeadr":yje8p44n]Good god. <!-- s:shock: --><img src="{SMILIES_PATH}/icon_eek.gif" alt=":shock:" title="Shocked" /><!-- s:shock: --> Can you cure a cataract with that? I sure hope so.[/quote:yje8p44n]

Haha is this a reference to all the monitors? or maybe the poor video quality? sorry about that.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed October 20th, 2010 10:51:49 AM

I was literally referring to a cataract... specifically mine, which is premature / genetic and
not induced by any external factors.  I'm jumping on the "you can do anything with this" bandwagon. <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 20th, 2010 12:46:12 PM

Oh well,

hmm... 


With a few added components...

Some precision encoders...

lasers...

I'll have to work it out a bit.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed October 20th, 2010 02:03:37 PM

lots of good possiblities with this how many i/o pins are there to use?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 20th, 2010 03:07:19 PM

There are 4 unused IO channels.

Two are capable of analog.

That doesn't seem like much but in reality its a ton as you could turn all 4 ports into high baud Serial connections and then multiplex out another 100 pins or whatever you need.

Also 2 more digital pins are being used to drive LED's for status indication, in a pinch you could tap those with some jumper wires.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed October 20th, 2010 04:41:13 PM

4 open ports is more than enough to do a lot specially with two analogue have you thought about a wifi version? and where did you get that bread board?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 20th, 2010 06:03:00 PM

[quote="TerrorDrone":3f6yjae8]4 open ports is more than enough to do a lot specially with two analogue have you thought about a wifi version? and where did you get that bread board?[/quote:3f6yjae8]

I think I got that one from <!-- m --><a class="postlink" href="http://www.goldmine-elec-products.com/products.asp?dept=1293">http://www.goldmine-elec-products.com/p ... ?dept=1293</a><!-- m -->

Electronic-Goldmine.

It's like an electronics reclamation yard except ONLINE, pretty cool.


Also yeah I did consider a wireless version but I was turned off by the price of current embedded transceivers.

Right now that ENTIRE BOARD only costs 20 bucks to make, a good bare bones wireless transceiver is 20-30 bucks all by itself.

So for now wired is the word.
