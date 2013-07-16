## micro controllers
Posted by **TerrorDrone** on Wed September 17th, 2008 02:13:28 PM

any know of any good resources on programming and using microcontrollers?

--------------------------------------------------------------------------------

Posted by **nak** on Wed September 17th, 2008 04:45:50 PM

I know logic, penguin and lost (not sure if he lurks here anymore) are pretty experienced with microcontrollers.  I've played with the basic stamp, oopic, atmel and the microchip PIC a little... a mile wide and an inch deep!  I hear a lot of great things about arduino, if you just want to get into something that just works and has a fairly straight forward syntax the arduino seems like a good way to go... I haven't tried it myself, but would love to sometime!!

parallax does basic stamp and propeller chips
I haven't seen much on OOPIC anymore, I have an oopic book you are welcome to (sold the hardware on ebay)
atmel seems to be pretty widely used among hobbyists, ladyada has some good tutorials and a nice cheap programmer kit for atmels.  Atmel is the base for the arduino by the way!
Microchip's PIC has a great resource at piclist.com, I was learning the 12f629 assembly at one point which was pretty fun, maybe I should get back into that. 

so pick one and concentrate <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed September 17th, 2008 07:14:41 PM

I guess it sorta depends on which ones you wanna use, depending on what you select the programming is gonna vary, especially if you decide to use assembly.

I like using the PIC from microchip, pretty simple once you get setup and you can use Pic Basic for most stuff even driving servos and serial i/o. but eventually to use all the functions of any micro controller you usually need to touch ASM.

If I could i would probably always use the Propeller chip from Parallax.
When it comes down to it 13 dollars a chip vs 80 cents a chip usually ends up guiding me back to the PIC's

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Thu September 18th, 2008 11:29:16 AM

[quote=&quot;nak&quot;:33wbcuiy]I know logic, penguin and lost (not sure if he lurks here anymore) are pretty experienced with microcontrollers.  I've played with the basic stamp, oopic, atmel and the microchip PIC a little... a mile wide and an inch deep!  I hear a lot of great things about arduino, if you just want to get into something that just works and has a fairly straight forward syntax the arduino seems like a good way to go... I haven't tried it myself, but would love to sometime!!

parallax does basic stamp and propeller chips
I haven't seen much on OOPIC anymore, I have an oopic book you are welcome to (sold the hardware on ebay)
atmel seems to be pretty widely used among hobbyists, ladyada has some good tutorials and a nice cheap programmer kit for atmels.  Atmel is the base for the arduino by the way!
Microchip's PIC has a great resource at piclist.com, I was learning the 12f629 assembly at one point which was pretty fun, maybe I should get back into that. 

so pick one and concentrate <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->[/quote:33wbcuiy]
i have the ladyada kit and have done some led controlling with it 
i woudl defintley appearciate and literature you have that i can use

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri September 19th, 2008 03:50:05 PM

I've used the OOPIC, several flavors of basic stamps, propeller, and formally trained on the Motorola HC11 chip for assembly from Devry. Not to be a brand whore, but I would recommend parallax and the propeller for a couple of reasons. I would recommend parallax in general because of how easy it is to get started, their manuals are very easy to follow and has the beginner in mind, but it can get as advanced as you want it to as well. I recommend the propeller for the power. It's not as cheap as a straight PIC, but you can get the demo board for $20, I purchased several. It has 8 processors on the chip, 80 Mhz (overclockable), and is 32 bit. You can program it in a high level language, and assembly (I have been concentrating on the assembly). Just for fun, I soldered several LEDS on the board and tried the whole POV thing, from scratch, and it wasn't very hard. This small project was only to try to get more familiar with assembly for the propeller, which wasn't really as hard as it seemed.

I have said this before in another thread, but I will be presenting one of my projects at the next meeting, the project uses this chip. And I guarantee it looks much cooler than a POV project.

--------------------------------------------------------------------------------

Posted by **nak** on Fri September 19th, 2008 05:43:25 PM

[quote=&quot;TerrorDrone&quot;:36rbxjoy]
i have the ladyada kit and have done some led controlling with it 
[/quote:36rbxjoy]

Which ladyada kit? The tinyUSB ISP for atmel micros? Or the boarduino? or what?

The OOPIC book wouldn't help you unless you bought an OOPIC <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Fri September 19th, 2008 11:21:49 PM

While on the subject who can help me build a safe dialer like the ITL 2000? I am sort of looking to make a modified version for electronic safe locks. I would pay for all parts, and time I just need some help to program it and assemble it.

--------------------------------------------------------------------------------

Posted by **nak** on Sat September 20th, 2008 10:54:11 AM

That guy, that sounds fun.  The electronic safes use a keypad right? so you would just have to setup button pressers and something that tests the handle.

One problem I can think of is different sized keypads... I can't think of a solution to that right now.

The rotary safes work like locker combo locks right?

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sat September 20th, 2008 12:15:48 PM

[quote=&quot;nak&quot;:2yp1fe17][quote=&quot;TerrorDrone&quot;:2yp1fe17]
i have the ladyada kit and have done some led controlling with it 
[/quote:2yp1fe17]

Which ladyada kit? The tinyUSB ISP for atmel micros? Or the boarduino? or what?

The OOPIC book wouldn't help you unless you bought an OOPIC <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->[/quote:2yp1fe17]
i have the tinyusb right now but looking to to getting more stuff for bigger mc the oopic has gotten my attention as i have read alot of good stuff about it this a pretty new area for me i usally had a buddy back in the day do the ships for me and i just designed and gave him algorithms to use 

that_guy one if teh projects i have been looking at has been a keypad locking device

--------------------------------------------------------------------------------

Posted by **ThatGuy** on Sat September 20th, 2008 12:48:04 PM

[quote=&quot;nak&quot;:2yfor3j7]That guy, that sounds fun. The electronic safes use a keypad right? so you would just have to setup button pressers and something that tests the handle. One problem I can think of is different sized keypads... I can't think of a solution to that right now. The rotary safes work like locker combo locks right?[/quote:2yfor3j7] 

The Key pads are pretty much a standard size, there are really only a few different companies that make them S&amp;G, La Grad, and Kaba. The rest of the generic key pads are almost exact copies. There are a few exceptions of course but I wanted to focus on the round style. I also thought about making the plunger’s moveable to adapt. 

The dial safe locks work similar to a combo lock because they have a wheel pack, fence, and gate. I have never seen an auto dialer for the electronic key pad, so I thought that would be cool to try out. Although this method is not practical for business use and there are faster ways to gain entry. It would be covert entry and border line surreptitious because it would leave very little or no trace of tampering. 

On some of the more secure expensive units you can see a log of all entries made into the system and they even have the time and date. Almost all of the locks have a lockout feature when to many of the wrong codes are entered, but they usually have a little led light that indicates when the code is valid, invalid, and, or locked out. The more I think about it the more involved it sounds and it's probably why no one has ever marketed one. I am been drawing some plans, for the idea, but I still need to buy a few machines before I start milling parts for testing.

More to come on this but I will bring an electronic safe lock mounted next time I go to a meeting, so anyone interested in the project can see how involved it would be, and play with the lock. Maybe throw a few ideas around, and get a rough estimate on parts needed.
