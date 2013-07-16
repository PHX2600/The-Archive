## Backup - Best Practices
Posted by **HalfSight** on Mon August 2nd, 2010 10:49:50 AM

Symantec Backup Exec 11d &amp; Veritas, hate this software, Pretty sure I need new Tape drives that handle bigger media loads. 

Anybody else deal with backups, Is tape still the best practice for huge loads of info any suggestions? Any tips on backup exec? Fuckers keep popping the tapes out and giving errors and failing. I have One running on a second tape now, so that will be a 2 tape backup. <!-- s:evil: --><img src="{SMILIES_PATH}/icon_evil.gif" alt=":evil:" title="Evil or Very Mad" /><!-- s:evil: -->  <!-- s:evil: --><img src="{SMILIES_PATH}/icon_evil.gif" alt=":evil:" title="Evil or Very Mad" /><!-- s:evil: -->  <!-- s:evil: --><img src="{SMILIES_PATH}/icon_evil.gif" alt=":evil:" title="Evil or Very Mad" /><!-- s:evil: -->

This is what a new tape drive costs:

3,390.00

--------------------------------------------------------------------------------

Posted by **Konshu** on Mon August 2nd, 2010 04:09:13 PM

[url:15xsc71i]http&#58;//www&#46;mozy&#46;com[/url:15xsc71i]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon August 2nd, 2010 04:18:54 PM

<!-- m --><a class="postlink" href="http://www.bacula.org/en/">http://www.bacula.org/en/</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **HalfSight** on Mon August 2nd, 2010 04:32:23 PM

The Head Partner of the Firm doesn't want backups in the cloud and it is for windows servers. And I like the looks of bacula, just not sure if the admin would like it.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue August 3rd, 2010 11:04:27 AM

When it comes to backups of important data, I've always liked the 3-2-1 backup strategy:

[list:kx2m9ajo]
[*:kx2m9ajo]Have (at least) 3 copies of anything you don't want to loose.[/*:m:kx2m9ajo]
[*:kx2m9ajo]Use at least 2 different types of media*[/*:m:kx2m9ajo]
[*:kx2m9ajo]Always have 1 copy of the data off-site[/*:m:kx2m9ajo][/list:u:kx2m9ajo]
*[size=85:kx2m9ajo] This will protect you if one type of media becomes obsolete or is unable to be read.[/size:kx2m9ajo]

Some other good practices:
[list:kx2m9ajo]
[*:kx2m9ajo]The only good backup is an automated backup.  If your backup relies on a human to start it, it IS NOT reliable.[/*:m:kx2m9ajo]
[*:kx2m9ajo]Have multiple scheduled backups if possible (ie - Daily, Weekly, Monthly).  You can then leave the daily backups in the office in the event of a time-sensitive emergency, and store the weekly/monthly backups off-site (at the bosses home maybe)[/*:m:kx2m9ajo]
[*:kx2m9ajo]While a RAID is a good idea for mission-critical data, IT IS NOT A BACKUP SOLUTION.[/*:m:kx2m9ajo]
[*:kx2m9ajo]DO NOT store all of your backups in the same location.  Sure having backups will protect against accidental deletion or hardware failures, but what happens when there's a fire in the office?[/*:m:kx2m9ajo][/list:u:kx2m9ajo]

I know you said your boss doesn't want to use an in-the-cloud backup solution, but these are truly a viable solution.  If you are unable to convince him of the security/reliability of these services, you can always use a company owned, off-site server or purchase one.  If he doesn't want to spend the money, paint him a picture of what would happen if this data was lost.  While hardware, and even people, are expendable, it's the companies data that is valuable.  Without this data, the company would be out of business.  Don't be cheap when it comes to your companies data.

As for the media to store your data on, the only other (semi-reasonable) option I can think of would be external hard drives.

--------------------------------------------------------------------------------

Posted by **Konshu** on Sat August 7th, 2010 01:25:15 AM

yeah I use the same method, however my offsite is through a cloud, only one big enough to hold large clusters of .7z files <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->
