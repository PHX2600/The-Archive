## Site Slowness
Posted by **PHLAK** on Thu August 28th, 2008 08:37:41 PM

Some of you may have noticed some pretty significant slow downs from the site over the last couple of days, well, I'll take the blame for it, but I do think the server is partially at fault (XlogicX, we'll talk about that).

Basically, I noticed the server get slower and slower over the last few days as I was working on the new [url=http&#58;//www&#46;phx2600&#46;org/blog:1qmpyn12]Wordpress layout[/url:1qmpyn12].  At first I thought this was due to some maintenance or miscellaneous work being performed server-side, because I would usually be working on the site between midnight and 4am.  However, this morning when I realized that the site was still slow between 11am and noon, I knew something was wrong.

Anyway, I fidgeted with the Wordpress install and found out that 2 of the WP plugins were responsible for the slowness of the site.  The interesting thing is, the plugins that are causing the slowness are plugins that communicate with external sites.  Along these same lines, while I was developing the site, I noticed that I could not have a file open for editing and upload a file at the same time.  In other words, it seemed that the number of active connections to the server is very limited.  Anyway, hopefully I'll get to talk with XlogicX at the September meeting and we'll see what we can do about this problem.

[b:1qmpyn12]UPDATE:[/b:1qmpyn12] I believe the slowness was mostly caused by a bug in Akismet (Wordpress plugin).  There was a fix posted ~24 hours after a previous update, and I think this has fixed the speed issues... for the most part.
