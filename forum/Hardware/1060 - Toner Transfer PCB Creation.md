## Toner Transfer PCB Creation
Posted by **Automated Penguin** on Wed August 12th, 2009 10:52:34 AM

Hokay, so

I have been using this method for quite a while now and it works pretty dang good with your typical 0.1 inch spacings and pdip style packages.

However,

Now I am moving on, PDIP is insufficient and I need to be able to create pcb's with clearances and widths of 0.025 and 0.01 inches respectively, for SSOP and other surface mount devices.

for example the widely popular level shifter ftdi series (which is not available in dip packaging  <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( --> ) 
<!-- m --><a class="postlink" href="http://www.ftdichip.com/Documents/DataSheets/DS_FT232R_V204.pdf">http://www.ftdichip.com/Documents/DataS ... R_V204.pdf</a><!-- m -->

I have switched from standard paper to glossy and from glossy to magazine paper each attempt getting slightly better, but I can tell I'm missing something because often my 0.01 inch traces will transfer to the copper with gaps or bridging. I think its my sophisticated toner transfer apparatus ( clothes iron ).  I have seen many sites that suggest using a lamination device to apply consistent heat and pressure, has anyone tried this? Does it work better than an iron? 
any stories or experience would be appreciated.

TL;DR:
Does anyone have experience printing homemade pcb's for teeny tiny surface mount chips.

Thanks.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed August 12th, 2009 04:24:07 PM

I've used iron and heat gun never tried a laminator though sounds like it would work good due to the constant wife area of heat 
Another thing I do is se local pcb manufacturs into making me cheap or free boards by acting like a possible long term bulk client. It works sometimes.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed August 12th, 2009 08:21:58 PM

uibgfiubwgfuieraguwehohiogwewg

Dextrin coated paper, it works, bitches.

99% transfer, epic.

Im in love, see you in a month.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed August 12th, 2009 08:27:20 PM

good find will have to try it out

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri August 14th, 2009 08:26:12 AM

Penguin, if there is any way you can demo normal PCB etching at a meeting, I'm sure a lot of us would be grateful, I know I would. It's something I've never done yet, though I know the steps, it's still one of those things where it is easier to see than read. Not sure how practical a demo would be though, needing a printer handy and all. Just throwing the request out there though.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri August 14th, 2009 09:16:13 AM

Woah, hmm lets see...

Wouldn't be too bad to haul out the supplies, except the laser printer, but I have a little Samsung greyscale that's pretty reasonable to lug around.
Yeah I could probably do a demo some time.
I worry about the chemicals a bit and the delicious fumes it would be giving off, but I could probably minimize that.

Print your name on a board of copper? Two-Dollar.
WAIT, COME BACK, FOR YOU SPECIAL PRICE, ONLY ONE DOLLAR.

But once you see how cheap and easy it is to make your own boards you'll be amazed, it really opens you up to be able to make larger more permanent projects too.

Costs:
&gt;Copper clad, available in large amounts for under 5 dollars 
(<!-- m --><a class="postlink" href="http://www.goldmine-elec-products.com/products.asp?dept=1034">http://www.goldmine-elec-products.com/p ... ?dept=1034</a><!-- m -->)

&gt;Etchant, Radioshack or as their friends call them, &quot;The Shack&quot; (lol) sells ferric-chloride etchant which is pretty much the standard for about 10 dollars, and its reusable several times, so if you don't throw it away one bottle will probably last you years.(<!-- m --><a class="postlink" href="http://www.radioshack.com/product/index.jsp?productId=2102868">http://www.radioshack.com/product/index ... Id=2102868</a><!-- m -->)

&gt;Laser Glossy paper ~ 15 dollars a ream.

&gt;Laser printer, maybe free on craigs list? or borrow from a friend.

&gt;Any PCB cad design program, Eagle CAD or ExpressPCB are both good free options and I have used both depending on the situation.

&gt;Time and effort figuring out what works, do I use normal toner level or dark? How much heat do I need to transfer the toner to the copper? How much pressure? How do I separate the god damn paper now that the toner is bonded? Hopefully I can answer some of these.

So really if you go all out, assuming you can find or get laser printer access for free you're still looking at well under 100 bux to get started.


*EDIT*

Before I agree to do a presentation I want to hear that at least a few others would be interested and show up, I hate it when I bring out my A game for nothing. This started in my childhood but that's another story.

--------------------------------------------------------------------------------

Posted by **nak** on Fri August 14th, 2009 12:31:16 PM

I just ordered some copper clad from electronic goldmine, and I read about this method pretty recently: <!-- m --><a class="postlink" href="http://www.instructables.com/id/Sponge-Ferric-Chloride-Method-Etch-Circuit-Bo/">http://www.instructables.com/id/Sponge- ... ircuit-Bo/</a><!-- m -->

Too bad I already ordered 50 sheets of transparency, but I'm not ready to do the teeny packages yet, I'm just tired of protoboard!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri August 14th, 2009 12:37:50 PM

yeah the sponge method is great if your toner is transferred really well, 

it gets rid of the copper super fast but you risk losing some of your traces dragging the sponge across.

I usually just do the old fashioned 15 minute soak.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri August 14th, 2009 03:06:28 PM

I still use perf board for small circuits 
This thread making me want to stop buying pcb and start making my own again
We should do a whole meeting on hardware presentation ie soldering pcb making component functions oscope dmm and what not
*edit that's if anyone wants to see this stuff

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri August 14th, 2009 04:57:41 PM

[quote=&quot;TerrorDrone&quot;:2clwtw7q]We should do a whole meeting on hardware presentation ie soldering pcb making component functions oscope dmm and what not[/quote:2clwtw7q]

I wouldn't mind seeing that.  From my observations, if you make an effort to show it, and make an announcement that you're going to show it, there will always be at least a few interested people.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat August 15th, 2009 05:25:21 AM

I can bring my scope. I have been using it a lot lately. I have been doing a lot of assembly code working on PWM and PCM. If I have enough un-horrible code ready, I can present (code and how the sound waves look on the scope generated by the code).

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sat August 15th, 2009 08:51:09 AM

[quote=&quot;PHLAK&quot;:36eb6u9q] I wouldn't mind seeing that.  From my observations, if you make an effort to show it, and make an announcement that you're going to show it, there will always be at least a few interested people.[/quote:36eb6u9q]
looks like xlogic is gonna bring an oscope and pengiun can do diy pcb i'll bring dmm and random other things

--------------------------------------------------------------------------------

Posted by **nak** on Tue August 18th, 2009 09:07:32 PM

[img:2eo2u63g]http&#58;//www&#46;wetwarehacks&#46;com/2600/apc_pcb&#46;jpg[/img:2eo2u63g]
[img:2eo2u63g]http&#58;//www&#46;wetwarehacks&#46;com/2600/DSC00508&#46;JPG[/img:2eo2u63g]

I tried it with magazine paper, it's an atari punk console circuit... that ginger ale is good too!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue August 18th, 2009 09:15:46 PM

delicious
