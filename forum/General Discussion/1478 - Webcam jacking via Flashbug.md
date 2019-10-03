## Webcam jacking via Flashbug
Posted by **XlogicX** on Sat October 22nd, 2011 02:35:40 AM

This guy explains how he does it, involves some clickjacking. The victim unwittingly accepts/allows their cam and mic to be shared.

<!-- m --><a class="postlink" href="http://www.youtube.com/watch?v=-LbvglVj8Ho">http://www.youtube.com/watch?v=-LbvglVj8Ho</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat October 22nd, 2011 02:37:32 AM

....though, they say they fixed it:
<!-- m --><a class="postlink" href="http://blogs.adobe.com/psirt/2011/10/clickjacking-issue-in-adobe-flash-player-settings-manager.html">http://blogs.adobe.com/psirt/2011/10/cl ... nager.html</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon October 24th, 2011 08:38:41 AM

Huh, That's pretty sneaky.

I wish I was a better web hacker.

Has anyone played with BeEF? <!-- m --><a class="postlink" href="http://beefproject.com/">http://beefproject.com/</a><!-- m -->

I played with it a bit here at ASU quite fun.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon October 24th, 2011 11:35:44 PM

BeEF looks cool, just watched the demo on their website. How is the actually hooking done, would you have to phish a user? or is it simpler than that.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue October 25th, 2011 08:42:48 AM

XSS or redirect the user to a site with the "hook" code.

Its basically a large blob of JavaScript which polls the server for commands and then sends back results.

Its pretty insane what you can do with it.

Maybe I will demo it at the next meeting.
