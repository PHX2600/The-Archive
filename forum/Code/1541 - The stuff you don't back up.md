## The stuff you don't back up
Posted by **XlogicX** on Fri January 20th, 2012 12:08:25 PM

So with a massive amount of data, it would be too expensive and stupid to backup everything...when it's in the multitudes of a handful of terrabytes (on a personal system). As far as what to back up, I would say anything personal and anything that you have created; because this is the stuff you can't get back.

Then there's all that crap you've collected from the interwebs. You know you could probably go re-download most of it if you lose it.

...the dilemma comes when you actually lose all of that data, and you realise that you don't even remember exactly what you had in the first place. So here's a stupid bash script I made:

#!/bin/bash

[code:35iwsap8]cd /home/xlogicx/logs
ls -R /mnt -R &gt; manifest&#46;txt
cp manifest&#46;txt /mnt/serverdrive/manifest&#46;txt
7za a manifest&#46;7z manifest&#46;txt -pSECRET
cp manifest&#46;7z /home/xlogicx/Dropbox/manifest&#46;7z
rm manifest&#46;7z[/code:35iwsap8]

A little explanation. It recursively lists all of the contents of each drive on my server (of which is mounted). Now there's a local copy in my logs folder, but it also creates another copy of it in one of the drives on the server (&quot;serverdrive&quot; is generic, not an actual mount on my system). Then it creates a password protected 7z file (with password SECRET...not my password) and copies it to my Dropbox folder to get backed up &quot;off-site.&quot;

That way, if I lose the stuff I didn't back up, at least I completely know what it is that I lost.

Sounds kinda dumb, but that's why I love stupid linux bash scripting, you can do it anyway.

oh, and I cron'd it

--------------------------------------------------------------------------------

Posted by **Valveritas** on Fri January 20th, 2012 09:53:10 PM

I'd use it. <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon January 23rd, 2012 11:15:11 AM

This is smart and not something I've thought of before.  Sure, I have a good backup plan in place, but would I ever need to know what I didn't backup in the event of data loss?  Thanks for making me think XlogicX!

--------------------------------------------------------------------------------

Posted by **nak** on Mon February 6th, 2012 10:36:22 AM

I recently did some forensics on a drive that I accidently installed ubuntu over, which gave me a bunch of un-named files and corrupt files.

What would be useful would be to take an MD5 hash of every file on your system and save that in your list as well, so if you every have to do recovery you just take hashes of every file you've recovered compare it against your database and rename/re-organize the recovered files.

Just a thought <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon February 6th, 2012 10:41:54 AM

I'll give that some thought. The hashing part probably wouldn't be so hard, but I'm not sure what kind of method I would use for the recovery, I guess it would depend on the forensic software.

--------------------------------------------------------------------------------

Posted by **nak** on Mon February 6th, 2012 10:46:55 AM

[quote=&quot;XlogicX&quot;:61k1mnr9]I'll give that some thought. The hashing part probably wouldn't be so hard, but I'm not sure what kind of method I would use for the recovery, I guess it would depend on the forensic software.[/quote:61k1mnr9]

Yeah, you can just hope that you don't have to, but if you kept hashes for your files you should be able to hack something up IF something bad happens.
(Md5 hash all recovered files, put it in a database, compare to known name/hash database, update filenames-(locations?))

Here's my blog post talking about using `foremost`: [url:61k1mnr9]http&#58;//nakedproof&#46;blogspot&#46;com/2012/01/oops-formatted-my-windows-partition&#46;html[/url:61k1mnr9]

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon February 6th, 2012 11:50:02 PM

foremost/scalpel are fun tools, I'll talk more about that later.
