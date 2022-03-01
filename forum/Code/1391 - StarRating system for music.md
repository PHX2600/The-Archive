## Star/Rating system for music
Posted by **XlogicX** on Sat March 12th, 2011 05:55:38 AM

I'm thinking many of you can relate to this....

It's depressing how little I have listened to my music collection for the past while. I am obsessive with how much music I collect, which probably means that 85+% of my collection is garbage. Although it is all very neatly organized and I have listened to all the music I have atleast once (I don't just collect for the sake of it).

I also like putting a huge collection on random, but the dillema is the large balance of rubbish. I'm sure we're all familiar with this, but I don't want to be among the people that constantly push the skip button, its a bad habbit to form; as when the habit is in full effect, you may be inclined to skip 'ok' music (to get to the great stuff)...I like 'ok' music too though.

One solution to this is to use a rating/5-star system for my music, then all I'd have to do is filter it by say 3-stars or higher. But this rating system doesn't store the rating on the mp3/id3 tag istelf (at least for WMP, Winamp, and many other media players). The rating is stored on a database file locally to the computer. In most cases, your ratings are gone if you:
     *Rename the mp3
     *move the mp3
     *re-format your computer
     *or just want to bring your music to another computer

I do those above things often enough to make a rating system useless, I would be devistated to rate all that music and just lose my ratings. Sure you could attempt to backup the database file, but this only solves the re-format/different computer issues (assuming drive mappings are the same), this still doesn't fix renaming/moving.

I have heard the suggestion of just making up your own rating system and putting it in the comment field of the ID3 tag. Not to be picky, but I do like the convenience and visual aspect of the star rating in the library. Although, my solution to this whole problem does make use of the comment field a little.

Here's my method of Back-up/Restoration/Maintenance

[b:2amych1p]Backup:[/b:2amych1p]
I use the querying system in the Media Library of WinAmp. I backup 1, 2, 3, 4, and 5 star items seperately. So for all 1 star rated songs, I would query:
	```?rating=1```
I would do a 'select-all' on those items and edit the meta-data and change the comment to &quot;*&quot;. I would do this for rating 2, 3, 4, and 5 with **, ***, ****, and ***** (respectively).

[b:2amych1p]Restore:[/b:2amych1p]
This is very similar; query:
	```?comment=*```
Select-all on the items that come up and change the rating to 1-star. Repeat for **, ***, ****, and ***** to 2-star, 3-star, 4-star, and 5-star (respectively).

[b:2amych1p]Maintenance:[/b:2amych1p]
Eventually, all of your songs will have *'s in the comments, and depending on if you've backed up, some/most will have ratings. Sometimes I'm at a computer system where I know I'm not going to listen for very long, or don't want to install winamp (or import the music to the library). As a quicky, I will just put the *'s in the comment manually. Sometimes this practice can make the star to * balance inconnsistent. A quick check for this would be (using 5 stars for exampe)
	```?comment=***** AND !rating=5```
Everything that comes up is inconsistent
	```?rating=5 and !comment=&quot;*****&quot; OR rating=4 and !comment=&quot;****&quot; OR rating=3 and !comment=&quot;***&quot; OR rating=2 and !comment=&quot;**&quot; OR rating=1 and !comment=&quot;*&quot;``` should work as well (for a complete inconsistency check)


I know this may look overcomplicated, but it is actually really quick and simple. There may be a more elegant way to do this (but I haven't found it), but this is a hacker forum, this was my hack.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun March 13th, 2011 04:11:26 PM

That's beautiful.

I don't know anyone else who takes advantage of that comment field like that.

Good Work!
