## Anti-bot measures for phpBB
Posted by **Valveritas** on Thu February 14th, 2008 04:14:01 AM

I guess this thread is mostly directed to PHLAK and XlogicX. 

Recently I installed [http://www.phpbb.com/mods/db/index&#46;php?i=misc&amp;mode=display&amp;contrib_id=1699](a mod) for an older version of phpBB.  XlogicX installed such a mod on the old board but couldn't quite  remember at the time which one it was.

Anyway, it didn't quite work as I was hoping.  I was suppose to be able to modify the questions from the admin panel. There was a section for Textual Confirmation but when clicking on it did not display correctly. No fields or anything to modify. Other than that, it seemed to work (like when you register). But I couldn't change the questions.

I manually installed it, and I was very careful to install everything correctly. I have no idea what went wrong. No idea at all. [color=#FAFAFA:jnv58mom]&lt;- Desperation.[/color:jnv58mom]

So if you have any suggestions, I'm all ears.  Like a different mod maybe? I have no plans to upgrade to the latest version of phpBB at this time.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 14th, 2008 01:38:22 PM

I guess my first question is why do you need this?  PHPBB 3 has built in Captcha to prevent spam bots.

Also, have you looked for a newer version?

--------------------------------------------------------------------------------

Posted by **Valveritas** on Thu February 14th, 2008 04:35:35 PM

I'm not running phpBB 3.  There is a newer version of that mod I've discovered. Maybe it'll work. I had just figured <!-- m --><a class="postlink" href="http://www.phpbb.com/">http://www.phpbb.com/</a><!-- m --> would have the latest version. Apparently that's not how it works.

I was wondering if most bots could be stopped simply by changing the text in the registration process.  I'm not sure how they make their hooks. Anyone know more about that?

--------------------------------------------------------------------------------

Posted by **nak** on Fri February 15th, 2008 08:17:48 PM

I haven't looked at how bots work, but its probably hard-coded posting to variables, the best thing to change would be the POST variables on the form... example:

Go to a registration form on a forum (this is the one I used: <!-- m --><a class="postlink" href="http://www.waraxe.us/forum-register.html">http://www.waraxe.us/forum-register.html</a><!-- m -->), then in firefox do Right click &gt; View Page Info &gt; Forms (tab) the variables are right there:
[b:2sshzsqk]username
user_password
random_num
gfx_check
op[/b:2sshzsqk]

it is very possible to write a bot that does it by getting the page, parsing the variables and using some sort of algorithm to fill in the values, but I wouldn't spend the time to do that when the variables are the same across the installation of the forum you are targeting.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Fri February 15th, 2008 08:27:47 PM

I installed a simple mod recently that just adds another confirmation code.  No bots so far.  I found [http://www.phpbb.com/community/viewtopic&#46;php?f=1&amp;t=427852](a thread of information) that pretty much has everything I need to know for defense.

It would probably be fun to write a bot though. <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Tue February 19th, 2008 02:25:05 AM

I forget what the mod was called, it was good and fixed the bots, but I did have to edit the SQL table to change the messages.
