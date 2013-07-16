## Hex Editing
Posted by **Valveritas** on Sun September 14th, 2008 03:37:26 PM

I'd like to get deeper into Hex Editing, and I was wondering if anyone can recommend any tutorials or have some experience in this area. I've not found much so far; most tutorials are geared toward editing a particular program or data file where the values are known, but I'd like to know more about seeking out and discovering unknown values.  Say, for example, you want to change a color in an app but have no idea where it is in the data file.  I did something like this today but the value of the location was known.

--------------------------------------------------------------------------------

Posted by **nak** on Sun September 14th, 2008 03:48:55 PM

OllyDBG give you the disassembly vs. raw hex, as long as the target is a win32 application.
From that you can get the memory address that needs to be altered and post instructions (or create a patching application) for the modification.  I've only really used a hex editor to add more bytes to the end of executable files and to mess up jpg files, etc.  OllyDBG takes those opcodes and gives you some idea of what is going on!!  If you want to post the target and what you want to do I could try and look at it, never really tried changing colors... mainly getting software registered <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sun September 14th, 2008 04:01:24 PM

I'd like to register software too.  Just anything I need to do fairly quickly on my own, when no crack or tool is available, but isn't a major project.  I'll try this OllyDBG.  I guess it makes sense that I wouldn't be able to identify much without it.  My understanding of hexadecimal and assembler is really poor, so if you can give me an example of something I could do to get started I'd appreciate it.   Maybe something you've done before, I could repeat.  As for myself on what I might want to do... hmm... well, there is the game I have installed right now (Metal Fatigue) that has all its keyboard assignments preset with no way to change them in program, and it also requires the CD to play.  I would think that the former at least would be something doable, if I could find where the values are stored.

Edit: Ugh, OllyDBG uses a small font.  Edit2: Nevermind, changed using OEM fixed font.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun September 14th, 2008 07:21:42 PM

<!-- m --><a class="postlink" href="http://www.tuts4you.com/download.php?list.17">http://www.tuts4you.com/download.php?list.17</a><!-- m -->

These are the tutorials I used getting started with Olly / reversing, they are pretty good and come with example stuff to work on while you watch.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sun September 14th, 2008 07:24:29 PM

Editing hex isn't really the hard part, it's only a handful of characters to edit. Obviously the hard part is understanding what it means, and this meaning will vary from application to application. If you want to modify an executable, assembly is essential, and very difficult to interpret on more complicated applications. You kind of have to know what to look for, I've only been able to do really simple stuff with that. Aside from applications is data, this varies very far from learning assembly, it really just depends on the format of the data. It can be really simple and even plain text-like, or it can be cryptic, but expect variance.

As far as hex editing, I just use notepad++. I've used it to enter that hex challenge on the back of a 2600 magazine several issues back. I spotted that the header identified an ID3 tag. So when I finished entering all the hex in, I saved it as an mp3. It actually played about a second of audio (meaningful audio, not just noise). This would be a great example of a data file, and the header is a very informative place to look, the rest is just data, and mistakes could even be made without it corrupting the file (though too many mistakes may make it sound wrong).

Either way, let us know what you learn. You'll probably find out more than I know, because I haven't played around a great deal with the type of adventures you are looking to go into.

--------------------------------------------------------------------------------

Posted by **opcode** on Mon September 15th, 2008 01:33:28 AM

If you're running Windows, I suggest Hexplorer ( <!-- m --><a class="postlink" href="http://artemis.wszib.edu.pl/~mdudek/">http://artemis.wszib.edu.pl/~mdudek/</a><!-- m --> ).  It is a free hex editor.

This also depends on what application you're running.  For example, if you are running a Windows based application using the Windows GUI window calls, see if you can take a screenshot of the running application.  Import that screenshot into an image manipulation program (mspaint, GIMP, Photoshop, PSP, etc) and use a color picker and select one of the pixels.  Write down the RGB values it shows you.

Open up your hex editor and do a 32-bit search for the RGB, which if I remember right as you read the bytes from left to right (ungrouped bytes), you should read the color as RGBA [Alpha if you're doing 32-bit colors].  Do a search for the color from the color picker.

As far as your keystrokes are concerned, find out through OllyDbg what Windows calls are being used for keypresses.  You could also use WinDASM (there is a free version, 8.9, but I can't find it at the moment [I managed to get the free version some years ago before you had to pay for it; I'll go look for it]).  WinDASM is excellent when looking for imported functions and which Windows libraries they are from.

Then go grab the key scan codes for the keyboard and match it up with how the call is made to Windows libraries (this will involve having to read assembly language from WinDASM).  Depending on the Windows library and version of Windows, you'll either see a push onto the stack and a CALL instruction, or a register load with a call to interrupt 0x41 (0x41 is common mostly for VB stuff to vbrun.dll).

Or are you inquiring this about Linux? (:  I have methods on that route as well. (:

--------------------------------------------------------------------------------

Posted by **Valveritas** on Mon September 15th, 2008 10:32:41 AM

Thanks Automated Penguin.  I'll be great if I can get the hang of this.  I've always been interested in this sort of activity.  Can't tell you how many times I've thought &quot;damn, if I only I could fix this program or change this&quot;.  

XlogicX:  I use notepad++ as well.  However, I think I may have discovered a limitation with the Hex Editor as it doesn't appear to show the offset of the byte you're looking at.  Perhaps there's a way to calculate this in your head, or something I've missed, but I don't know how.  I had to get Hex Workshop 5.1 to show me the offsets.  It also has a &quot;goto offset&quot; feature (either decimal or hex).   

BTW, as far as reading hex itself, I think the simplest explanation I found was in this article I read the other day:

[quote:10mgej70]A quick explanation of how to read hex code numbers.

0-9&amp;A-F = 0-9&amp;10-15 for each character. IE 3 = 3, B = 11, F = 15.

The 1st chararacter is multiplied by 16, and then added to the 2nd character to get the hex number.

Example -- Hex # D7.

D = 13, 7 = 7.

D x 16 = 13 x 16 = 208 + 7 = 215, or D7 to the hex code reader.

One more example.

Hex # 2E. 2 x 16 = 32 + E (14) = 46. [/quote:10mgej70]

As I understand it, mp3s have no real pattern of bytes.  Nice discovery!

I'm not really sure how far I will get in this direction.  I'm in the sort of mood, I feel like doing more than one thing at a time.  So  if this gets to be too much, I'll work on Flash or something.  <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

Opcode, that sounds like a great way to find colors.  But let me mention this: right now I'm looking at a saved game for Homeworld Catclysm (yes, another old game) which I had modified the other day to change the colors of the ships.  I made a guess as to where the values were based on the previous  game (Homeworld) as  I came across a walkthru that happened to mention what offset the values were stored at for ship color.  I just used those same offsets to find them in Cataclysm.   Of course, if the data structure had been different, I probably would've been screwed - but it worked.  Anyway... I'm looking at this saved game file, and in it is the RGB color I inserted before: 39A91F. But if I do a search for this hex sequence throughout the file, I get 8 matches.  So even if I know the RGB color, how would I know which sequence to modify?! Haha.  Of course in this case I know the location, but if I didn't, how would I narrow that down?  I think in any data file or program the chance of 3 distinct hex numbers popping up would have many instances.  
I get the same results with RGBA, or 39A91FFF (that is, 8 instances).

Thanks for the info on the keys.  I'm not quite sure I understand how to proceed with that.... probably have to come back to that later.

Oh, I ran MetalFatigue.exe with OllyDBG.  I couldn't figure out how to go back to OllyDBG after the program ran, as ALT-TAB wouldn't work.   I'm actually not sure what output window I should be paying attention to either once I return to OllyDBG, but I guess the tutorials will help me there.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Tue September 16th, 2008 09:19:12 PM

As far as reading hex goes, some context on the history of it may help (an the irony is that hex was introduced for readability).

When programming machine language and data in the olden days, one would have to do it in binary. A couple of bytes could look like this:
10110100110101000000010001101111

If I had to deal with that back in the day, I might break them up to look something like this:
1011_0100, 1101_0100, 0000_0100, 0110_1111
(commas separating bytes, _'s breaking each byte into nibbles).

Hex was just a tool to take this idea to the next step; a different representation of binary created for better readability, that's it. So the above binary could be written as:
B4 C4 04 6F
Less mistakes could be made with this code.

As far as the math example you had (and I will use your exact example), the binary representation should also show it's direct correlation (as it should).

Hex D7 in binary is 1101_0111 (I did each 4 bits separately). Keep in mind
0000 = 0
0001 = 1
..........
1001 = 9
1010 = A (10)
1011 = B (11)
1100 = C (12)
1101 = D (13)
1110 = E (14)
1111 = F (15)
It is preferable to break up into nibbles (4 bits each).

So how does that work out to 215. Well, I'll do it straight binary, with each digit to the left having a power of 2 increase:

128   64   32   16   8   4   2   1
1      1     0     1     0   1   1   1
So...
128+64+16+4+2+1 = 215

That stuff above may be overkill, but I think the real emphasis is that Hex and binary are exactly the same thing, just different ways of representing it, whereas hex is the prettier way. I would also emphasise to work in nibbles (4-bits) and go from there, when working with hex. the 215 math thing is technically correct, for a byte. it really depends on how far you want to take that though, because: 1D7 could also just as easily be 471 (256 + 215, since the 1 in hex has a value of 256 that far to the right). the numerical value could be really high values depending on if you want to look at it that way. but hex doesn't always represent 8-bit unsigned numbers. The best and most significant example of this would be an op code, you can think of it as a number, but the number is more arbitrary than the meaning of what it does. So doing the math for a byte (2 nibbles) of hex is really only useful when trying to figure out what 8-bit unsigned number it would represent (of which you could do the same with binary; being that hex and binary represent the same data).

I hope none of this didn't come off as convoluted, and I'm not too sure how clear my information seemed. This is one area I could easily take clarifying questions in though, I deal with this stuff on a regular basis.

--------------------------------------------------------------------------------

Posted by **nak** on Tue September 16th, 2008 10:59:32 PM

Best thread in a while <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

All numbers are the same thing binary is just base 2, what we are used to is base 10, hex is base 16... you could mess around with a bunch of different bases if you wanted to... hurts my head though, I'll stick with those 3!

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed September 17th, 2008 12:42:39 AM

heh, more elegantly put.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed September 17th, 2008 01:59:41 AM

You should post that &quot;History of Hex Code&quot; to the blog... we need to get some content flowing.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed September 17th, 2008 09:10:43 AM

[quote=&quot;PHLAK&quot;:3nr857ho]You should post that &quot;History of Hex Code&quot; to the blog... we need to get some content flowing.[/quote:3nr857ho]


NO U
