## Quick and Simple PHP directory lister
Posted by **PHLAK** on Tue June 30th, 2009 12:20:05 AM

Just pushed my new site for my Directory Lister project: <http&#58;//www&#46;directorylister&#46;com>

Directory Lister is a simple PHP based script created to let you list the contents of a directory and all it's sub-directories and allow you to navigate there within. Just download and install Directory Lister to any web directory and have immediate access to all files and sub-direcories under that directory.

Check it out and spread the word on [b:2l2ez58v][http&#58;//digg&#46;com/d1vFso:2l2ez58v]Digg[/url:2l2ez58v][/b:2l2ez58v] or [b:2l2ez58v][url=http&#58;//www&#46;reddit&#46;com/submit/?url=http&#58;//www&#46;directorylister&#46;comtitle=Quick%20and%20Simple%20PHP%20Directory%20Lister](Reddit)[/b:2l2ez58v] if you feel so inclined.

--------------------------------------------------------------------------------

Posted by **nak** on Tue June 30th, 2009 03:45:13 AM

dang nice site and php script, should I click an ad?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue June 30th, 2009 03:33:13 PM

Looks alot like the directory lister I used to use, 

if its anything like that one then im sure its a good script.

--------------------------------------------------------------------------------

Posted by **Evil1** on Tue June 30th, 2009 10:15:39 PM

Hey PHLAK, you sure you wrote that directory list yourself? Looks copied from evoluted.net Here is a comparison.

[img:2ul2ywl9]http&#58;//i43&#46;tinypic&#46;com/2cwosjo&#46;jpg[/img:2ul2ywl9]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue June 30th, 2009 11:05:36 PM

[quote=&quot;Evil1&quot;:3sk5wwjd]Hey PHLAK, you sure you wrote that directory list yourself? Looks copied from evoluted.net Here is a comparison.[/quote:3sk5wwjd]

Well you caught me.  I was, in fact, inspired by an earlier version of that very directory lister ([http&#58;//www&#46;chriskankiewicz&#46;com/documents/phx2600/dlister&#46;zip](See the exact version here)).  However, if you'd take a look at the code underneath, you'll probably notice it is substantially different.  Also, at the time I started coding my script, nowhere in his script or on his site could I find a copyright notice for the script.  Lastly, I find it hard to believe that any coder can honestly say that they never borrowed code from other sources, ESPECIALLY on the web.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue June 30th, 2009 11:48:39 PM

Yeah but most coders making ad revenue off the content they borrowed will also pay royalties for their &quot;inspiration&quot; or at least give credit where its due.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed July 1st, 2009 07:19:33 PM

I seriously doubt I will make any money on those ads.  They're more of an experiment than they are of a source of income.

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat July 11th, 2009 08:47:27 PM

Agree, you should always give credit unless it's some incredibly minor piece of code. 

That said, this is just what I'm looking for.  However, after installation, all I get is an output of the source code file when I goto index.php url and a &quot;Not Found&quot; when I got the directory it's in.  It's not working for me.  I wanted to use it to list all my .swf files that I've been working on lately.

Maybe cox webspace doesn't support php.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon July 13th, 2009 10:57:15 PM

[quote=&quot;CultLeadr&quot;:a78iuazn]Maybe cox webspace doesn't support php.[/quote:a78iuazn]

I believe that's  correct, Cox webspace does not support PHP.

--------------------------------------------------------------------------------

Posted by **hexatex** on Sat July 18th, 2009 07:47:37 PM

found a hole. according to the code I should not be able to view the folder named .directory-lister
And it is infact blocked at this url:
<!-- m --><a class="postlink" href="http://www.directorylister.com/demo/index.php?dir=.directory-lister">http://www.directorylister.com/demo/ind ... ory-lister</a><!-- m -->

but when I go here I can view the directory contents
<!-- m --><a class="postlink" href="http://www.directorylister.com/demo/index.php?dir=.directory-lister/">http://www.directorylister.com/demo/ind ... ry-lister/</a><!-- m -->

Hey Look its my first post in this forum hello everyone

--------------------------------------------------------------------------------

Posted by **hexatex** on Sat July 18th, 2009 08:18:30 PM

lols another hole Not sure why this hole works on my server and not yours, some configuration thing, anywho, if you goto index.php?dir=/tmp/ 
you can see the tmp contents, you can do this to any folder that the script has rights to view. you have protection against ../ but it allows you to start at root / 
also, not sure if this work, (I dont have a server with the proper config) but it may be possible to goto 
index.php?dir=..%00/ and get past your filters, however the null byte gets changed to \0 on both of our servers.

--------------------------------------------------------------------------------

Posted by **hexatex** on Sat July 18th, 2009 11:31:23 PM

LOL nvm didnt get tthe updated version so ignore my last post, have retested my first post yet though

btw you need to put the updated coed on your website, and the folder with the css and images is not in the zips on your site

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun July 19th, 2009 03:21:36 PM

[quote=&quot;hexatex&quot;:5hy5epiz]found a hole. according to the code I should not be able to view the folder named .directory-lister
And it is infact blocked at this url:
<!-- m --><a class="postlink" href="http://www.directorylister.com/demo/ind">http://www.directorylister.com/demo/ind</a><!-- m --> ... ory-lister

but when I go here I can view the directory contents
<!-- m --><a class="postlink" href="http://www.directorylister.com/demo/ind">http://www.directorylister.com/demo/ind</a><!-- m --> ... ry-lister/[/quote:5hy5epiz]

Noted.  Will be fixing this and updating the script (hopefully) later today.

Also, you may consider joining [http&#58;//github&#46;com/:5hy5epiz]GitHub[/url:5hy5epiz], forking [url=http&#58;//github&#46;com/PHLAK/directory-lister/tree/master](my project,) making the changes and committing it yourself.  Then I will merge your commits back into the master and everyone is happy!  After all, that's the power of open source!


[quote=&quot;hexatex&quot;:5hy5epiz]btw you need to put the updated coed on your website, and the folder with the css and images is not in the zips on your site[/quote:5hy5epiz]

Unsure of what you mean by this.  I just downloaded the zip and extracted it on my machine and saw every file needed.  If you're on Linux though you might not see the .directory-lister folder because of the preceeding period, try doing an  &quot;ls -a&quot; to see if you can see it.


[quote=&quot;hexatex&quot;:5hy5epiz]Hey Look its my first post in this forum hello everyone[/quote:5hy5epiz]

CONGRATULATIONS!  And welcome to the forums!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun July 19th, 2009 04:37:15 PM

Script has been updated to v1.0.3 including slight security tweak and other minor fixes.  Get it at <!-- m --><a class="postlink" href="http://bit.ly/JDphG">http://bit.ly/JDphG</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed November 11th, 2009 01:58:29 PM

I would find an optional CAPTCHA very useful for this, for whenever you click on a file.  I'm going to use this lister for some of my website files, but there's a great potential for abuse, from other sites stealing links.   Happens all the time to sites like mine.   

It would also be nice if it kept track of how many times a file was accessed... but I'm probably asking for too much.  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

This is still great though as is.  But don't you want to be awesome? ;P

EDIT:

Incidentally, I ran into a snag deleting a test directory after I had installed this php script.   Remains of it was invisible, so I had to issue manual ftp commands to get rid of it the rest.  In particular:

CWD .directory-lister
RMD .directory-lister
