## Batch Calculator
Posted by **Valveritas** on Thu January 31st, 2008 01:39:21 PM

Came across this the other day.  I don't know why, but I found this particularly awesome. 

[code:7kp9hkbw]@echo off
echo Type exit when done&#46;
&#58;start
set /p _string=&quot;&gt; &quot;
if /i &quot;%_string%&quot;==&quot;exit&quot; goto end
set /a _result=%_string%
echo %_result%
goto start

&#58;end
echo Bye&#46;
echo&#46;

set _string=
set _result=[/code:7kp9hkbw]

You can enter just about any mathematical expression and get an answer.  I have no idea what this would really be useful for, but having a batch file do this in just few lines is ...well, awesome.

--------------------------------------------------------------------------------

Posted by **nak** on Thu January 31st, 2008 03:32:35 PM

Cool beans! Maths are useful.

--------------------------------------------------------------------------------

Posted by **phigan** on Fri February 1st, 2008 11:11:46 AM

Nice, now get it use decimals. <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri February 1st, 2008 11:46:59 AM

Yeah, when I did 12/5 I got 2.  I was like OH LAWD!

I wonder what would happen if I divided by zero...?

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat February 2nd, 2008 05:20:36 PM

Maybe we should have a contest to see who can come up with the most complex and elaborate expression that works.  Keep in mind you may use any of these:

[quote:3qijupnd]
 ()                  - grouping
    ! ~ -               - unary operators
    * / %               - arithmetic operators
    + -                 - arithmetic operators
    &lt;&lt; &gt;&gt;               - logical shift
    &amp;                   - bitwise and
    ^                   - bitwise exclusive or
    |                   - bitwise or
    = *= /= %= += -=    - assignment
      &amp;= ^= |= &lt;&lt;= &gt;&gt;=
    ,                   - expression separator
[/quote:3qijupnd]

Of course, I would lose this contest.  But I'm curious as to what someone might be able to come up with.

--------------------------------------------------------------------------------

Posted by **nak** on Sat February 2nd, 2008 08:02:39 PM

ALUE=((((1^-^1)+((2*3)*(14/2)))/((6^2)/6)*(1^10))/(10^6))*(100/10)+2

Uhh, nothing special here folks.  The &amp; doesn't seem to want to work, probably because the dos interpretor see's it as trying to run another exe in the background.
[quote:3fbeicmx]
&gt; ALUE=((1^-^1)+((2*3)*(14/2)))/((6^2)/6)*(&amp;10)
Missing operand.
'10)' is not recognized as an internal or external command,
operable program or batch file.[/quote:3fbeicmx]
