## encrypted google searches
Posted by **XlogicX** on Sat October 22nd, 2011 01:02:27 AM

Google is starting to make searches encrypted by default...as long as you are signed in.

However, if you don't want to be signed in, the already existing method of just manually going to <!-- m --><a class="postlink" href="https://www.google.com">https://www.google.com</a><!-- m --> should still work.

This is good news in general, though it will be a small blindspot for coffee shop monitoring, but I still encourage this from google. Although I would be much happier with them if they just made the not-signed-in version default to https as well.

--------------------------------------------------------------------------------

Posted by **ArchAngel** on Mon October 24th, 2011 06:56:59 AM

Relatedly: if you change your settings to make HTTPS the default when signed in, the GMail Notifier application for Windows will frequently Lose Its Shit™ until you drop the following into your registry:

[code:3vjy4rq6]
&#91;HKEY_CURRENT_USER\Software\Google\Gmail\Flags&#93;
&quot;url&quot;=&quot;https&#58;//mail&#46;google&#46;com/mail/&quot;
[/code:3vjy4rq6]

Hopefully this will save someone some time ...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon October 24th, 2011 08:36:28 AM

Excellent info guys.

Thanks.

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon October 24th, 2011 12:30:39 PM

Nice to see it as the default. (Or a default, anyway)

I still recommend HTTPS Everywhere to everyone I see, though. Covers lots more than Google.
<!-- m --><a class="postlink" href="https://www.eff.org/https-everywhere">https://www.eff.org/https-everywhere</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon October 24th, 2011 11:32:03 PM

Agrees with https everywhere, definitely one of the plug-ins in use on my browser.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue November 1st, 2011 11:01:58 AM

[quote=&quot;AltF4&quot;:levnju70]Nice to see it as the default. (Or a default, anyway)

I still recommend HTTPS Everywhere to everyone I see, though. Covers lots more than Google.
<!-- m --><a class="postlink" href="https://www.eff.org/https-everywhere">https://www.eff.org/https-everywhere</a><!-- m -->[/quote:levnju70]

+1 for HTTPS Everywhere, though I did run into a bug on Youtube related to it.  Had to disable ytimg.com to allow resizing of videos.

--------------------------------------------------------------------------------

Posted by **nak** on Tue November 1st, 2011 05:40:35 PM

&quot;I started using HTTPS Everywhere because of this forum thread, and it's great! Only ran into a problem while trying to see Steve Job's last words&quot; - Oh wow, oh wow, oh WOW.
