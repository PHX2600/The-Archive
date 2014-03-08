## Circuit Layout Software
Posted by **Ugly** on Fri December 24th, 2010 06:08:30 PM

So, I've laid out the schematic for a tube amplifier using geda. I arranged the
components in a manner mirroring their physical placement in the device but now
I'd like to move them around and try to group them in a more functional fashion.
This proves difficult as geda does not reroute traces at all, it simply
maintains the terminal connections with the shortest straight lines, leading to
all manner of crazy fun and extra work.

Does anyone know of a free (as in beer) schematic design program that supports
automatically rerouting interconnects? This does not have to be PCB design
software, no digital logic is required at all and the traces do not need to be
optimal, they just need to stay off each other as components are re-arranged.The
ability to import from geda would be nice, but I would gladly re-diagram it in
the new program if necessary. Suggestions?

On a side note, who the hell gave me the Boy Toy Bill Gates picture?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sat December 25th, 2010 10:36:34 AM

Eagle PCB is my fav.

Does logical schematics then will route your traces for you in physical
placement.

Pretty sweet!

<http://www.cadsoftusa.com/download.htm>

Merry Christmas!

--------------------------------------------------------------------------------

Posted by **Ugly** on Tue December 28th, 2010 08:47:46 PM

You know, that kept coming up in my searches and I skipped over it because I
didn't need to do actual board layout and was under the impression the board
size limit applied to schematics as well. Nice to see that's not true. Now to
find out if schematic traces re-route when I move components...

Looks like it drags them point to point in the shortest line like geda but at
least there is an option to break the trace and correct it in place without
recreating it from scratch. Not quite what I was hoping for but it should be
enough to accomplish my goal without making me contemplate suicide.
