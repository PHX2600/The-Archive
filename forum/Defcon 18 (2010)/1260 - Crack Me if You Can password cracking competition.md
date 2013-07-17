## Crack Me if You Can password cracking competition
Posted by **PHLAK** on Thu July 1st, 2010 03:40:42 PM

Check this out, it's a password cracking competition at Defcon this year.

<http://www.korelogic.com/defcon_2010-contest.html>

Asside from the fact that this is relevent content to the PHX2600, the main
reason I'm mentioning this is because they state any number of people can be on
a team and only one person has to be present at the competion.  I've already
spoken with Penguin, and he sounded interested.  He also stated that he may have
access to a super computer for our use in cracking.

I still need to contact @TwtrHatingMatt (who is going to the convention) or
anyone else attending to talk it over, buy please respond if you're interested.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu July 1st, 2010 04:48:11 PM

Yeah I got permission to run "Benchmarks" on the High Performance Computing
cluster here at ASU.

700+ Nodes

5000+ Processors

12 Terabytes of Ram

Petabytes of Disk space

Awesome.

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu July 1st, 2010 11:08:51 PM

I'll do it w/ you guys. Sounds like a blast. I'll be at the con, though.

Talk about it at the meet tomorrow?

--------------------------------------------------------------------------------

Posted by **AltF4** on Wed July 7th, 2010 07:21:49 PM

Double Post:

So any thoughts on this? Should we take some time to prepare? Get some rainbow
tables together, word lists, mangling rules, etc...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu July 8th, 2010 02:24:51 PM

Do want,

who wants to meet up where/when?

I'm in.

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu July 8th, 2010 10:49:53 PM

Sometime next weekend? That's 2 weeks before the 'con. Should be enough time to
prepare. Will Unlimited still be a good place?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri July 9th, 2010 11:35:53 AM

I'm closer to the mesa/tempe/gilbert area,

Where are you located roughly?

If unlimited is about even between us then that would be fine, otherwise we
might as well meet somewhere else.

I'm on the ASU Tempe campus 7-4 week days.

GWC 164

--------------------------------------------------------------------------------

Posted by **AltF4** on Fri July 9th, 2010 01:24:34 PM

Oh, I'm not far from ASU. Around the 202 and Alma School. Could meet at ASU if
you like. What about Phlak?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri July 9th, 2010 01:39:10 PM

I can meet wherever.  Can we find a coffee shop near ASU with WiFi maybe? I know
of Cartel and Xtreme Bean, either wold work.  I'm not sure yet if I'm free
tomorrow, but Sunday I think I'm free all day.  ~~Hop in the PHX2600 IRC channel
on irc.2600.net to chat.~~  IM me on Google Talk at [Chris at ChrisKankiewicz
dot com].

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri July 9th, 2010 01:54:39 PM

Im there.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri July 9th, 2010 04:02:50 PM

We have 10000 CPU-Hours on the cluster.

one cpu for 10000 hours
10000 cpu's for one hour
etc

Here's the documentation
<http://hpc.asu.edu/help>

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu July 15th, 2010 07:49:46 AM

So how 'bout this weekend? What coffee shops are there around ASU?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu July 15th, 2010 08:09:24 AM

Fuck tons of coffee shops around here,

You guys can decide

<http://maps.google.com/maps?q=coffee&amp;f=l&amp;dq=asu+main&amp;sll=33.420481,-111.931973&amp;sspn=0.013199,0.022531&amp;ie=UTF8&amp;t=h&amp;split=1&amp;rq=1&amp;ev=zo&amp;radius=0.78&amp;hq=coffee&amp;hnear=&amp;ll=33.421269,-111.932788&amp;spn=0.013199,0.022531&amp;z=16>

If we meet near the brickyard we will have access to the engineering computer
labs there.

still trying to figure out the scheduler on the cluster so we can run tools on
It.

Maybe we should come up with an agenda for this meeting, things to accomplish
etc.

also I am <cbock@asu.edu<> on google talk if that is more convenient.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri July 16th, 2010 09:58:03 AM

I like Cartel Coffee Lab, wouldn't mind meeting there Saturday (after 2pm) or
Sunday afternoon.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon July 19th, 2010 08:41:39 AM

PROGRESS REPORT:

Finishing up downloading MD5 Tables featuring such hit artists as:

alpha-numeric-space#1-8
alpha-space#1-9
loweralpha-numeric-space#1-8
mixalpha-numeric-all-space#1-6
mixalpha-numeric-space#1-7
numeric#1-12

Will start on NTLM tonight.

PHLAK us handling LM and SHA

All tables are being transferred to large external devices for ease of transfer

Haven't talked to the BOFH for the cluster yet, Ill see If maybe he can help us
get some John on there.

I guess right now I'm thinking the slowest machine (Maybe mine? I only have a
plain ole core 2?) Should be running the rainbow tables and other machines with
more cores/faster clocks should probably be hitting John with some mangling
rules and word lists.

I found this fairly comprehensive word list as a start, its well formed and
doesn't have any ridiculous words or chains of punctuation or anything silly
like that <ftp://ftp.openwall.com/pub/wordlists/all.gz>

Anyway that's what I have so far.

Peace.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon July 19th, 2010 10:42:06 AM

Working on clearing out some HDD space, then I'll get my hashes downloaded.

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon July 19th, 2010 10:41:26 PM

Working on wrangling word lists and making mangling rules.

Oh, Penguin. If you need a hand figuring out that odd script format to get
things running on the ASU cloud, let me know. I'd be happy to help. And we
really want to be able to use that thing. I really want to see how far the ASU
supercomputer can get in incremental mode! Basically brute force.

You know, we might just wind up having to spend a non-trivial amount of time
compiling all of the results from our cracking together upon completion...
Especially if the organizers need our results in any particular format. (Which I
would imagine they would, so they could automatically check winners)


Good selection of International Plus odd Wordlists:
<ftp://ftp.ox.ac.uk/pub/wordlists/>

PacketStorm's Lists:
<http://packetstormsecurity.org/Crackers/wordlists/>
^Includes things like religious word lists. Bet that will get some hits.

OutPost9. Includes a lot of good name lists. Like names from movies, etc...
<http://www.outpost9.com/files/WordLists.html>

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue July 20th, 2010 08:13:27 AM

> **AltF4 wrote:**
> Oh, Penguin. If you need a hand figuring out that odd script format to get
> things running on the ASU cloud, let me know. I'd be happy to help. And we
> really want to be able to use that thing. I really want to see how far the ASU
> supercomputer can get in incremental mode! Basically brute force.

I have contacted the cluster admin about getting John working on there.

I'm waiting for a reply now.

If you want to play with it though i can request a secondary account for you if
you like.

Let me know.

--Penguin

--------------------------------------------------------------------------------

Posted by **Konshu** on Tue July 20th, 2010 10:45:10 AM

... and you have my sword.

Dual Xeon 5530's 32GB ram.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue July 20th, 2010 10:47:13 AM

UPDATE:

_IT'S ALIVE_

Got John compiled and running using MPI on teh cluster, so sweet.

Heres some results:

**DES Benchmarks:**
_Using 8 Nodes:_
Benchmarking: Traditional DES [128/128 BS SSE2-16]... DONE
Many salts:	20341K c/s real, 20316K c/s virtual
Only one salt:	17127K c/s real, 17149K c/s virtual
_Using 32 Nodes:_
Benchmarking: Traditional DES [128/128 BS SSE2-16]... DONE
Many salts:	81241K c/s real, 81292K c/s virtual
Only one salt:	68897K c/s real, 68880K c/s virtual
_Using 64 Nodes:_
Benchmarking: Traditional DES [128/128 BS SSE2-16]... DONE
Many salts:	162612K c/s real, 162597K c/s virtual
Only one salt:	137765K c/s real, 137735K c/s virtual


**MD5 Benchmarks:**

_Using 8 Nodes:_
Benchmarking: FreeBSD MD5 [32/64 X2]... DONE
Raw:	80555 c/s real, 80493 c/s virtual

_Using 32 Nodes:_
Benchmarking: FreeBSD MD5 [32/64 X2]... DONE
Raw:	322013 c/s real, 321873 c/s virtual

_Using 64 Nodes:_
Benchmarking: FreeBSD MD5 [32/64 X2]... DONE
Raw:	643964 c/s real, 643779 c/s virtual

The Benchmarks seem to scale very linearly so you can do the math for 128 nodes
256 etc I'm guessing on a weekend or a nice slow night we could use as many as
512 nodes.

Stuff to compare the benchmarks to:
<http://openwall.info/wiki/john/benchmarks>

Cluster status page ( may require creds ):
<http://saguaro.fulton.asu.edu/>

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue July 20th, 2010 11:12:48 AM

im in got some military grade encrtyp/decrtyp computers that have been
decommissioned that i can prolly use

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue July 20th, 2010 11:29:46 AM

> **TerrorDrone wrote:**
> im in got some military grade encrtyp/decrtyp computers that have been
> decommissioned that i can prolly use

Awesome!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue July 20th, 2010 11:42:24 AM

Okay, let's also schedule a 2550 meeting on the Friday of the con (July 30th,
during the competition) so we can all meet up and work on this.  We'll meet at
Unlimited Coffee (if that works for everyone) starting at 6pm going until
whenever, show up when you can.

--------------------------------------------------------------------------------

Posted by **Konshu** on Tue July 20th, 2010 11:44:57 AM

I will be at the RIU in Cabo...

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue July 20th, 2010 01:01:02 PM

will try to make it gonna head into the armory and see what i can do setting up
one of these computers also have a old laptop with a new processor laying around
that ill try to setup into just a cracking machine

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue July 20th, 2010 06:34:18 PM

I let out a maniacal laugh when I saw those benchmark tests, Penguin. That ASU
cluster will serve us very well. :)

I wanted to post this, from the contest rules:

> At the conclusion of the contest, KoreLogic will:
>
>   * Announce the winners and award the prizes.
>   * Release the entire password list.
>   * Provide statistics on which types of passwords were totally missed by all
>   teams.
>   * Provide statistics on which types of word lists were totally missed by all
>   teams.
>   * **Release a number of word lists and John the Ripper rules under an
>   open-source license. Taken together, these rules and word lists will be able
>   to crack a majority of the 53,000 passwords.**

(Emphasis mine)

So they're saying that the majority of the passwords can be cracked using good
word lists / manging rules. Good to know.

Also, KoreLogic (the contest organizers) have a series of tools and resources on
their website: <http://www.korelogic.com/tools.html>

Some of which are extensions and such for JtR. I would expect that KoreLogic
will use the contest as an opportunity to advertise for their own badassery. I
bet that a good portion of the passwords that can't be cracked with standard
wordlists/mangling rules will be cracked using their tools.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue July 20th, 2010 09:32:14 PM

Good catch AltF4.  I'd bet your correct on all counts.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue July 20th, 2010 10:18:42 PM

I hit a couple snags doing some playing with the cluster.

The Default JTR build wont do raw MD5 Hashes so im gonna try and install some
"patches" tomorrow to provide additional abilities like raw-MD5

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue July 20th, 2010 11:10:38 PM

I hit the exact same snag! How funny. I just got done applying a patch that
OpenWall had on their website with extra algorithms. Looks like it works. It
includes a boatload of hash algorithms like "raw"-MD5. Should be pretty self
explanatory I think:

Patch:
<http://www.openwall.com/john/contrib/john-1.7.6-jumbo-5.diff.gz>

HowTo: Apply Patches to John the Ripper
<http://openwall.info/wiki/john/how-to-extract-tarballs-and-apply-patches>

EDIT: Just tested this, and it works. Cracked some passwords I added to my own
Ubuntu machine. (Sha-512, as mentioned below) So, ya. Thumbs up.

Also, the Ubuntu repository version is kind of old. Newer version you get from
source is much faster, and has more algorithm support. So I'd suggest building
from source unless there's compelling reasons not to.

Also, this place has a patch for SHA-512 (The current default Ubuntu scheme,
which regrettably does not have default support in John) for JtR:
<http://pka.engr.ccny.cuny.edu/~jmao/node/26>

Though, technically, you can do SHA-512 in Ubuntu by using the "--format=crypt"
option. But it *should* be faster if you apply the patch above. So John can do
the SHA calculation internally rather than asking the OS to do it.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed July 21st, 2010 08:30:51 AM

Yeah compiling from source is pretty much my _only_ option on the cluster.

Everything else requires escalated permissions which I don't have,

Hopefully those patches will work just as well with the MPI version of John on
the cluster.

Ill update you later,

-Peng

UPDATE:

raw md5 is working now on the cluster, ran a test batch and it nailed a few
pretty damn quick.

will be doing more testing throughout the day.

UPDATE2:

Cluster time goes quick... we have a quota of 10000 hours Ran a test against a
bunch of md5 hashes for 3 minutes on 64 nodes thats 3.2 hours of cpu time. Must
keep this in mind.

ALTF4: I designate you the official word list and mangling rules compiler.

I have John up and running on here but I think you must have more experience
with it than I so I'll be depending on you for that kind of stuff.

Once you get all that together you can send me the files and the syntax to use
them and ill give them a test on my current md5 test set.

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue July 27th, 2010 09:17:39 PM

I'm going to try to come up with some manging rules, but the ones built in to
john are just really good. I'm having a hard time brainstorming ones to add.

As for running, it's pretty straightforward. To do a full brute force of all
alphanumeric passwords, do:

    ./john -incremental:Alnum PASSWORDFILE

You'll see the "Alnum" section defined in "john.conf" as follows:

    [Incremental:Alnum]
    File = $JOHN/alnum.chr
    MinLen = 1
    MaxLen = 8
    CharCount = 36

We may want to adjust that maxLength down to 6 or 7, though. 8 may take too long.

**QUICK MATH TIME**

You benchmarked our ASU supercomputer at 643964 c/s. Assuming md5. Miles may
vary for other hash algorithms. Let's say we're brute forcing all 6 character
passwords. That's 36 ^ 6 = 2, 176, 782, 336 total possible passwords. 2, 176,
782, 336 passwords / 643964 passwords/sec = 3, 380 seconds = **56 minutes**

Then bruting all 5 character passwords takes a mere **1.5 minutes**, and the
rest are negligible.

EDIT: Getting all length 7 passwords would be 36 hours. But if we can get 512
nodes instead of 64, it would only take 4.5

Plus, John's incremental mode tries words in an order most statistically likely
to hit real passwords first. As opposed to AAA, AAB, AAC, etc...


That will be a really good place to start. After doing that brute force, let's
look at the passwords which did crack and see if there are any patterns. Perhaps
a lot of them are the names of fish species, who knows?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu July 29th, 2010 08:33:47 PM

Quick results of a test run of rcracki_mt on the dual Xeon (16 cores), 40+GB RAM
processing server we got access to:

    statistics
    -------------------------------------------------------
    plaintext found:          10 of 14 (71.43%)
    total disk access time:   69.17 s
    total cryptanalysis time: 123.31 s
    total chain walk step:    1349595027
    total false alarm:        136623
    total chain walk step due to false alarm: 504585283

    result
    -------------------------------------------------------
    5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8        password        hex:70617373776f7264
    3f86be8cbe1fa89a27d47b9254cd3317bcd8d4df        god123          hex:676f64313233
    c8d7e65df4336a656dd4fe9af20c996941602ca4        123sex          hex:313233736578
    0641da2e677aab2dfa28a6faf370416aa655ac5a        asd fds         hex:61736420666473
    78aeea22d010b188a7047bc1fd7999affab9eb5c        bork it         hex:626f726b206974
    a4e737661ee0d4c91dfce65b60a44dad84ed15be        645 asdf        hex:3634352061736466
    2f187bd3c3a43c688fdcbb6b4a4d43346209bb84        lag 1337        hex:6c61672031333337
    ee41fbd75dfb4f1cfd776af34c47df04fc93f17a        1337h4x         hex:31333337683478
    62eb6601f8e794a95b3f67e5b6d5032b99cd851b        <notfound>      hex:<notfound>
    aa8172bc60688134e3acd8523c417ecc1287d316        <notfound>      hex:<notfound>
    112bb791304791ddcf692e29fd5cf149b35fea37        <notfound>      hex:<notfound>
    8be3c943b1609fffbfc51aad666d0a04adf83c9d        <notfound>      hex:<notfound>
    e8c97e07828db4388f219fe423e300c7fc74e370        65118713        hex:3635313138373133
    01446fa4f9609f569936ee46178b9f5630e6c1d1        b0rki7up        hex:6230726b69377570

Note: Those 4 it didn't find were purposefully made too complex for the rainbow tables.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu July 29th, 2010 08:43:02 PM

We're good to go.  I'll forward everyone a copy of the password list once
received.

> Thank you, your key has been successfully confirmed.
>
> You will receive a copy of the encrypted password list when the contest
> starts.
>
> Don't forget to stop by our table at DEFCON to get your registration
> code, so that your teams' scores will be posted on the contest website,
> and so that you can be eligible to win.

--------------------------------------------------------------------------------

Posted by **AltF4** on Fri July 30th, 2010 06:08:29 AM

Hey,

5 minutes in, and I've got 282 cracked. However, I'm having an issue with the
list. It's sorted by username, and not separated by hash type.

John does like that. It will only crack one type of hash per instance. It would
be awesome if we could have separate lists per hash type...

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri July 30th, 2010 09:03:31 PM

can i get the list forwarded to me at <terrordronev1@gmail.com>

--------------------------------------------------------------------------------

Posted by **Ghostshell** on Sat July 31st, 2010 10:27:14 AM

I'm at the con, have a room at the riv
