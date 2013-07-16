## lolz at my confusing assembly comments
Posted by **XlogicX** on Fri September 18th, 2009 02:11:30 AM

So here are 4 lines of ASM (for propeller) code (with comments even):

[code:cngihta1]
mov       mx_adr1, par       'receive input parameter (from main memory)
add       mx_adr1, #84       'index to get correct input
rdlong    mx_val1, mx_adr1   'puts value (actually an address) in local variable
rdlong    mx_val1, mx_val1   'put value of the address of address in local workspace (lolz at the 
                              confusing)&#46;
[/code:cngihta1]

Uh, cool, that's not at all non-intuitive. I mean, it made sense at the time, but you know how that is...it doesn't make any sense at all 2 minutes later. So in my 'documentation comments, I had to write a more detailed explanation:

[code:cngihta1]
-The addressess that hold another address that hold the value sounds confusing, and I shouldn't
just leave it at lol'ing at in the comments below&#46; The indirectness allows me to be flexible&#46; This engine merely asks where the real data is located, instead of all of the extra overhead of passing several real values everywhere&#46; Other cores are going to be constantly updating the data in real time, so this engine only cares where that data currently is, and will then play with it&#46; Visuall analogy (painful)&#58;
       Addresses                         value in address
       1337 W&#46; HaK Dr&#46;                   Actual Sample chunk of data     (a value)
       1369 E&#46; Noob St&#46;                  1337 W&#46; HaK Dr&#46;                 (a value, however, of 
                                                                          an address)

                        This code grabs the address of the address (it gets the 1369 address), 
                        It puts the value of that address (1337 Dr&#46;) in a local variable, It 
                        then overwrites the value of the address from that local variable 
                        (1337 Dr&#46;) into the variable&#46; So now we have real data in a local 
                        workable variable (inderectly, but flexibly)
                        &#46;&#46;&#46;lol
[/code:cngihta1]

Looking back on the documentation comments, I'm lol'ing all over again. Yay comments.

One thing I have learned from experience with cryptic programming languages is (slightly unrelated):
If you don't understand what you just wrote, and you don't feel like making the comments understandable, then you better make absolutely sure that the code not only works perfectly, but that it is also modular (takes something in, spits something out), and that you will never have to 'fix' or 'improve' it. Although, you should still at least include comments of how and in what format it needs it's inputs, and how and what format it will spit it out.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri September 18th, 2009 09:01:06 AM

[quote=&quot;XlogicX&quot;:2ehw7sy7]
[code:2ehw7sy7]
rdlong    mx_val1, mx_adr1   'puts value (actually an address) in local variable
rdlong    mx_val1, mx_val1   'put value of the address of address in local workspace&#46;
[/code:2ehw7sy7]
[/quote:2ehw7sy7]

I had to read those two comments about 3 times before it even registered as proper english to me.

MOAR ASM.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Fri September 18th, 2009 01:06:13 PM

Hmm... we definitly see the twisted possibilities of pointing to a pointer, but what did YOU have in mind for something like this? (Other than intentional obfuscation.)

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri September 18th, 2009 09:21:56 PM

Mx_adr1 means the address of channel 1, to be mixed. I actually have 3 other similar routines (for 4 channels), and another different routine for the output.
There are a few reasons for being so indirect (intentional confusion not one of them in this case). The first thing to know is that I am actively controlling 3 processors in parallel. I have a bunch of wave tables with 16-bit audio, however, my PWM assembly engine needs 32-bit data.
Processor 1: Decides which wave shapes to select and which channels to decode. It then uncompresses the 16-bit audio data into a bunch of 32 bit ones (since I have 2 16-bit pieces packed into one 32-bit long each). When finished, it puts the uncompressed values in a special part of main memory (for the uncompressed channel data). This processor will perform this action whenever asked (by seeing the request on a custom flag register)
Processor2: This processor will look at all of the channel data and mix it into one channel; it will then put the mix into another part of memory. This processor constantly performs the operation (it doesn’t wait to be called; I’ll get back to this).
Processor 3: Times the different channels, regarding what frequency to play the wave shape, indexing through the PCM values, how long to play the shape, and actually playing the shape using PWM.
My code example was mostly referring to the 2nd processor, but every processor modifies the channel data. The mx_adr1 is just an address of the values on the channel data. Processor 1 will put the values there. Processor 2 mixes it, and Processor 3 is mostly just looking for the output on it.
Reasons for doing it this way. It requires less commands to access main memory, these type of commands take more clock cycles due to the semaphores required for multiple cores accessing the same data. Another convenience, is that the 2nd core is continuously updating the mix data, all it needs to know is where the current information should be (by indirect addressing), it doesn’t need to be passed a parameter every time it is called.

Why not a fixed address? because it changes, yeah the channel data starts at the same place, but there are 128 pieces to each wave, I don't leave it up to the 2nd core to figure that out when it doesn't need to, just let it know where the current piece is and it will crunch it.

So this may clear up your question Medicine Soup, or maybe it was hinting at other questions to ask, who knows. I’m not done with the code just yet though (I am almost finished, in debugging process). I’ll post code when I finish (and hopefully I do). It may be a week to a month (hopefully).

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Wed September 23rd, 2009 08:55:02 AM

That is so cool!
