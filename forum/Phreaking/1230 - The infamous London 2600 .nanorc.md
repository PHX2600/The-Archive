## The infamous London 2600 .nanorc
Posted by **knightmare** on Sun April 11th, 2010 07:48:57 AM

Hey Guys,

I met Dual at the London 2600 meeting last week.  He has mentioned that a few
people want my .nanorc file which highlights various different lanuages and
codes.

There are some problems with the regex code, and I welcome any corrections.  :D

I also created the Windows 3.11 Hackbox in Qemu and will upload some screens in
due course...

UPDATE: 12 APR 2010 @ 10:34AM  I've updated a couple of lines and fixed some of
the errors.  If anyone wants to help, I could really do with someone who has
Cisco config files to help with that part of the highlighting.  I was thinking
of adding Toneloc logs too, is this something people would use, or not...?

UPDATE: 17 MAY 2010 @ 13:38PM This is yet another update to the nanorc file
which fixes some small regex bugs that had crept in over the 1000+ lines of
regex commands.  The Cisco highlighting has added a few more lines, and minicom
scripts and syslinux.cfg files are now supported.  I am slowly working on fixing
some of the issues.  As always, any suggestions, additions and corrections are
welcome.  Cheers.


Cheers,
Knightmare

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun April 11th, 2010 10:14:25 AM

wow awesome,

this will boost my productivity in nano 10000%

--------------------------------------------------------------------------------

Posted by **dual** on Mon April 12th, 2010 02:52:09 PM

Thanks for the rc file! And welcome!

--------------------------------------------------------------------------------

Posted by **dual** on Mon April 12th, 2010 03:03:01 PM

Ran into a little something using nano 2.0.9...

Error in /etc/nanorc on line 1048: Bad regex "\s*"$?".*$": Invalid preceding
regular expression

Should $? be escaped?

color white "\s*\$\?.*$"

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon April 12th, 2010 04:25:45 PM

Awesome, thanks! I'm one of the ones that requested this from Dual.

--------------------------------------------------------------------------------

Posted by **knightmare** on Tue April 13th, 2010 03:39:52 AM

Hi Guys,

Glad to be on board.  Always happy to contribute something to the HPAC community
:)

Some of the comments in the rc file give you an idea of what my work in progress
is.  I also plan to add lots of hacker tools to the bash syntax highlighting. I
will probably make that a new line with an appropriate comment to let people
know how to update it as they go.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed April 14th, 2010 09:22:59 PM

oi thanx next time im in london i'll buy you a pint

--------------------------------------------------------------------------------

Posted by **knightmare** on Mon May 17th, 2010 06:45:50 AM

Hi Guys,

Does anyone have a toneloc log file with carriers, etc in it that I can use as a
basis for adding toneloc support to nano...?

Also, I am currently working on finishing the easter egg, and minicom support.
If anyone would like to help me test these, please drop me a line.

Cheers,
Knightmare
