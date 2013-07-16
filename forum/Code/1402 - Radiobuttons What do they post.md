## Radiobuttons: What do they post?
Posted by **fightgar** on Fri May 13th, 2011 11:16:58 PM

Let's find out.

--------------------------------------------------------------------------------

Posted by **fightgar** on Fri May 13th, 2011 11:28:37 PM

vote_id%5B%5D=3
vote_id[]=3
vote_id is the &quot;name&quot; attribute, 3 is the &quot;value&quot; ... well that's screwy, that's what I thought, but it's still not working.  Sorry for the noise.  If I fix it, I'll let people know the problem and the solution.

--------------------------------------------------------------------------------

Posted by **fightgar** on Fri May 13th, 2011 11:37:11 PM

[code:68gfixtb]&lt;input type=&quot;radio&quot; name=&quot;U2FsdGVkX18zMTA5MzMxMGD1yeFFuiq_uMo0vaCagR0cEja-7SlJGxBmsW7sSN-0avwVyt8O&#58;-pk&quot; value=&quot;A&quot; id=&quot;A&quot; tabindex=&quot;1&quot;&gt;
	hide
&lt;/label&gt;

&lt;label class=&quot;req&quot; title=&quot;craigslist will anonymize your email address&quot;&gt;
	&lt;input type=&quot;radio&quot; name=&quot;U2FsdGVkX18zMTA5MzMxMGD1yeFFuiq_uMo0vaCagR0cEja-7SlJGxBmsW7sSN-0avwVyt8O&#58;-pk&quot; value=&quot;C&quot; checked tabindex=&quot;1&quot;&gt;[/code:68gfixtb]

So... yeah I set that long-ass name to A and it doesn't think it's checked, if I set it to C the HTML there says it's checked, and it goes through just fine... whatever just weird, its an HTTPS connection, so I can't sniff it easily from my interface with wireshark, I could use burp... if I were on a windows machine.

What's a burp-like app for linux?
