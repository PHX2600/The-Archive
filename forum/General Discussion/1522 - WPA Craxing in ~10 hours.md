## WPA Craxing in ~10 hours
Posted by **ArchAngel** on Wed December 28th, 2011 07:23:11 PM

<!-- m --><a class="postlink" href="http://www.devttys0.com/2011/12/cracking-wpa-in-10-hours-or-less/">http://www.devttys0.com/2011/12/crackin ... s-or-less/</a><!-- m -->
 Pretty much speaks for itself ... 10 hours is still a long time, but not outside the realm of feasability. Watch like five movies, come bax to a WPA key. ^_-.

Also ... wasn't sure where this kind of post belonged; move as appropriate please. ^_^;;

--------------------------------------------------------------------------------

Posted by **nak** on Fri December 30th, 2011 02:11:44 PM

Ok so I tried it out, expect an angry (or excited post at 1 AM)
[url:1qlw598e]http&#58;//nakedproof&#46;blogspot&#46;com/2011/12/installing-reaver-12-on-ubuntu&#46;html[/url:1qlw598e]

~edit:
I don't have injection support on any of my interfaces... I've never done a classy attack with packet injection... <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 31st, 2011 01:13:03 AM

Yeah, looks interesting, let us know what you guys find. I read another article on this at threatpost (<!-- m --><a class="postlink" href="http://threatpost.com/en_us/blogs/wifi-protected-setup-flaw-can-lead-compromise-router-pins-122711">http://threatpost.com/en_us/blogs/wifi- ... ins-122711</a><!-- m -->). It's the WPS feature (setup) that is vulnerable. The threatpost.com article has a decent breakdown of why. Reminds me of of shitty LanMan hashes; a 14 byte password broken into 7 byte parts.  <!-- s:o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":o" title="Surprised" /><!-- s:o --> . Each extra byte exponentially increases brute force times. So 8 is way better than 7, 9 way better than 8. 14 would be fantastic, but 2 sevens doesn't even come close to one 14 (blah blah blah <!-- m --><a class="postlink" href="http://en.wikipedia.org/wiki/Lanman">http://en.wikipedia.org/wiki/Lanman</a><!-- m -->)
