## Random bit trick (for swapping variables)
Posted by **XlogicX** on Fri September 18th, 2009 02:43:01 AM

How to swap values in two variables...wait for it...without a third one (well, also without a stupid swap opcode, if your machine language is so incredibly not RISC to have that).

Here is the old way:
Say you have A, B, and C and '=' is an assigment operation:
C = A
A = B
B = C
(ok, they're swapped now)

Say you're working in assembly with only two registers; you don't have the luxury of C (it can happen, seriously).

[code:1om37iq9]
A = A xor B             'step 1
B = A xor B             'step 2
A = A xor B             'step 3
[/code:1om37iq9]

It should be totally obvious that after those 3 xor's, A will now have what B had, and B will now have what A did... <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) --> 

Ok fine, wasn't even obvious to me, lets see it in binary. Well, before that, for those that don't know what XOR does, it's like 'or', but exclusive. In english: either or, but not both. So if I have a 1 and a 0, in any order, xor would return 1 (true), since either or (also not both) were true. If I have two 1's, or two 0's, xor would return 0 (false), because with 0's, neither is true, with 1's, both are true (can't have both, just one or the other).

So say A has 13 (1101), and B has 6 (0110)

Step 1:
[code:1om37iq9]
A = A xor B
    1101    (A, 13)
xor 0110    (B, 6)
----------
    1011    (A now has 11)
[/code:1om37iq9]

Step 2:
[code:1om37iq9]
B = A xor B
    1011    (A, now 11)
xor 0110    (B, 6)
----------
    1101    (B now has 13)  &lt;--see the magic starting to happen
[/code:1om37iq9]

Step 3:
[code:1om37iq9]
A = A xor B
    1011    (A, still 11)
xor 1101    (B, now 13)
----------
    0110    (A now has 6)  &lt;--There you have it, A now has 6, B has 13 (they are swapped)
[/code:1om37iq9]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri September 18th, 2009 08:56:33 AM

Genius.

xor is so useful it amazes me.

thats a pretty good trick, and you're right sometimes you only have a few registers, heck on the pic's you only have ONE multipurpose register (w).

Anyway im really enjoying all this assembly stuff makes me want to jump back into it sometime.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Fri September 18th, 2009 12:59:08 PM

We [i:1a02ah8m]love[/i:1a02ah8m] it!

We swear; understanding bitwise magic is like knowing kung fu.

Nice trick, xlogicx

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri September 18th, 2009 07:00:05 PM

I love this!  Actually useful information that is!
