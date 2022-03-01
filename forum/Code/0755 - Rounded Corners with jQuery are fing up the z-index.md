## Rounded Corners with jQuery are f***ing up the z-index
Posted by **PHLAK** on Sat February 28th, 2009 05:39:36 PM

I'm looking for someone with a bit of jQuery knowledge that can perhaps help me solve a problem.  I'm using jQuery and the jQuery Corners plugin to round the corners on <http&#58;//chronostudios&#46;com/5&#46;0/>.  If you take note to the navigation menu at the top right you can hover over the top 2/3 of the link and click them, however the bottom 1/3 does nothing when hovering or clicking.

I've narrowed this down to a problem with the rounded corners of the parent div (the black header box) being overlayed on top of the navigation menu.  If I disable JavaScript from the page the problem goes away.  I have attempted to manually set the z-index of both the navigation bar and the parent div, but alas, nothing changed.

Anyone have any other ideas?  A solution would be most appreciated!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun March 1st, 2009 01:06:43 PM

I'm an idiot and somehow didn't try (or missed it if I did) to stick a &quot;z-index: 1;&quot; on the navigation menu.  Now it seems to be working, huzzah!

--------------------------------------------------------------------------------

Posted by **fightgar** on Mon March 2nd, 2009 11:11:10 AM

Functionality Increase: 67%
