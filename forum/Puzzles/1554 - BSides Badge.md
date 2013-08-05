## BSides Badge
Posted by **nak** on Sun February 19th, 2012 12:26:50 AM

<https://twitpic.com/8lk2eu>

    0e 07 1a 1f 4d 49 5c 09 00 18 48 14 02 40 46 21 17 02 5e
    e0 71 a1 f4 d4 95 c0 90 01 84 81 40 24 04 62 11 70 25 ef

    0e071a1f4d495c09001848140240462117025e
    e071a1f4d495c09001848140240462117025ef

RT @schuetzdj: A hint on the #bsidesphx badge puzzle: there are 19 hex pairs.
Drop first 0 or last F? A nybble at frequency analysis might help you decide.

--------------------------------------------------------------------------------

Posted by **AltF4** on Sun February 19th, 2012 09:16:43 AM

Frequency analysis seems to suggest a simple cipher to me. Caeser if they wanted
it easy. Vignere if they wanted it hard.

The hex values do surely seem low entropy. I'm going to try enumerating some
possibilities for a Caeser cipher encoded into ascii. See if it gets anywhere.

EDIT: I can't find any good Caseser cipher solvers that do more than just case
insensitive alpha characters. (IE: 26 characters) So I'm going to make one that
doe ASCII in hex. Hopefully won't take more than a few hours. XD

--------------------------------------------------------------------------------

Posted by **AltF4** on Sun February 19th, 2012 03:49:12 PM

Okay, finished the program:

<https://github.com/altf4/CaesarSolver>

The results have unprintable ASCII characters, naturally, so I'm attaching them
as text files to this post.

There's only a few interesting results, in the range of key = 32

Key 32: .':?mi|) 8h4"`fA7"~

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 19th, 2012 06:47:43 PM

    #! /usr/bin/python2

    import struct

    badge_bytes = '0e071a1f4d495c09001848140240462117025e'

    FSNOW_bytes = '46534e4f5746534e4f5746534e4f5746534e4f5746534e4f57'

    fin = ''
    fin_num = ''

    for i in range(0, len(badge_bytes), 2):
      fin += chr(int(badge_bytes[i:i+2], 16) ^ int(FSNOW_bytes[i:i+2], 16))
      fin_num += str(hex(int(badge_bytes[i:i+2], 16) ^ int(FSNOW_bytes[i:i+2], 16))) + ' '

    print fin
    print fin_num

outputs:

HTTPGOOGLgDL (ascii of decimal)

72 84 84 80 26 15 15 71 79 79 14 71 76 15 17 103 68 76 17 (decimal)

Some were 32dec off from the actual character needed to get the answer:
<http://goo.gl/1Gdl1>

What a terrible prize. I find it difficult to fap to (?°?°??? ???

**tl;dr:**

FSNOW (over and over) was the key (maybe...), it got enough of the answer
readable that I was able to find out how far off the wrong characters were (://
. gD were off by 32 decimal) and be able to manually fiddle it until it worked.

**edit:**

neupqebtjpafadstkbtqzmqo7o8n6625480731on2731r378pp109paftfy

Found these 60 characters at the bottom of the .PNG file. wut.

edit...

neupqebtjpafadstkbtqzmqo7o8n6625480731on2731r378pp109paftfyx

OUCH. that x

--------------------------------------------------------------------------------

Posted by **AltF4** on Sun February 19th, 2012 08:16:52 PM

Lol, It's a picture of Caesar's Palace. Caeser Cipher it is!

Rot14:

BSIDESPHXDOTORGHYPHENAEC7C8B6625480731CB2731F378DD109DOTHTM

or:

<http://bsidesphx.org/-AEC7C8B6625480731CB2731F378DD109.htm>

But the rotate tool I used didn't rotate the numbers. So that's probably
wrong... Working on it.

EDIT: Here it is:

<http://bsidesphx.org/aec7c8b6625480731cb2731f378dd109.html>

And that's a SLASH not a HYPHEN. Sheesh! Caused some headache. :) Thanks to
Penguin for that last part.

--------------------------------------------------------------------------------

Posted by **nak** on Sun February 19th, 2012 09:57:49 PM

<http://darthnull.org/2012/02/19/bsides-phoenix-2012-badge-puzzle/>

and a write up :P

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon February 20th, 2012 06:32:10 PM

Just got a reply to our email.

> Skyler Bingham <ailiminator@gmail.com>
>
> Nice work! You guys are the second to solve this year's challenge (and no one
> else has solved it so far).
>
> Hope you enjoyed it!

Yay!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 23rd, 2012 05:36:19 PM

Damn, I missed all the fun.
