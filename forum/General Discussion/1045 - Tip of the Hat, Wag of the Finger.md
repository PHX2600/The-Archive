## Tip of the Hat, Wag of the Finger
Posted by **TheWill** on Mon August 3rd, 2009 04:23:05 AM

**Tip of the Hat:**
   Great to meet a couple of you at defcon this past weekend! (Sorry, I don't remember any names.) It was my first actual hacker meetup and it did great things for my psyche (6,700 people just like me?!?) I'll try to make it to the meetup this Friday. Also, if you're a twitter type person, please shoot me a message [url=http://www.twitter.com/willbradley:22qtwyeo]@willbradley> since forums are about 10 years behind the online socializing curve. I r nice, n r do not b bitin.

**Wag of the Finger:**
   (Re: attached screenshot of "my password") Srsly guys? This kind of security hole is silly for a hacker group to be continuing... If you'd like me to hack phpbb to remove the little HERE IS YOUR PASSWORD WHICH YOU PROBABLY ALSO USE FOR OTHER FORUMS AND ONLINE SERVICES TOO note I'd be happy to help out <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Mon August 3rd, 2009 11:36:25 AM

welcome to the show

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon August 3rd, 2009 01:25:11 PM

I do kind of agree with you that sending your password along with the email is a bit of a security risk, but in no way is that risk on the PHX2600 end, it's all up to the receiver of the email.

However, I will see what I can do about removing it from the emails, probably just a simple PHP echo that can be removed or changed.

Thanks and welcome!

--------------------------------------------------------------------------------

Posted by **AltF4Warrior** on Mon August 3rd, 2009 10:46:58 PM

Hey, what's up?

I see you live in Tempe. Does that make you an ASU student? I'm lonely there. ASU hasn't much of a hacker community, I'm sorry to say. But I'm hoping to fix that. <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **dxh** on Mon August 3rd, 2009 11:24:30 PM

[quote="AltF4Warrior":evp89f48]I see you live in Tempe. Does that make you an ASU student? I'm lonely there. ASU hasn't much of a hacker community, I'm sorry to say. But I'm hoping to fix that. <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->[/quote:evp89f48]

Wat?  There be plenty of closeted hackers in ASULIUG and the ASU Computer Society Student Branch thar.

--------------------------------------------------------------------------------

Posted by **AltF4Warrior** on Tue August 4th, 2009 08:20:19 AM

Well don't be so damn closeted, then!  <!-- s:lol: --><img src="{SMILIES_PATH}/icon_lol.gif" alt=":lol:" title="Laughing" /><!-- s:lol: --> 

I was thinking of running an internal ASU CTF this semester. I wonder what kind of interest I might be able to get. The difficulty would be a little less than other national or international CTF's. And the scope would be more broad. (Hitting some things like cryptography, WLAN security, web apps, etc...) Not just focusing almost exclusively on binary reversing like others.

--------------------------------------------------------------------------------

Posted by **TheWill** on Tue August 4th, 2009 04:12:39 PM

Hey all, thanks for the warm welcomes.
I'm not an ASU student, but I do, shall we say, frequent the Tempe area.
Setting up a CTF would be pretty cool; I've always wanted to try writing secure code (how to write C# in a way you can't buffer overflow? No idea.) Plus working with Bill Nye would be pretty cool (didn't know you taught at ASU!)

--------------------------------------------------------------------------------

Posted by **Konshu** on Wed August 5th, 2009 03:25:33 PM

Welcome to PHX2600  <!-- s8-) --><img src="{SMILIES_PATH}/icon_cool.gif" alt="8-)" title="Cool" /><!-- s8-) -->

--------------------------------------------------------------------------------

Posted by **Evil1** on Fri August 7th, 2009 11:30:03 AM

So....posting a clear text password to a password protected email is thats usually SSL encrypted is bad how?

--------------------------------------------------------------------------------

Posted by **hexatex** on Fri August 7th, 2009 02:47:35 PM

[quote="Evil1":3okox7qn]So....posting a clear text password to a password protected email is thats usually SSL encrypted is bad how?[/quote:3okox7qn]

hmm I could see a security issue with that, email transfer usually isn't ssl encrypted by default, at least from what I have seen.

But also, its important that when an attacker gains access that it is limited. If an attacker cracks his email pass, he would then also have the password his forum account. Which give access to private messages that would give the attacker a foothold to move further.

Also i don't know the situaltion of the password thing, as I did'nt read to closely <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->, but if this is the password to his other online accounts that two could be very bad, unless hes talking about a password reset.

--------------------------------------------------------------------------------

Posted by **TheWill** on Fri August 7th, 2009 07:49:04 PM

A high profile example is the Twitter company hack a few weeks ago. A hacker found the personal Gmail address of an employee, asked for a password reset, noticed that it was going to send to an (expired) Hotmail address, registered that address and sent the reset, then logged into the Gmail account and sifted thru it looking for forum password emails like the one in question. Reset the Gmail password to the forum password which had a high probability of being identical, employee none the wiser. Rinse and repeat on up to the Twitter Google Apps account and all of their secret company documents.

Not to mention that SMTP email transmission and email databases themselves are frequently not encrypted, so emailing permanent passwords as a practice is quite flawed.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sat August 15th, 2009 01:05:49 PM

I had a brief look around the code and didn't see where it was generating the email text.  I could probably find it if I really dug deep, but that might take a while.  If anyone would like to help me find where it's echoing this, grab a copy of the PHPBB code from [url=http://www.ohloh.net/p/phpbb/download?filename=phpBB-3.0.5.zip:11yhff8x]here> and give me a file path/name and line number and I'll get this done.

--------------------------------------------------------------------------------

Posted by **jargon** on Wed August 19th, 2009 08:33:11 AM

**Re: Tip of the Hat, Wag of the Finger**

[quote="TheWill on Fri Aug 07, 2009 6:49 pm":1yflhaq1]
A high profile example is the Twitter company hack a few weeks ago. A hacker found the personal Gmail address of an employee, asked for a password reset, noticed that it was going to send to an (expired) Hotmail address, registered that address and sent the reset, then logged into the Gmail account and sifted thru it looking for forum password emails like the one in question. Reset the Gmail password to the forum password which had a high probability of being identical, employee none the wiser. Rinse and repeat on up to the Twitter Google Apps account and all of their secret company documents.

Not to mention that SMTP email transmission and email databases themselves are frequently not encrypted, so emailing permanent passwords as a practice is quite flawed.
[/quote:1yflhaq1]

[quote="PHLAK on Sat Aug 15, 2009 12:05 pm":1yflhaq1]
I had a brief look around the code and didn't see where it was generating the email text. I could probably find it if I really dug deep, but that might take a while. If anyone would like to help me find where it's echoing this, grab a copy of the PHPBB code from here and give me a file path/name and line number and I'll get this done.
[/quote:1yflhaq1]

This is an example with the XAMPP httpd using the default install, with PHPBB installed using default folder name:
[code:1yflhaq1]C:\xampp\htdocs\phpBB3\language\en\email\user_activate_passwd.txt[/code:1yflhaq1]

Here is that document:
[code:1yflhaq1]
Subject: New password activation

Hello {USERNAME}

You are receiving this notification because you have (or someone pretending to be you has) requested a new password be sent for your account on "{SITENAME}". If you did not request this notification then please ignore it, if you keep receiving it please contact the board administrator.

To use the new password you need to activate it. To do this click the link provided below.

{U_ACTIVATE}

If successful you will be able to login using the following password:

Password: {PASSWORD}

You can of course change this password yourself via the profile page. If you have any difficulties please contact the board administrator.

{EMAIL_SIG}
[/code:1yflhaq1]

You need to remove:
[code:1yflhaq1]
If successful you will be able to login using the following password:

Password: {PASSWORD}
[/code:1yflhaq1]

Either that or force people to change their password at the re-activation {U_ACTIVATE} url using a password strength test compared to the former password. You only want to do this server side, and only send the result of the check to the admin and nobody else in order for the admin to potentially assist post-reactivate regarding password trouble.

--------------------------------------------------------------------------------

Posted by **nak** on Wed August 19th, 2009 10:45:00 AM

nice nice nice

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri August 21st, 2009 04:37:27 PM

Registration/activation emails should no longer display your password.  Thanks to Jargon for scraping the code to find where this was!
