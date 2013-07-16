## PHX2600 hacked
Posted by **hexatex** on Fri August 7th, 2009 12:59:23 AM

Lol well mostly, I have enough info that if I wanted to spend enough time with it I would most definately gain access.
Ill give more info once PHLAK gets a chance to fix the problem.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri August 7th, 2009 10:24:16 AM

I think this is great... honestly, and would like to thank you for approaching me with the problems first and giving me a chance to fix them before publishing them.  After that I have no problem with you presenting your findings (avoiding the release anyone's private info if possible).

If anyone else finds any problems with the site/server, please email me at <!-- e --><a href="mailto:phlak@phx2600.org">phlak@phx2600.org</a><!-- e --> or send me a PM.  After all, this is a community driven site and everyone's contributions help make the experience better for all.

--------------------------------------------------------------------------------

Posted by **Evil1** on Fri August 7th, 2009 11:21:17 AM

<!-- e --><a href="mailto:hexatex@gmail.com">hexatex@gmail.com</a><!-- e --> AKA
Cory Baumer
38306 N 23 dr Phoenix Arizona 85086
[url:rox5ptub]http&#58;//local&#46;google&#46;com/maps?f=q&amp;source=s_q&amp;hl=en&amp;geocode=&amp;q=38306+N+23+dr+Phoenix+Arizona+85086&amp;sll=37&#46;0625,-95&#46;677068&amp;sspn=47&#46;349227,79&#46;013672&amp;ie=UTF8&amp;t=h&amp;z=16&amp;iwloc=A[/url:rox5ptub]
(623)-687-5379 (linked to datastorm PC repair, not registered as an official LLC)

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri August 7th, 2009 11:43:28 AM

[quote=&quot;Evil1&quot;:2gy44dn9]hexatex@gmail.com AKA
Cory Baumer
38306 N 23 dr Phoenix Arizona 85086
[url:2gy44dn9]http&#58;//local&#46;google&#46;com/maps?f=q&amp;source=s_q&amp;hl=en&amp;geocode=&amp;q=38306+N+23+dr+Phoenix+Arizona+85086&amp;sll=37&#46;0625,-95&#46;677068&amp;sspn=47&#46;349227,79&#46;013672&amp;ie=UTF8&amp;t=h&amp;z=16&amp;iwloc=A[/url:2gy44dn9]
(623)-687-5379 (linked to datastorm PC repair, not registered as an official LLC)[/quote:2gy44dn9]

OMG, man you got me, hahaha, I better melt down my computer. 
I wasn't trying to be secretive, if I was I wouldn't have posted in the forum using my common handle, lol, Just exploring the security of the site <!-- s;-) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";-)" title="Wink" /><!-- s;-) -->
oh, and actually its cory baumer aka hexatex. That company name is not registered as an llc because its not active, lol.

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri August 7th, 2009 11:46:41 AM

Oh and your two moves behind on my location, Im a friggin nomad, lol, dig deeper.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri August 7th, 2009 12:38:17 PM

Is there supposed to be a link to Viagra at the top left of your site: <!-- m --><a class="postlink" href="http://hexatex.org">http://hexatex.org</a><!-- m --> ?

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri August 7th, 2009 01:57:54 PM

omg hahaha I didnt notice that till now, it came with the wordpress template hahahahahahaha. Ill remove that as soon as possible lololol. Anyone wanna make the johnson grow? jk <!-- s:-) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":-)" title="Smile" /><!-- s:-) -->

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri August 7th, 2009 03:25:25 PM

[quote=&quot;PHLAK&quot;:r30b2ore]Is there supposed to be a link to Viagra at the top left of your site: <!-- m --><a class="postlink" href="http://hexatex.org">http://hexatex.org</a><!-- m --> ?[/quote:r30b2ore]
ok, penis pill link removed. Damn spammers and their free templates!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri August 7th, 2009 06:05:46 PM

You scratch my back, I'll scratch yours... metaphorically of course.

--------------------------------------------------------------------------------

Posted by **hexatex** on Sat August 8th, 2009 05:57:41 AM

Ok, so the hoe has been patched, time to realse the info <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

basically all it was, was the opendir command which allows url wrappers. First I got it to loginto a remote ftp site, funny but not useful. then I found you could type in index.php?dir=file:///etc/ to do directory traversal. All it really did was help me find hidden files and a list of all the websites hosted on this server, but it did get me enough information to gain access.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat September 26th, 2009 03:40:29 PM

How often do you come across this hoe on other sites?

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri October 2nd, 2009 02:41:54 PM

I assume you mean hole and not hoe. 
I've never seen this before actually, I just did some research on the different ways the command is used, and toyed with it on my server. I dont think the command is used that often, and if so not normally in a way that echos the response out. But I will keep this in mind in the future.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Fri October 2nd, 2009 02:48:34 PM

You said yourself &quot;the hoe has been patched&quot; - lol.

But yeah, I was just curious if you've come across this before.  Interesting that you haven't.
