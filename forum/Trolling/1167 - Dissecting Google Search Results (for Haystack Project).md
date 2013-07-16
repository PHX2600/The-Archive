## Dissecting Google Search Results (for Haystack Project)
Posted by **jargon** on Mon December 7th, 2009 02:52:38 PM

[url:2ptvvca3]http&#58;//www&#46;phx2600&#46;org/forum/viewtopic&#46;php?f=11&amp;t=1153[/url:2ptvvca3]

[b:2ptvvca3]Dissecting Google Search Results (for Haystack Project)[/b:2ptvvca3]

[quote=&quot;dxh&quot;:2ptvvca3]
Hey everyone,

I'm working on getting clickthrough obfuscation working for Haystack Project, but alas, that part is a bit harder than I figured it would be. As it turns out, simply going to the link with a Google cookie enabled isn't enough to register a clickthrough in your Google Search History. After grabbing the generated (read: optimized to the point of being nightmarish to read) html source code, it seems that they have a JavaScript function that rewrites the URL of a search result when clicked (left or right click, it happens on the onmousedown event). For example, before you click on a search result link, it looks like this:

[code:2ptvvca3]
&lt;a class=&quot;l&quot; onmousedown=&quot;return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')&quot; href=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot; realurl=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot;&gt;
[/code:2ptvvca3]

After clicking on it (left or right), it looks like this.

[code:2ptvvca3]
&lt;a class=&quot;l&quot; onmousedown=&quot;return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')&quot; href=&quot;/url?sa=t&amp;source=web&amp;ct=res&amp;cd=2&amp;ved=0CAsQFjAB&amp;url=http%3A%2F%2Fhelderribeiro&#46;net%2F%3Ftag%3Dgpl&amp;ei=PZP_St_PDYy8sgPR2N2eCg&amp;usg=AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ&quot; realurl=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot;&gt;
[/code:2ptvvca3]

My goal is to fake-navigate (set the source of an invisible iframe) to the URL in the second code block, but I have no idea where the rwt() fucntion is defined, and thus can't .click() the search result &lt;a&gt; element with only the generated html, which doesn't mention rwt() or even a .js file that might include it, thus driving me bananas.

Any ideas, leet haxors? <!-- s:geek: --><img src="{SMILIES_PATH}/icon_e_geek.gif" alt=":geek:" title="Geek" /><!-- s:geek: -->
[/quote:2ptvvca3]

[b:2ptvvca3]Re: Dissecting Google Search Results (for Haystack Project)[/b:2ptvvca3]

[quote=&quot;dxh&quot;:2ptvvca3]
If anyone wants to take a look at the whole result page's source, this is what Opera's DragonFly page inspector pulled up.

[url:2ptvvca3]http&#58;//pastebin&#46;com/f455a00ff[/url:2ptvvca3]

It seems that DragonFly found something useful that Firebug didn't seem to:

[code:2ptvvca3]
&lt;script&gt;google&#46;y={};google&#46;x=function(e,g){google&#46;y&#91;e&#46;id&#93;=&#91;e,g&#93;;return false};window&#46;rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window&#46;event&#46;srcElement;while(a){if(a&#46;href)break;a=a&#46;parentNode}}var b=encodeURIComponent||escape,c;c=a&#46;href;var n=&#91;&quot;/url?sa=t&quot;,&quot;\x26source\x3dweb&quot;,e?&quot;&amp;oi=&quot;+b(e)&#58;&quot;&quot;,f?&quot;&amp;cad=&quot;+b(f)&#58;&quot;&quot;,&quot;&amp;ct=&quot;,b(j||&quot;res&quot;),&quot;&amp;cd=&quot;,b(k),&quot;&amp;ved=&quot;,b(m),&quot;&amp;url=&quot;,b(c)&#46;replace(/\+/g,&quot;%2B&quot;),&quot;&amp;ei=&quot;,&quot;PoIPS6elGZH-tQPviYTmAQ&quot;,g?&quot;&amp;usg=&quot;+g&#58;&quot;&quot;,l&#93;&#46;join(&quot;&quot;);a&#46;href=n;a&#46;onmousedown=&quot;&quot;}catch(o){}return true};
window&#46;gbar={qs&#58;function(){},tg&#58;function(e){var o={id&#58;'gbar'};for(i in e)o&#91;i&#93;=e&#91;i&#93;;google&#46;x(o,function(){gbar&#46;tg(o)})}};
&lt;/script&gt;
[/code:2ptvvca3]

Not exactly the most maintainable looking code to read, but its a start.
[/quote:2ptvvca3]

[b:2ptvvca3]Re: Dissecting Google Search Results (for Haystack Project)[/b:2ptvvca3]

[quote=&quot;dxh&quot;:2ptvvca3]

[quote=&quot;dxh&quot;:2ptvvca3]

[code:2ptvvca3]
&lt;script&gt;google&#46;y={};google&#46;x=function(e,g){google&#46;y&#91;e&#46;id&#93;=&#91;e,g&#93;;return false};window&#46;rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window&#46;event&#46;srcElement;while(a){if(a&#46;href)break;a=a&#46;parentNode}}var b=encodeURIComponent||escape,c;c=a&#46;href;var n=&#91;&quot;/url?sa=t&quot;,&quot;\x26source\x3dweb&quot;,e?&quot;&amp;oi=&quot;+b(e)&#58;&quot;&quot;,f?&quot;&amp;cad=&quot;+b(f)&#58;&quot;&quot;,&quot;&amp;ct=&quot;,b(j||&quot;res&quot;),&quot;&amp;cd=&quot;,b(k),&quot;&amp;ved=&quot;,b(m),&quot;&amp;url=&quot;,b(c)&#46;replace(/\+/g,&quot;%2B&quot;),&quot;&amp;ei=&quot;,&quot;PoIPS6elGZH-tQPviYTmAQ&quot;,g?&quot;&amp;usg=&quot;+g&#58;&quot;&quot;,l&#93;&#46;join(&quot;&quot;);a&#46;href=n;a&#46;onmousedown=&quot;&quot;}catch(o){}return true};
window&#46;gbar={qs&#58;function(){},tg&#58;function(e){var o={id&#58;'gbar'};for(i in e)o&#91;i&#93;=e&#91;i&#93;;google&#46;x(o,function(){gbar&#46;tg(o)})}};
&lt;/script&gt;
[/code:2ptvvca3]

Not exactly the most maintainable looking code to read, but its a start.
[/quote:2ptvvca3]

FYI, if anyone can translate this ultra-optimized code into something readable and tell me what rwt()'s parameters are supposed to be, I will buy you coffee at the next meeting.
[/quote:2ptvvca3]

[b:2ptvvca3]Re: Dissecting Google Search Results (for Haystack Project)[/b:2ptvvca3]

[quote=&quot;PHLAK&quot;:2ptvvca3]
Just saw this post. I too have noticed the JS link swapping Google does on their search results pages and considered this pretty big vulnerability as a phishing tactic. As for getting the URL the way you're talking about I'll have to think about. Maybe we can go over it at the next meeting and (hopefully) come up with a solution. At the moment however, I do not have the time. I'll see if I can make some though, and let you know if I figure anything out.
[/quote:2ptvvca3]


[b:2ptvvca3]Re: Dissecting Google Search Results (for Haystack Project)[/b:2ptvvca3]

[quote=&quot;dxh&quot;:2ptvvca3]
TrackMeNot was able to get clickthrough obfuscation working at one point, but Google changed the code and its broken, according to one of their developers. They seem to have similar aims with HayProj, although their algorithms and technical goals seem slightly different.
[/quote:2ptvvca3]

Here is a by-hand indentation of the code I wrote up over the past 20 minutes:

[code:2ptvvca3]
&lt;script&gt;
		google
	&#46;
		y
=
	{
	}
;
		google
	&#46;
		x
=
	function
	(
			e
		,
			g
	)
	{
				google
			&#46;
				y
		&#91;
				e
			&#46;
				id
		&#93;
	=
		&#91;
				e
			,
				g
		&#93;
	;
	return
		false
	}
	;
			window
		&#46;
			rwt
	=
		function
		(
			a
		,
			e
		,
			f
		,
			j
		,
			k
		,
			g
		,
			l
		,
			m
		)
		{
			try
			{
				if
				(
						a
					===
						window
				)
				{
						a
					=
							window
						&#46;
							event
						&#46;
							srcElement
					;
					while
					(
						a
					)
					{
						if
						(
								a
							&#46;
								href
						)
							break
						;
							a
						=
								a
							&#46;
								parentNode
						}
					}
						var
							b
						=
								encodeURIComponent
							||
								escape
					,
						c
					;
						c
					=
							a
						&#46;
							href
					;
					var
						n
					=
						&#91;
							&quot;/url?sa=t&quot;
						,
							&quot;\x26source\x3dweb&quot;
						,
								e
							?
									&quot;&amp;oi=&quot;
								+
									b
									(
										e
									)
							&#58;
								&quot;&quot;
						,
								f
							?
									&quot;&amp;cad=&quot;
								+
									b
									(
										f
									)
							&#58;
								&quot;&quot;
						,
							&quot;&amp;ct=&quot;
						,
							b
							(
									j
								||
									&quot;res&quot;
							)
						,
							&quot;&amp;cd=&quot;
						,
							b
							(
								k
							)
						,
							&quot;&amp;ved=&quot;
						,
							b
							(
								m
							)
						,
							&quot;&amp;url=&quot;
						,
								b
								(
									c
								)
							&#46;
								replace
								(
									/\+/g
								,
									&quot;%2B&quot;
								)
						,
							&quot;&amp;ei=&quot;
						,
							&quot;PoIPS6elGZH-tQPviYTmAQ&quot;
						,
								g
							?
									&quot;&amp;usg=&quot;
								+
									g
							&#58;
								&quot;&quot;
						,
							l
						&#93;
					&#46;
						join
						(
							&quot;&quot;
						)
					;
							a
						&#46;
							href
					=
						n
					;
							a
						&#46;
							onmousedown
					=
						&quot;&quot;
				}
				catch
				(
					o
				)
				{
				}
				return
					true
				}
			;
					window
				&#46;
					gbar
			=
			{
					qs
				&#58;
					function
					(
					)
					{
					}
				,
					tg
				&#58;
					function
					(
						e
					)
					{
							var
								o
						=
							{
									id
								&#58;
									'gbar'
							}
					;
					for
					(
							i
						in
							e
					)
							o
						&#91;
							i
						&#93;
					=
						e
						&#91;
							i
						&#93;
					;
							google
						&#46;
							x
					(
						o
					,
						function
						(
						)
						{
									gbar
								&#46;
									tg
							(
								o
							)
				}
			)
		}
	}
;
&lt;/script&gt;
[/code:2ptvvca3]

If you want the code comments, call to send up an appointment to meet me at Unlimited Coffee and give me 50.00 USD in cash up-front no-questions-asked when you arrive. (480 323 8892)

-- T.R.Keal alias jargon
[url:2ptvvca3]http&#58;//thekealshow&#46;com/[/url:2ptvvca3]

--------------------------------------------------------------------------------

Posted by **dxh** on Mon December 7th, 2009 07:20:44 PM

[img:2a7w4r5d]http&#58;//imgur&#46;com/puRUJ&#46;jpg[/img:2a7w4r5d]

Beat ya to the chase, yo. <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->  Looks like we'll have a click-through capable HayProj implementation by Kwanzaa! <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->

--------------------------------------------------------------------------------

Posted by **jargon** on Mon December 7th, 2009 09:11:23 PM

[quote=&quot;dxh&quot;:ilbddihz][img:ilbddihz]http&#58;//imgur&#46;com/puRUJ&#46;jpg[/img:ilbddihz]

Beat ya to the chase, yo. <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->  Looks like we'll have a click-through capable HayProj implementation by Kwanzaa! <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->[/quote:ilbddihz]

I respect Kwanzaa, but not its inventor.

He beat the crap and tortured two women to make the end justify the means.

He embodied the cultural revolution version of Stalin/Hitler WWII &quot;super science&quot;.

I don't like the man one bit.

Kwanzaa is a good thing, the man is not.

Btw, I would have detailed it all in full detail if you had simply convinced Eric to go with me shoe shopping since I don't know where to find good Vans/Airwalk/Converse style shoes.

All I really wanted out of the deal was a pair of size 10 1/2 shoes and 6 to twelve pairs of socks since I don't want my feet to wither away and die this Winter. (All I have are 3 shoddy worn out pairs of socks and a pair of open-foot sandals.)

My mom would have given me the money, for the shoes had Eric simply agreed to take me out to his shoe hunt haunts.

Plus Eric needs new shoes anyhoo.

That indented code really is my own work in 20 minutes time, and it is indeed flawlessly indented in order to create a complete nesting-trace.

If you are worried about me being a nutter. I am nowhere near the nutter that other dude I met that you know from conventions.

I just want some good shoes and six to twelve pairs of decent toed socks out of the deal of offering the injection expertise.

(I am pretty sure I know a hijack or two to inject backwards into prior to page loading via forced re-cache, which is what would have to be done in-order to thwart the new method which defeated the older TrackMeNot methodology. This is why Opera's Dragonfly page inspector saw something that Firefox's Firebug script debugger did not.)

You want deeper insight than this, convince XlogicX to take me with him shoe/sock shopping.

-- T.R.Keal alias jargon (480 323 8892)
<!-- m --><a class="postlink" href="http://thekealshow.com/">http://thekealshow.com/</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **dxh** on Mon December 7th, 2009 09:42:37 PM

[quote=&quot;jargon&quot;:b43g6nlm]
(I am pretty sure I know a hijack or two to inject backwards into prior to page loading via forced re-cache, which is what would have to be done in-order to thwart the new method which defeated the older TrackMeNot methodology. This is why Opera's Dragonfly page inspector saw something that Firefox's Firebug script debugger did not.)

You want deeper insight than this, convince XlogicX to take me with him shoe/sock shopping.

-- T.R.Keal alias jargon (480 323 8892)
<!-- m --><a class="postlink" href="http://thekealshow.com/">http://thekealshow.com/</a><!-- m -->[/quote:b43g6nlm]

No need to; The rwt code has been re-engineered to work in HayProj.  Plus I have no idea how to convince any straight man to go shoe-shopping with someone lacking boobs.
