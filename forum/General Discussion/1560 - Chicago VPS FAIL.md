## Chicago VPS FAIL
Posted by **Automated Penguin** on Thu February 23rd, 2012 04:47:05 PM

SO today I am greeted by this amazing deal, a 7/month VPS wth 2 gigs of ram right? So OK I have to check this out.

Anyway they sent me an email after registration containing my Username/Password combo. So I Sent them a support ticket asking whats up with that, because I feel like its a strong indicator that they arent hashing passwords right?

Well I'll let you read the rest....

[quote:1j4dv6lj]
Hello,

I have some questions about the service.

First of all I was wondering if there is any user controlled way to switch distros on the VM, basically re-image the vm on demand.

Secondly I am fairly alarmed at the fact that you are displaying and emailing me my password in plain text. This seems to imply that you are storing the passwords without securely hashing them first. I would like to hear some kind of explanation for that.

Thanks,

-Charles
[/quote:1j4dv6lj]
[quote:1j4dv6lj]
Charles,

In the control panel you can reload your VPS whenever you would like.

As for storing your passwords, this is not my area of expertese so my lead tech would have to answer that.

Regards,

---------------
Chris Fabozzi
CEO / Director of Operations
<!-- e --><a href="mailto:Chris@chicagovps.net">Chris@chicagovps.net</a><!-- e -->

[/quote:1j4dv6lj]

LOL THE CE FUCKING O IS DOING THE TECH SUPPORT? SWEET. Also he seems to know nothing about the DB/password storage. Epic.

[quote:1j4dv6lj]

Thanks,

I would like to hear what your lead tech has to say about it if possible.

Thanks,

-Charles

[/quote:1j4dv6lj]

[quote:1j4dv6lj]
Charles,

All of the passwords are hashed in teh database. Once logged in, they are decrypted.
[/quote:1j4dv6lj]

So passwords are "hashed" and then "decrypted" Uh Yeah...

[quote:1j4dv6lj]
Hi Jeremiah,

How then are you able to display them to me in plain text?

I don't understand how that would be possible if you are hashing the passwords?

Thanks for your time,

-Charles

[/quote:1j4dv6lj]

[quote:1j4dv6lj]

You may also want to review some of your procedures regarding sending and
displaying passwords in general.

It is widely accepted that sending passwords over email or displaying them
in plain text is extremely dangerous and often unnecessary.

Here are a few Google hits I came up with which discuss this issue.

<!-- m --><a class="postlink" href="http://www.techconsumer.com/2008/02/11/bad-form-companies-still-sending-my-passwords-via-email/">http://www.techconsumer.com/2008/02/11/ ... via-email/</a><!-- m -->

<!-- m --><a class="postlink" href="http://www.thebitmill.com/articles/password_email.html">http://www.thebitmill.com/articles/password_email.html</a><!-- m -->

<!-- m --><a class="postlink" href="http://imsaar.posterous.com/boycott-websites-that-send-you-email-with-you">http://imsaar.posterous.com/boycott-web ... l-with-you</a><!-- m -->

Typically the server code encrypts the plain-text password with a one-way
cypher , and stores the result of that. The idea is that it is
computationally infeasible to obtain the plain-text password from the
cypher text.

When the user logs in, they give their password, the server hashes it,
and checks if the result matches the cypher text stored in the
server's database.

But the server cannot tell the user what the user's password is, because
the server never stores a plain text copy.

Please reply with your thoughts on this subject as it concerns me and other
security conscious customers greatly.

Thanks again for your time,

-Charles

[/quote:1j4dv6lj]


[quote:1j4dv6lj]
Chicago VPS

Charles,

I understand the concepts, please review my signature. There are two options, you get passwords or you don't. This is from the developers of the software and not my of my own call.

If you feel it is an issue, use a nulled password, and change your password in your VPS and billing.

---------
Jeremiah Shinkle
<!-- e --><a href="mailto:jshinkle@chicagovps.net">jshinkle@chicagovps.net</a><!-- e -->
Chief Networking Officer
A+, N+, S+, Se+, L+, CCNA, ASA - Networking, cPBC::Tech, cPPC::Sales 
[/quote:1j4dv6lj]

LOL DEALING WITH A BAD ASS HERE SEC+ OMFG. Man this guy amirite? lol, Also change my password? what good would that do me it would just get re-stored in the same plain text field in their DB? huh.

Anyway I'll update you as these shenanigans move forward...

UPDATE:

So I just sent this.... No reply yet..

[quote:1j4dv6lj]
Hi Jeremiah,

Yeah I totally understand software restraints I'm just still conflicted on the whole hashed or not thing.

I feel like the fact that I am seeing my password in plain text is a strong indicator that the database is storing the passwords without hashing them first you know?

I guess I'm just looking for a more technical answer to satisfy my curiosity. I realize I'm asking a lot more than the average user but I feel like security is very important and I like to know that the services I use are secure.

I see your Sec+ so I know you are familiar with the concepts and that you understand my logic and concerns here.

I would really appreciate a technical answer as to how my information is being stored is all, I'm sure you can relate.

Thanks again and sorry for being such a bother,

-Charles
[/quote:1j4dv6lj]

Let me know what you guys think, am I out of line here? Maybe I should have held back on the sending passwords in emails lecture...

UPDATE:

Some more chatter... I'm starting to feel like I'm climbing a tree with no fruit here...

[quote:1j4dv6lj]
Charles,

As i stated, they are encrypted in the database, just like mine and the rest of the administrators on here. It decrypts them upon login.

---------
Jeremiah Shinkle
<!-- e --><a href="mailto:jshinkle@chicagovps.net">jshinkle@chicagovps.net</a><!-- e -->
Chief Networking Officer
A+, N+, S+, Se+, L+, CCNA, ASA - Networking, cPBC::Tech, cPPC::Sales 
[/quote:1j4dv6lj]
[quote:1j4dv6lj]
Hi Jeremy,

That doesn't make sense to me, as you know, a hash is a one way function by definition.

Please explain how the passwords are "decrypted" from a hash. I assume I am missing something or we aren't using the same terminology.

I am fairly technical you don't have to tone it down for me.

Thanks!
[/quote:1j4dv6lj]

UPDATE:

LEVEL 2 ACHIEVED. So I got past the CEO and the Chief Networking Officer.... Who is next?
#773023 - General VPS Questions Open - Level 2

UPDATE:

Well after 6 days of no response they finally copped out on me.

[quote:1j4dv6lj]
Hi, Haven't heard back in a while.

Just wondering what the status of this ticket is?

Thanks.

Charles
[/quote:1j4dv6lj]

[quote:1j4dv6lj]
Still looking for some kind of response to this....

The non-response I'm receiving seems to indicate you are doing some research or have no response for me?

Please let me know what the status of this issue is.

Thanks.
[/quote:1j4dv6lj]

[quote:1j4dv6lj]
Charles,

I am very sorry but we are not able to discuss this due to security. If you have any other questions, please let us know.

---------
Luc Ayotte
ChicagoVPS Support Tech
<!-- e --><a href="mailto:layotte@chicagovps.net">layotte@chicagovps.net</a><!-- e -->
[/quote:1j4dv6lj]

I guess their infrastructure cant stand up to scrutiny or technical questions of any nature...
How disappointing.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 23rd, 2012 05:17:17 PM

$7/mo VPS? You get what you pay for I guess.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu February 23rd, 2012 05:50:37 PM

[quote="PHLAK":3mxgc96c]$7/mo VPS? You get what you pay for I guess.[/quote:3mxgc96c]

Yeah its actually not that bad for 7 bux a month, 

I should probably stop kicking them in the teeth and just enjoy what I got.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu February 23rd, 2012 05:57:12 PM

[quote="Automated Penguin":3sq3ildg]I should probably stop kicking them in the teeth and just enjoy what I got.[/quote:3sq3ildg]

This is the wrong community to be proposing that.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri February 24th, 2012 12:08:12 AM

Epic conversation, thanks for sharing <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

Best part:

[quote:2miqnzd3]I understand the concepts, please review my signature.[/quote:2miqnzd3]

Lol, who cares. The request is for him to show his actual understanding, not the pieces of paper that says he should understand (of which he is not demonstrating). Him saying what he's saying and pointing to his certs merely make the certs look bad, in context.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri February 24th, 2012 07:35:38 AM

[quote="XlogicX":1vwuv5n9]Epic conversation, thanks for sharing <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

Best part:

[quote:1vwuv5n9]I understand the concepts, please review my signature.[/quote:1vwuv5n9]

Lol, who cares. The request is for him to show his actual understanding, not the pieces of paper that says he should understand (of which he is not demonstrating). Him saying what he's saying and pointing to his certs merely make the certs look bad, in context.[/quote:1vwuv5n9]

Yeah that was my take on it as well. I wanted to reply with like "Are you seriously asking me to be satisfied with the fact that you have a sec+?" But I figured that was the fast track to ending the conversation

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri February 24th, 2012 11:19:42 PM

Right exactly, I think the way you've been handling it is correct.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon February 27th, 2012 08:22:32 AM

Any updates on what level 2 had to say?

--------------------------------------------------------------------------------

Posted by **Urbal** on Mon February 27th, 2012 11:22:12 AM

This is fucking great! I can't wait to hear the outcome. "Please review my signature"... classic!

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon February 27th, 2012 01:41:03 PM

They have parked my ticket at "level two" and haven't contacted me since my last update.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed February 29th, 2012 01:33:56 PM

Don't let it sit parked without any activity for too long, or they'll likely close it.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed February 29th, 2012 05:00:45 PM

I replied 2 days ago asking for a status update, no response.

I guess I should post this thread on Reddit or something and let the community know.

UPDATE: they copped out on me, not sure where to go from here, I put the new stuff in the original post.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon May 21st, 2012 10:28:50 AM

[http://dilbert.com/fast/2012-05-19/:2v6k5geo][img](http://i.imgur.com/33V0l.gif[/img:2v6k5geo])

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Fri September 7th, 2012 10:20:27 AM

[quote:6bongnmv]I understand the concepts, please review my signature.[/quote:6bongnmv]

Heheheh! Using that one from now on.

"Don't question what we say! Please review our signature:"
