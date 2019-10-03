## Phx2600 CTF: Team and Upcoming events
Posted by **AltF4** on Sun January 13th, 2013 10:18:32 PM

Hey all,

So for some time now we've been putting some light effort into competing in online Capture the Flag events, but never made a large and concerted push. Well, I'd like to change that. If you haven't noticed, CTF games have really exploded in popularity. There happens to be a new event online nearly every month these days. Gone are the days when you had to wait to compete in the Defcon Quals only once per year.

So what is the Phx2600 CTF team? It is a loosely organized group that will compete in online CTF challenges for the purpose of education and entertainment. We don't have memberships, so you don't need to "join". You can play just by showing up at one of our events as they are planned. As usual, the Phx2600 philosophy of being an elitist-free environment will be present. We're all here to learn, so please don't count yourself out just because you don't think you're 1337 enough. I'm also going to start some outreach into some other local non-2600 communities to join in.

There's a (relatively) new website that keeps track of all the disparate CTFs happening out on the Internet: <!-- m --><a class="postlink" href="http://www.ctftime.org/">http://www.ctftime.org/</a><!-- m -->
You will find a calendar of upcoming events, team point tracking, writeups, and some answers to basic questions.

**Next Event:** Codegate Prelims and Nullcon CTF, March 1st-2nd 2013
- <!-- m --><a class="postlink" href="http://www.ctftime.org/event/67/">http://www.ctftime.org/event/67/</a><!-- m -->, <!-- m --><a class="postlink" href="http://www.ctftime.org/event/62/">http://www.ctftime.org/event/62/</a><!-- m -->
- Meetup is in person at the March Phx2600 meeting. See the main page phx2600.org for details.

Naturally, it is not required that you be present for the entire meetup, but you are strongly encouraged to give a full effort. A CTF is a 48 hour hackathon! Also note that we'll be playing continuously throughout the weekend online via IRC and such. 

**How do I play?**

In order to play with the Phx2600 team, you will need to communicate along with us. CTF is a team sport! To that end, we will be using the following to collaborate and communicate:

**File sharing:**

A very frequent need of the competition is to quickly and easily share files amongst one another. If someone cracks half of a binary, another teammate will want to look at the remaining half. Transferring files over USB stick is unsafe security wise (you probably shouldn't trust a USB stick a hacker gives to you) and also useless to people not within arm length of you (playing from home). 

To solve this problem, we are using SparkleShare. It is a Dropbox-like program that uses a git backend and is Free Software. You can share files with the rest of us just by dragging and dropping them into a special folder. Github was gracious enough to give our team free private repositories to use during the competitions. This will let us share files in secret during the competition, and then open them up to the world afterward. here is how to get it set up:
[quote:1x1w98nu]
[u:1x1w98nu]Prerequisiites[/u:1x1w98nu]

    A GitHub account (sign up at <!-- m --><a class="postlink" href="https://www.github.com">https://www.github.com</a><!-- m -->)
    sparkleshare (<!-- m --><a class="postlink" href="http://sparkleshare.org/">http://sparkleshare.org/</a><!-- m -->)
    Git >= v1.7.12 (<!-- m --><a class="postlink" href="http://www.git-scm.com">http://www.git-scm.com</a><!-- m -->)

[u:1x1w98nu]Install Git on Ubuntu[/u:1x1w98nu]

$ sudo apt-get update &amp;&amp; sudo apt-get install git

To generate an SSH key, run the following from a terminal:

$ ssh-keygen -r rsa -C "your_email@example.com"

Add Your SSH Key to GitHub

Copy your SSH key to your clipboard by running:

$ clip < ~/.ssh/id_rsa.pub

    Go to your Account Settings
    Click SSH Keys in the left sidebar
    Click "Add SSH key"
    Paste your key into the "Key" field
    Click "Add key"
    Confirm the action by entering your GitHub password

[u:1x1w98nu]Install Sparkleshare on Ubuntu[/u:1x1w98nu]

    $ sudo apt-get install sparkleshare

[u:1x1w98nu]Add a Project to Spakleshare[/u:1x1w98nu]

    From the Sprakleshare context menu, select "Add hosted project..."
    Select GitHub as the project host
    Use "PHX2600/project_name" for the remote path. In thsi case: "PHX2600/codegate-2013" and "PHX2600/nullcon-2013"
    Click the Add button
[/quote:1x1w98nu]

**Communications:**

Our primary method of communication when not meeting in person will be via IRC. Freenode, room #phx2600-ctf Note that while in-person meetups are happening, we will likely not be checking IRC very often, if at all. IRC will be primarily used for in-between hours and late nights when we should probably be sleeping. So please come to the meet-up if you want to play.

**What to bring with you?**

CTFs are a hands-on hackathon. Don't expect to sit around idly thinking on some abstract problem. You will be throwing together quick python scripts, analyzing packet dumps, tracing through a mystery executable's system calls, injecting SQL statements into some web field, etc... So you will most certainly require your own laptop to do this on. You will also find that a good GNU/Linux distribution will serve you best, as well. Backtrack isn't needed, precanned attack tools won't get you anywhere here, and it doesn't make for a very friendly normal desktop anyway.

Thanks,
-Alt

--------------------------------------------------------------------------------

Posted by **tprime** on Mon January 14th, 2013 12:39:04 PM

Sounds cool! I will see if anybody from Buffer Overflow wants to participate. We just had the first 'hacker challenge night' at Heatsync last month, which we want to continue with on a regular basis. There was a good turnout so I imagine this will be able to attract a good crowd if properly advertised, especially on the heatsync blog. Many of them were quite new to security though, so some hand-holding will probably be necessary.

--------------------------------------------------------------------------------

Posted by **rj98942** on Mon January 14th, 2013 10:47:44 PM

I'll pass this around to the group at MCC as well. If it's going to be anything like the Buffer Overflow one, you might need more room. Hopefully the girlfriend will let me out of the house for that long.

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue January 15th, 2013 03:06:59 PM

That would be great, tprime and rj98942. Please do.

As for "hand holding", we are very inviting for beginners. You're not going to be expected to have some minimum level of awesome in order to participate. However the CTF is a competition, not a class. We're here to learn by doing. So I wouldn't want someone to come in with wrong expectations. This won't be a passive experience where you sit in the back of the room and listen to someone talk at you. But if you're not familiar with technique X, or tool Y, I would be super happy to tell you, and so would everyone else. I hope the distinction in clear.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue January 15th, 2013 03:31:44 PM

Thanks for posting this AltF4.  I hope we can get some more active contributors to the CTFs.  They are usually pretty fun and, at the very least, I generally learn something new by participating.

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu January 31st, 2013 03:29:27 PM

OP has been updated to include the following:

[quote:3ea99oxf]
**How do I play?**

In order to play with the Phx2600 team, you will need to communicate along with us. CTF is a team sport! To that end, we will be using the following to collaborate and communicate:

**File sharing:**

A very frequent need of the competition is to quickly and easily share files amongst one another. If someone cracks half of a binary, another teammate will want to look at the remaining half. Transferring files over USB stick is unsafe security wise (you probably shouldn't trust a USB stick a hacker gives to you) and also useless to people not within arm length of you (playing from home). 

To solve this problem, we are using SparkleShare. It is a Dropbox-like program that uses a git backend and is Free Software. You can share files with the rest of us just by dragging and dropping them into a special folder. Github was gracious enough to give our team free private repositories to use during the competitions. This will let us share files in secret during the competition, and then open them up to the world afterward. 

To share files with us:
1) Download the sparkleshare client (available on Linux/Windows/Mac)
2) Make a github account
3) Inform me or PHLAK (in person at the event, or via email or forum post beforehand) what your github account is, and I'll add you to the list of people able to access the files.
4) Add the repository that I give you to your SparkleShare accounts

**Communications:**

Our primary method of communication when not meeting in person will be via IRC. A specific channel will be determined at a later time. (probably on Freenode, though) Note that while in-person meetups are happening, we will likely not be checking IRC very often, if at all. IRC will be primarily used for in-between hours and late nights when we should probably be sleeping. So please come to the meet-up if you want to play.

**What to bring with you?**

CTFs are a hands-on hackathon. Don't expect to sit around idly thinking on some abstract problem. You will be throwing together quick python scripts, analyzing packet dumps, tracing through a mystery executable's system calls, injecting SQL statements into some web field, etc... So you will most certainly require your own laptop to do this on. You will also find that a good GNU/Linux distribution will serve you best, as well. Backtack isn't needed, precanned attack tools won't get you anywhere here.

[/quote:3ea99oxf]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri February 1st, 2013 09:22:53 AM

This is a great post,

You know I'll be there.

--------------------------------------------------------------------------------

Posted by **twitterkilo** on Tue February 26th, 2013 07:59:00 PM

The IRC is at <!-- m --><a class="postlink" href="http://webchat.freenode.net/">http://webchat.freenode.net/</a><!-- m --> and channel is #phx2600
