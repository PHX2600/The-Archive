## Crack Me If You Can
Posted by **AltF4** on Tue June 14th, 2011 11:18:38 PM

Last year, Phx2600 participated in the Crack Me If You Can competition at Defcon 18 and took 8th place. A very good showing, but we knew we could do better.

The competition is on! Let's start preparing our machines / strategies / personnel.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed June 15th, 2011 09:48:33 AM

I'll start tinkering with the cluster

We should rebuild our tables, 

I'll start pulling MD5 and SHA1 from <!-- m --><a class="postlink" href="http://www.freerainbowtables.com/en/tables/">http://www.freerainbowtables.com/en/tables/</a><!-- m -->

Maybe PHLAK or someone could start pulling NTLM and LM?

--------------------------------------------------------------------------------

Posted by **AltF4** on Wed June 15th, 2011 12:58:08 PM

I'm in the process of trying out the tables from FreeRainbowTables.com, too. Just as a &quot;see if I can get the damn thing to work&quot; sort of exercise. We should definitely divide out the effort though. For the ASU cluster, maybe hashcat will work better? It seems to support multithreading out of the box, unlike John.

We can practice against last year's hash list, and maybe others. (gawker database?)

--------------------------------------------------------------------------------

Posted by **nak** on Wed June 15th, 2011 03:59:08 PM

maybe this will get me to actually learn VHDL or whatever for that xilinx fpga.  Once we get more details I guess we could start planning something along the lines of:
1) Run fastest method first (my guess would be rainbow tables)
2) Run the cluster, maybe have it give up on hashes after spending a certain amount of time on them (?? not sure if that can be setup easily or if that's how it works, I saw the word &quot;multithreading&quot; so it might not be that simple)
3) for hashes that are taking too many flops (lol jk) from the cluster we could then have a script pass the tough ones to the FPGA (if we can figure out how to get a MD5 craxor running on it, or whatever algo we need running on it... I know some dude in Germany, same guy who runs/did the SUMP logical analyzer project[the main reason I got this spartan 3 board] wrote some magic to crack md5 hashes with the FPGA... but took it down due to fascist computer law)

That's all my ideas, and probably a lil' too wordy, but hey... typing is fun <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed June 15th, 2011 06:04:28 PM

[quote=&quot;nak&quot;:3io5tzlc]maybe this will get me to actually learn VHDL or whatever for that xilinx fpga.  Once we get more details I guess we could start planning something along the lines of:
1) Run fastest method first (my guess would be rainbow tables)
2) Run the cluster, maybe have it give up on hashes after spending a certain amount of time on them (?? not sure if that can be setup easily or if that's how it works, I saw the word &quot;multithreading&quot; so it might not be that simple)
3) for hashes that are taking too many flops (lol jk) from the cluster we could then have a script pass the tough ones to the FPGA (if we can figure out how to get a MD5 craxor running on it, or whatever algo we need running on it... I know some dude in Germany, same guy who runs/did the SUMP logical analyzer project[the main reason I got this spartan 3 board] wrote some magic to crack md5 hashes with the FPGA... but took it down due to fascist computer law)

That's all my ideas, and probably a lil' too wordy, but hey... typing is fun <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->[/quote:3io5tzlc]


Do it fgt.

--------------------------------------------------------------------------------

Posted by **AltF4** on Wed June 15th, 2011 07:50:21 PM

Got word from the official Defcon source that Crack Me If You Can is approved for this year again. Sweet! Let's do this.

What was that crazy machine that Matt had last year?

EDIT: For those of you trying out the rainbow tables here: <!-- m --><a class="postlink" href="http://www.freerainbowtables.com/en/tables/">http://www.freerainbowtables.com/en/tables/</a><!-- m -->

The naming scheme on the tables tripped me up for a little while until Penguin set me straight. It can be a little confusing. The table I downloaded was &quot;md5_hybrid(loweralpha#6-6,numeric#1-3)&quot; Which means it cracks only passwords with lower case alphabetic exactly 6 characters, followed by exactly three numeric digits. Examples:

dhbfrt567
paswrd123

etc...

I was trying &quot;password&quot; and &quot;lol&quot; and not getting hits, wondering why. There you go.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun June 19th, 2011 09:01:10 PM

It was Zapperlink that provided the machine, and I was operating it (my name isn't Matt, btw).  Not sure if we'll get that box again or not.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon June 20th, 2011 01:33:44 PM

Does anyone have the hash lists from last year so we can start doing some testing and fiddling.

I want to write a script that will auto sort/format the hashes this year. Last year it took us way to long to determine what was ntlm/md5 etc.

nomorenewbmistakesplz

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu June 23rd, 2011 01:15:02 PM

Was the list not in that archive I gave you?

--------------------------------------------------------------------------------

Posted by **blazerx** on Sat July 30th, 2011 06:39:09 AM

hello. First Timer here

I came across this page from googling &quot;Crack me if you can&quot; 2011 as I was curious as to whether there any teams recruiting members for this years defcon &quot;Crack me if you can&quot; challenge. BTW grats for last year, i didn't find any teams to join so didn't participate, but wanted to.

While reading through your posts here is a quick word of advice (I'm a regular at FreeRainbowTables (same user name)), anyhow I would just like to say that use Rainbow tables as a last resort unless you are running them off RAID/SSDs, each file under the RTI2 format takes roughly ~9 seconds to load on a standard system. Also check the bruteforce point of the table you are using, this indicates the maximum number of hashes the table is useful to crack before brute-forcing becomes quicker. So probably use all other means before RTs. 

Tip: Also if you guys are downloading tables remember to get the newly released ones which use the RTI2 format as they are packed better than the RTI format saving considerable space.

Good luck this year guys.

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon August 1st, 2011 12:23:27 PM

Official Website is up:
<!-- m --><a class="postlink" href="http://contest.korelogic.com/">http://contest.korelogic.com/</a><!-- m -->

I'll take care of registration and submissions. So send me your cracked passwords during the competition. However you want is fine, email, in person, whatever.

--------------------------------------------------------------------------------

Posted by **blazerx** on Mon August 8th, 2011 02:21:21 AM

hey guys, a very commendable effort this year. It was damn challenging i might add.

I rolled with insidepro team 2011 and would like to share our cracked password statistics.

Cracked password by:

[b:1w2ix08u]Length:[/b:1w2ix08u]
[url=http://imgur.com/cyvlA]

[b:1w2ix08u]Charset:[/b:1w2ix08u]
[url=http://imgur.com/76y7G]

[b:1w2ix08u]Cracked vs Uncracked[/b:1w2ix08u]
[url=http://imgur.com/cEeYV]


See you guys next year.
