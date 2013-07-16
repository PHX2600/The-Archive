## Phx2600 &quot;badge&quot; dreams
Posted by **Automated Penguin** on Mon September 7th, 2009 08:07:10 PM

(6:14:34 PM) Penguin: ok im thinking a small device which works stand alone or usb and it is wireless, if you push a button on the device it sends out a signal that pings any other devices arround it and they send back a reply so you can send out a ping and see if any of the others are nearby, but you can also plug it in via usb and use the device to transmit messages wirelessly to the other devices, words and text like an IM service or an out of band wireless network, interesting? not interesting? ideas?
(6:15:09 PM) Penguin:for the phx2600 &quot;badge&quot;
(6:16:09 PM) Penguin: im just tossing it arround
(6:16:12 PM) Penguin:in my head
(6:17:01 PM) PHLAK: And it uses WiFi?
(6:17:09 PM) Penguin: no
(6:17:14 PM) Penguin: narrow band AM
(6:17:34 PM) Penguin: 200 - 300 foot range prolly
(6:17:39 PM) PHLAK: Hmmm
(6:17:44 PM) PHLAK: Sounds cool
(6:17:47 PM) Penguin: enough so you could know if someone else was in the same talk as you
(6:17:50 PM) Penguin: by pushing a button
(6:18:19 PM) PHLAK: Will it have a display, or just like a light?
(6:18:29 PM) PHLAK: Oh
(6:18:32 PM) Penguin: I was thinking just an led or a piezo
(6:18:35 PM) Penguin: then if you USB it
(6:18:41 PM) PHLAK: So its basically a proximity sensor
(6:18:41 PM) Penguin: you can do more advanced stuff
(6:18:44 PM) Penguin: like that
(6:18:56 PM) PHLAK: I like it
(6:18:57 PM) Penguin: yeah that would be its main thing
(6:19:15 PM) PHLAK: Gonna put it on the phx2600 logo?
(6:19:15 PM) Penguin: you would know if you got &quot;pinged&quot;
(6:19:20 PM) Penguin: and the other dude would get a reply
(6:19:23 PM) PHLAK: Yeah
(6:19:24 PM) Penguin: knowing you were arround
(6:19:30 PM) PHLAK: Cool
(6:19:35 PM) Penguin: idk how small I could make it
(6:19:44 PM) Penguin: I could definately incorporate teh logo
(6:19:47 PM) PHLAK: what about
(6:19:54 PM) PHLAK: instead of a ping
(6:20:13 PM) PHLAK: you had an few LEDs that look like a signal bar
(6:20:24 PM) PHLAK: and it would light up based on distance
(6:20:29 PM) Penguin: hmmmm
(6:20:52 PM) Penguin: I would have to work out a way for it to detect signal strength
(6:20:58 PM) Penguin: which might be pretty hard
(6:21:03 PM) PHLAK: ok
(6:21:07 PM) Penguin: basically if youre running off a battery
(6:21:08 PM) PHLAK: maybe not then
(6:21:12 PM) Penguin: constantly sending out a signal
(6:21:14 PM) PHLAK: yeah
(6:21:15 PM) Penguin: would suck balls
(6:21:15 PM) PHLAK: true
(6:21:36 PM) Penguin: im just kicking it arround
(6:21:39 PM) Penguin: like in my head
(6:21:42 PM) Penguin: I think I can do that
(6:21:49 PM) Penguin: pretty successfully
(6:22:07 PM) Penguin: it would be about 2400 baud
(6:22:12 PM) Penguin: but pretty reliable 
(6:22:16 PM) Penguin: so you could send anything
(6:22:18 PM) Penguin: even files
(6:22:19 PM) Penguin: etc
(6:22:22 PM) Penguin: via usb
(6:22:34 PM) Penguin: just might be kinda slow
(6:22:56 PM) Penguin: 2400 baud is like 300 bytes/second
(6:23:09 PM) Penguin: but thats tons for like a message
(6:23:11 PM) Penguin: or text
(6:23:27 PM) Penguin: thats like 50 words a second
(6:23:39 PM) Penguin: if the average word is 5-6 characters long
(6:25:15 PM) Penguin: the components to make such a thing ma be prohibitive unless everyone really wants one
(6:25:37 PM) Penguin: you would be looking at about 20 dollars
(6:25:41 PM) Penguin: probably
(6:25:47 PM) Penguin: in parts
(6:26:34 PM) PHLAK: that's not too bad
(6:28:18 PM) Penguin: im thinking a transmitter reciever pair ~ 10 bucks minimum, a uC ~4 bucks, usb interface ~ 4 bucks, and other shit another 2-5 bucks

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon September 7th, 2009 09:08:01 PM

do able
complex but do able 
so what you pretty much want to build is a rf data network  
will it mass broadcast to every badge in range or do you want it to go only to specific badge

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon September 7th, 2009 10:03:13 PM

Honestly its totally doable you're right the only part I don't have 100% confidence in is what you just asked.

Basically you have like 5-20 of these things all occupying the same frequency, so collisions would become an issue and separating collisions from legit traffic becomes an issue and rebroadcasting in case of collisions becomes an issue. 

But yeah I think it would be a single frequency ad-hoc broadcast network basically.

But that doesn't mean each badge cant just have a unique ID to specifically address traffic to.

could be a lot of fun.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue September 8th, 2009 09:35:23 AM

A fix for interference and collsion would be to use a freq hop based on some constant such as syncing an internal clock to the forum time.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue September 8th, 2009 07:09:17 PM

[quote=&quot;TerrorDrone&quot;:gdov2awj]A fix for interference and collsion would be to use a freq hop based on some constant such as syncing an internal clock to the forum time.[/quote:gdov2awj]

LOL!  I'd use an ACTUAL time server for that (even though I do sync this server to a time server).

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue September 8th, 2009 08:35:35 PM

[quote=&quot;Terrordrone&quot;:2chz3man]Really couldn't figure out another constant we all have easy access to and figured time would be easiest to write algorithm for.[/quote:2chz3man]

But time is irrelevant and arbitrary, maaan...

--------------------------------------------------------------------------------

Posted by **dxh** on Wed September 9th, 2009 03:40:29 PM

Imma total hardware/rf noob, but why narrow band AM?  Is there an awesome advantage to it I'm unaware of?  I was thinking Using Xbee modules and using 802.13 zigbee communication would take care of the collision issues and such, but I'm, guessing that might make it more expensive?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed September 9th, 2009 04:24:10 PM

[quote=&quot;dxh&quot;:37gaeo3q]Imma total hardware/rf noob, but why narrow band AM?  Is there an awesome advantage to it I'm unaware of?  I was thinking Using Xbee modules and using 802.13 zigbee communication would take care of the collision issues and such, but I'm, guessing that might make it more expensive?[/quote:37gaeo3q]

yeah cost.
narrow band AM tx/rx pair: 9 bux
<!-- m --><a class="postlink" href="http://www.sparkfun.com/commerce/product_info.php?products_id=8946">http://www.sparkfun.com/commerce/produc ... ts_id=8946</a><!-- m -->
<!-- m --><a class="postlink" href="http://www.sparkfun.com/commerce/product_info.php?products_id=8949">http://www.sparkfun.com/commerce/produc ... ts_id=8949</a><!-- m -->

Cheapest Xbee Module: 23 bux
<!-- m --><a class="postlink" href="http://www.sparkfun.com/commerce/product_info.php?products_id=8664">http://www.sparkfun.com/commerce/produc ... ts_id=8664</a><!-- m -->

maybe worth it though, we will see.

*Edit*

There's also a pretty good chance I can make some thing similar to those AM transceivers for about 3 bucks a piece and not have to buy them at all.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed September 9th, 2009 08:00:56 PM

i think we have more than enough talent in this group to get this done
as for cost maybe a fundraiser Phx2600 bake sale anyone 
(yes there does need to be a sarcasm font)
i really dont thinkcollison would be a problem using a burst or freq hop pretty much eleminates that

--------------------------------------------------------------------------------

Posted by **Konshu** on Thu September 10th, 2009 11:32:31 AM

This actually sounds fairly sweet!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon January 3rd, 2011 07:20:37 AM

It Begins.

<!-- m --><a class="postlink" href="http://www.youtube.com/watch?v=2pPPmvdE-P4">http://www.youtube.com/watch?v=2pPPmvdE-P4</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Tue January 4th, 2011 11:06:59 PM

that is cool.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 7th, 2011 07:44:50 AM

Ok So Dang,

I have ordered enough PIC 18's to create 3 Prototype badges.

But I hit a snag.

The one pic18 that I have right now isn't receiving through its USART peripheral properly.

Or I'm &quot;doing it wrong&quot;

I'm using interupts to handle the transmit and receive buffers so I don't think its a timing issue. And I have spent 2 days fiddling with the config registers to no avail, so I turn to you my community! If anyone has experience with this sort of thing a friendly nudge in the right direction would be fantastico. 

I have posted my code so far below for your diligent review and consideration. Also a link to the doc's on the chip I'm using (18F45K20) and a link to a Microchip App Note about USART configs.


[code:r754vk3y]

//----------------------------------------------------------------------------
// Fuses
//----------------------------------------------------------------------------

#pragma config FOSC = INTIO67, FCMEN = OFF, IESO = OFF                      // CONFIG1H
#pragma config PWRT = OFF, BOREN = OFF, BORV = 30                           // CONFIG2L
#pragma config WDTEN = OFF, WDTPS = 32768                                   // CONFIG2H
#pragma config MCLRE = OFF, LPT1OSC = OFF, PBADEN = OFF, CCP2MX = PORTC      // CONFIG3H
#pragma config STVREN = ON, LVP = OFF, XINST = OFF                          // CONFIG4L
#pragma config CP0 = OFF, CP1 = OFF, CP2 = OFF, CP3 = OFF                   // CONFIG5L
#pragma config CPB = OFF, CPD = OFF                                         // CONFIG5H
#pragma config WRT0 = OFF, WRT1 = OFF, WRT2 = OFF, WRT3 = OFF               // CONFIG6L
#pragma config WRTB = OFF, WRTC = OFF, WRTD = OFF                           // CONFIG6H
#pragma config EBTR0 = OFF, EBTR1 = OFF, EBTR2 = OFF, EBTR3 = OFF           // CONFIG7L
#pragma config EBTRB = OFF                                                  // CONFIG7H


//----------------------------------------------------------------------------
// Includes
//----------------------------------------------------------------------------

#include &lt;p18f45k20&#46;h&gt;
#include &lt;delays&#46;h&gt;


//----------------------------------------------------------------------------
// Prototypes
//----------------------------------------------------------------------------

void main (void);
void InitInterupts(void);
void InitUSART(void);
void InterruptHandlerHigh (void);


//----------------------------------------------------------------------------
// Main routines
//----------------------------------------------------------------------------

unsigned char txCount=0x00;

void main ()
{
    //Setup Osc
    OSCCON = 0x70;          // IRCFx = 111 (16 MHz)
    OSCTUNEbits&#46;PLLEN = 0;  // x4 PLL NOT enabled = 16x4 = 64MHz

    //Setup IO
    TRISD = 0x00;     // PORTD All Output
    TRISC = 0x00;  // PORTC All Output RxPin Input
    TRISCbits&#46;TRISC6=1; //Configure for USART
    TRISCbits&#46;TRISC7=1; //Configure for USART
   
    LATD=0xFF;
   
    // No Analog
    ANSEL=0x00;
    ANSELH=0x00;

    InitInterupts();
    InitUSART();

    while (1) {
        LATDbits&#46;LATD7=~LATDbits&#46;LATD7;
        Delay10KTCYx(160);    // Delay 160 x 10000 = 16,000,000 cycles; 1s @ 16MHz
    }

}

void InitInterupts (){
    //Setup Interupts
    RCON = 0x9c;                  //Enable Priority Levels
    INTCON = 0x80;                //Enable High Priority Interupts
    PIE1 = 0x30;                  //Enable TX and RX interupts
    IPR1=0x30;                    //High priority TX and RX interupts
}

void InitUSART (){
    //Init USART
    BAUDCONbits&#46;DTRXP=0; // Non inverted RX
    BAUDCONbits&#46;CKTXP=0; // Non inverted TX
    BAUDCONbits&#46;BRG16=0; // 8 bit baud rate
    TXSTAbits&#46;BRGH=0;      //Low Speed
    SPBRG=103;             //2400 Baud
    TXSTAbits&#46;SYNC=0;    // Asynchronus
    TXSTAbits&#46;TXEN=1;    // Transmit Enable
    RCSTAbits&#46;SPEN=1;    // Serial Port Enable
    RCSTAbits&#46;CREN=1;    // Recieve Enable

}

//----------------------------------------------------------------------------
// High priority interrupt vector
//----------------------------------------------------------------------------

#pragma code InterruptVectorHigh = 0x08
void InterruptVectorHigh (void) {
    _asm
        goto InterruptHandlerHigh //jump to interrupt routine
    _endasm
}

//----------------------------------------------------------------------------
//High priority interrupt routine
//----------------------------------------------------------------------------

#pragma code
#pragma interrupt InterruptHandlerHigh

void InterruptHandlerHigh () {

    if (PIR1bits&#46;RCIF) { //Check for RX Buffer Ready Flag                                  
        LATD=RCREG;       
    }

    if (PIR1bits&#46;TXIF) { //Check for TX Buffer Ready Flag   
        TXREG = txCount;
        txCount++;
    }

}

//----------------------------------------------------------------------------

[/code:r754vk3y]

USART App Note:
[url:r754vk3y]http&#58;//ww1&#46;microchip&#46;com/downloads/en/AppNotes/00774a&#46;pdf[/url:r754vk3y]

18F45K20 Data Sheet:
[url:r754vk3y]http&#58;//ww1&#46;microchip&#46;com/downloads/en/DeviceDoc/41303G&#46;pdf[/url:r754vk3y]

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri January 7th, 2011 02:16:35 PM

so it is transmitting correctly though?
Interesting when I get home after work tonight I'll give it a go.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 7th, 2011 02:35:40 PM

Transmit works like a dream,

I have it set up to interrupt as soon as the xmit buffer has space for the next character so it should be producing a perfectly continuous transmission.

I don't have a logic analyser though so I cant confirm.

I have used a serial LCD to receive the transmissions though and it does display correctly, so the transmissions are definitely within tolerances at 2400 baud.

EDIT:

I'll also be bringing my dev setup to the meeting tonight in case you'll be there.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri January 7th, 2011 06:56:17 PM

not making the meeting the wife is at work till 1930 and don't want to bring kids along with me.
this is interesting as in asynchronous should transmit and receive on the same pin after i get the lil ones to bed I'm going drag out the pic dev kit and see what happens if i use your code

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 7th, 2011 09:31:47 PM

Sweet!

On my pic xmit is c6 and rx is c7 separate pins so idk prolly take a look at that data sheet

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sat January 8th, 2011 12:13:34 PM

[img:1jw66hy6]http&#58;//forum&#46;ntreev&#46;net/grandchase/cfs-filesystemfile&#46;ashx/__key/CommunityServer&#46;Discussions&#46;Components&#46;Files/26/8156&#46;rage_5F00_face&#46;jpg[/img:1jw66hy6]

Found a microscopic solder bridge between RC7 and RD4, problem solved.

there goes 8 hours of my life.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sun January 9th, 2011 11:32:36 AM

oh that sucks had it happen to me a few times.
thought something was strange because I had it working over here with your code

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun January 9th, 2011 02:07:09 PM

Really on what hardware?

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sun January 9th, 2011 03:05:27 PM

global star stx2 something i working on for work which was there and on setup on the bread board already so just switch mcu and and was able to receive and transmit

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun January 9th, 2011 04:11:47 PM

yeah what MCU?

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Sun January 9th, 2011 10:46:10 PM

TI MSP430 is what I'm currently using for the prototype

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon January 10th, 2011 09:48:48 AM

You got my code running on a TI chip?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue January 11th, 2011 04:05:35 PM

UPDATE:

Chips just arrived from today from microchip so I can start experimenting with the USB interface once I design a dev board for these beauties

Pics, It did happen:

[img:ybk9qcg4]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0081%20%28Small%29&#46;JPG[/img:ybk9qcg4]

[img:ybk9qcg4]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0082%20%28Small%29&#46;JPG[/img:ybk9qcg4]

[img:ybk9qcg4]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0085%20%28Small%29&#46;JPG[/img:ybk9qcg4]

So I have the wireless interface working, I can send and receive data successfully , I now have the chips that have integrated USB so I will be working on that soon to facilitate the PC to wireless interface.

But I need your input, what else would you like to see on this device besides a wireless transceiver, we can add LED's that sync when the devices are in range of each other, we can have a button that does a &quot;ping&quot; broadcast to all the badges in range, the sky is the limit (and price and battery life) so whats it gonna be, I'm ready to go here, give me your input!

Also I would love to make this a community effort instead of a ME effort so if you have something you want to contribute or some resources we could use that would be great!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue January 11th, 2011 05:46:03 PM

Also here's a list of the uC's i was considering using, I ordered 3 of each for testing.
						
Product	        Documents
18F44J50 	[url:92agneta]http&#58;//www&#46;microchip&#46;com/stellent/idcplg?IdcService=SS_GET_PAGE&amp;nodeId=1335&amp;dDocName=en534038[/url:92agneta]
18F4550 	[url:92agneta]http&#58;//www&#46;microchip&#46;com/stellent/idcplg?IdcService=SS_GET_PAGE&amp;nodeId=1335&amp;dDocName=en010300[/url:92agneta]
18F46J53 	[url:92agneta]http&#58;//www&#46;microchip&#46;com/stellent/idcplg?IdcService=SS_GET_PAGE&amp;nodeId=1335&amp;dDocName=en54869[/url:92agneta]

They are all fairly similar and all in the same price range, only different in number and type of peripheral range as well as voltage tolerances.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri January 14th, 2011 06:29:39 PM

I have some of these I'm not using right now if you can use them 
<!-- m --><a class="postlink" href="http://focus.ti.com/lit/ds/symlink/tusb1105.pdf">http://focus.ti.com/lit/ds/symlink/tusb1105.pdf</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sat January 15th, 2011 08:50:17 PM

Thanks for the offer but I'm pretty set on the PIC.

Here's some pics of the breakout boards I made today to start playing with the new high end procs.

[img:1x5q7unu]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0088%20%28Small%29&#46;JPG[/img:1x5q7unu]

The traces are 8 mil and the text is 5, fucking smalllll.

1mil = 1/1000inch

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sat January 15th, 2011 09:32:34 PM

More pics of the breakouts with component test fit.

Drilling and soldering will have to wait till tomorrow, getting late.


[img:r4u34bks]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0090%20%28Small%29&#46;JPG[/img:r4u34bks]

[img:r4u34bks]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0091%20%28Small%29&#46;JPG[/img:r4u34bks]

--------------------------------------------------------------------------------

Posted by **Rax** on Sat January 15th, 2011 10:40:52 PM

I notice the subtle placement of the &quot;69&quot; in that picture (on the silver quarter)!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun January 16th, 2011 10:54:25 AM

[quote=&quot;Rax&quot;:14gxmuii]I notice the subtle placement of the &quot;69&quot; in that picture (on the silver quarter)![/quote:14gxmuii]

Rax you dirty old man.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon January 17th, 2011 01:23:44 PM

Tentacles.

[img:36p1s3j4]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0092%20%28Small%29&#46;JPG[/img:36p1s3j4]

[img:36p1s3j4]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0093%20%28Small%29&#46;JPG[/img:36p1s3j4]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon January 17th, 2011 06:07:20 PM

DERP

Cant get the pic to talk to me.

Powered all the correct pins got the VCAP setup, pulled up MCLR.

Wont even give me its device ID.

Son of a.

Well there's always tomorrow.

--------------------------------------------------------------------------------

Posted by **nak** on Tue January 18th, 2011 06:10:26 PM

Uh, did I ever tell you that what you do is incredibly sexy to part of my brain meat penguin.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu January 20th, 2011 08:54:55 PM

[quote=&quot;nak&quot;:227h5sll]Uh, did I ever tell you that what you do is incredibly sexy to part of my brain meat penguin.[/quote:227h5sll]

My Life Is Validated.

On another note I am switching to the 18F4550 because I cant get any of the J series to program.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue January 25th, 2011 08:01:57 PM

Update:

New breakout boards and working USB Functionality.

Pics or it didn't happen...

Etching Setup
[img:36t34hjg]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0096%20%28Small%29&#46;JPG[/img:36t34hjg]

New Breakouts
[img:36t34hjg]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0097%20%28Small%29&#46;JPG[/img:36t34hjg]

 Data sheets, data sheets everywhere.
[img:36t34hjg]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0102%20%28Small%29&#46;JPG[/img:36t34hjg]

&quot;Prototype aggressively&quot;.
[img:36t34hjg]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/JUNK/dcbadge/IMG_0104%20%28Small%29&#46;JPG[/img:36t34hjg]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon February 14th, 2011 01:55:55 PM

Update:

<!-- m --><a class="postlink" href="http://www.youtube.com/watch?v=n0NlKOL8xY8">http://www.youtube.com/watch?v=n0NlKOL8xY8</a><!-- m -->

Usb working.

Wireless working.

Just need to polish it all up and start producing devices.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu March 3rd, 2011 05:24:40 PM

Finalizing Board design. Might have something to show at the meet tomorrow.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon March 7th, 2011 08:19:47 PM

I can't wait to see even more of this, keep up the great work.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed April 20th, 2011 09:59:01 AM

[quote=&quot;XlogicX&quot;:3mpe7u0i]I can't wait to see even more of this, keep up the great work.[/quote:3mpe7u0i]

Is that some red-stone dust?

Are you a mine-crafter?????

If so we need to talk.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri April 29th, 2011 11:53:09 PM

Lol, yeah, I only started on beta 1.4 though, so I'm not old school. But me and a few friends from work are on a server. Redstone is what makes this game so unique...well, and everything else about it. But srsly, people have made ALU's and CPU's that function, in-game. But it's likely you knew about it. For everyone else, hard to explain what the appeal is about the game, just have to see for yourself.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue May 3rd, 2011 09:24:21 AM

Definitely worth playing if you haven't before, One of the most entertaining sandbox games I have played.

Dangerously addictive but super fun.

The red stone stuff is pretty epic, being able to define logic gates and build your own complex functions into the game is super fun.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed May 4th, 2011 03:07:53 AM

Yeah, so addictive that I have a kinked neck from mining obsidian for a whole day (as my computer setup is not all that ergonomic). But seriously, I got a physical injury from playing a video game. Well, we will definitely have to talk at the meeting this week.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun May 8th, 2011 07:47:16 PM

So I'm hardcore burnt out on this project just so everyone knows.

Progress was good but I have completely lost interest as I do some times.

I have started another project though... Some of you saw the kinect I had at the meet.

Here are some teaser pics of that project ramping up. I'll start a new thread for it later.

<!-- m --><a class="postlink" href="http://www.public.asu.edu/~cbock/JUNK/auton2/IMG_0208.JPG">http://www.public.asu.edu/~cbock/JUNK/a ... G_0208.JPG</a><!-- m -->

<!-- m --><a class="postlink" href="http://www.public.asu.edu/~cbock/JUNK/auton2/IMG_0209.JPG">http://www.public.asu.edu/~cbock/JUNK/a ... G_0209.JPG</a><!-- m -->

<!-- m --><a class="postlink" href="http://www.public.asu.edu/~cbock/JUNK/auton2/IMG_0212.JPG">http://www.public.asu.edu/~cbock/JUNK/a ... G_0212.JPG</a><!-- m -->

<!-- m --><a class="postlink" href="http://www.public.asu.edu/~cbock/JUNK/auton2/IMG_0214.JPG">http://www.public.asu.edu/~cbock/JUNK/a ... G_0214.JPG</a><!-- m -->
