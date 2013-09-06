## Dissecting Google Search Results (for Haystack Project)
Posted by **jargon** on Mon December 7th, 2009 02:52:38 PM

<http://www.phx2600.org/forum/viewtopic.php?f=11&t=1153>

**Dissecting Google Search Results (for Haystack Project)**

> **dxh wrote:**
>
> Hey everyone,
>
> I'm working on getting clickthrough obfuscation working for Haystack Project,
> but alas, that part is a bit harder than I figured it would be. As it turns
> out, simply going to the link with a Google cookie enabled isn't enough to
> register a clickthrough in your Google Search History. After grabbing the
> generated (read: optimized to the point of being nightmarish to read) html
> source code, it seems that they have a JavaScript function that rewrites the
> URL of a search result when clicked (left or right click, it happens on the
> onmousedown event). For example, before you click on a search result link, it
> looks like this:
>
>     <a class="l" onmousedown="return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')" href="http://helderribeiro.net/?tag=gpl" realurl="http://helderribeiro.net/?tag=gpl">
>
> After clicking on it (left or right), it looks like this.
>
>     <a class="l" onmousedown="return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')" href="/url?sa=t&source=web&ct=res&cd=2&ved=0CAsQFjAB&url=http%3A%2F%2Fhelderribeiro.net%2F%3Ftag%3Dgpl&ei=PZP_St_PDYy8sgPR2N2eCg&usg=AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg&sig2=o9xmv5ZAf-z4w1bYl7nbUQ" realurl="http://helderribeiro.net/?tag=gpl">
>
> My goal is to fake-navigate (set the source of an invisible iframe) to the URL
> in the second code block, but I have no idea where the rwt() fucntion is
> defined, and thus can't .click() the search result <aelement with only the
> generated html, which doesn't mention rwt() or even a .js file that might
> include it, thus driving me bananas.

> Any ideas, leet haxors? :geek:

**Re: Dissecting Google Search Results (for Haystack Project)**

> **dxh wrote:**
>
> If anyone wants to take a look at the whole result page's source, this is what
> Opera's DragonFly page inspector pulled up.
>
> <http://pastebin.com/f455a00ff>
>
> It seems that DragonFly found something useful that Firebug didn't seem to:
>
>     <script>google.y={};google.x=function(e,g){google.y[e.id]=[e,g];return false};window.rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window.event.srcElement;while(a){if(a.href)break;a=a.parentNode}}var b=encodeURIComponent||escape,c;c=a.href;var n=["/url?sa=t","\x26source\x3dweb",e?"&oi="+b(e):"",f?"&cad="+b(f):"","&ct=",b(j||"res"),"&cd=",b(k),"&ved=",b(m),"&url=",b(c).replace(/\+/g,"%2B"),"&ei=","PoIPS6elGZH-tQPviYTmAQ",g?"&usg="+g:"",l].join("");a.href=n;a.onmousedown=""}catch(o){}return true};
>     window.gbar={qs:function(){},tg:function(e){var o={id:'gbar'};for(i in e)o[i]=e[i];google.x(o,function(){gbar.tg(o)})}};
>     </script>
>
> Not exactly the most maintainable looking code to read, but its a start.

**Re: Dissecting Google Search Results (for Haystack Project)**

> **dxh wrote:**
>
> > **dxh wrote:**
> >
> > If anyone wants to take a look at the whole result page's source, this is what
> > Opera's DragonFly page inspector pulled up.
> >
> > <http://pastebin.com/f455a00ff>
> >
> > It seems that DragonFly found something useful that Firebug didn't seem to:
> >
> >     <script>google.y={};google.x=function(e,g){google.y[e.id]=[e,g];return false};window.rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window.event.srcElement;while(a){if(a.href)break;a=a.parentNode}}var b=encodeURIComponent||escape,c;c=a.href;var n=["/url?sa=t","\x26source\x3dweb",e?"&oi="+b(e):"",f?"&cad="+b(f):"","&ct=",b(j||"res"),"&cd=",b(k),"&ved=",b(m),"&url=",b(c).replace(/\+/g,"%2B"),"&ei=","PoIPS6elGZH-tQPviYTmAQ",g?"&usg="+g:"",l].join("");a.href=n;a.onmousedown=""}catch(o){}return true};
> >     window.gbar={qs:function(){},tg:function(e){var o={id:'gbar'};for(i in e)o[i]=e[i];google.x(o,function(){gbar.tg(o)})}};
> >     </script>
> >
> > Not exactly the most maintainable looking code to read, but its a start.
>
> FYI, if anyone can translate this ultra-optimized code into something readable
> and tell me what rwt()'s parameters are supposed to be, I will buy you coffee
> at the next meeting.

**Re: Dissecting Google Search Results (for Haystack Project)**

> **PHLAK wrote:**
>
> Just saw this post. I too have noticed the JS link swapping Google does on
> their search results pages and considered this pretty big vulnerability as a
> phishing tactic. As for getting the URL the way you're talking about I'll have
> to think about. Maybe we can go over it at the next meeting and (hopefully)
> come up with a solution. At the moment however, I do not have the time. I'll
> see if I can make some though, and let you know if I figure anything out.

**Re: Dissecting Google Search Results (for Haystack Project)**

> **dxh wrote:**
> TrackMeNot was able to get clickthrough obfuscation working at one point, but
> Google changed the code and its broken, according to one of their developers.
> They seem to have similar aims with HayProj, although their algorithms and
> technical goals seem slightly different.

Here is a by-hand indentation of the code I wrote up over the past 20 minutes:

	<script>
			google
		.
			y
	=
		{
		}
	;
			google
		.
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
				.
					y
			[
					e
				.
					id
			]
		=
			[
					e
				,
					g
			]
		;
		return
			false
		}
		;
				window
			.
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
							.
								event
							.
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
								.
									href
							)
								break
							;
								a
							=
									a
								.
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
							.
								href
						;
						var
							n
						=
							[
								"/url?sa=t"
							,
								"\x26source\x3dweb"
							,
									e
								?
										"&oi="
									+
										b
										(
											e
										)
								:
									""
							,
									f
								?
										"&cad="
									+
										b
										(
											f
										)
								:
									""
							,
								"&ct="
							,
								b
								(
										j
									||
										"res"
								)
							,
								"&cd="
							,
								b
								(
									k
								)
							,
								"&ved="
							,
								b
								(
									m
								)
							,
								"&url="
							,
									b
									(
										c
									)
								.
									replace
									(
										/\+/g
									,
										"%2B"
									)
							,
								"&ei="
							,
								"PoIPS6elGZH-tQPviYTmAQ"
							,
									g
								?
										"&usg="
									+
										g
								:
									""
							,
								l
							]
						.
							join
							(
								""
							)
						;
								a
							.
								href
						=
							n
						;
								a
							.
								onmousedown
						=
							""
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
					.
						gbar
				=
				{
						qs
					:
						function
						(
						)
						{
						}
					,
						tg
					:
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
									:
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
							[
								i
							]
						=
							e
							[
								i
							]
						;
								google
							.
								x
						(
							o
						,
							function
							(
							)
							{
										gbar
									.
										tg
								(
									o
								)
					}
				)
			}
		}
	;
	</script>

If you want the code comments, call to send up an appointment to meet me at
Unlimited Coffee and give me 50.00 USD in cash up-front no-questions-asked when
you arrive. (480 323 8892)

-- T.R.Keal alias jargon
<http://thekealshow.com/>

--------------------------------------------------------------------------------

Posted by **dxh** on Mon December 7th, 2009 07:20:44 PM

![](http://imgur.com/puRUJ.jpg)

Beat ya to the chase, yo. ;) Looks like we'll have a click-through capable
HayProj implementation by Kwanzaa! :D

--------------------------------------------------------------------------------

Posted by **jargon** on Mon December 7th, 2009 09:11:23 PM

> **dxh wrote:**
>
> ![](http://imgur.com/puRUJ.jpg)
>
> Beat ya to the chase, yo. ;) Looks like we'll have a click-through capable
> HayProj implementation by Kwanzaa! :D

I respect Kwanzaa, but not its inventor.

He beat the crap and tortured two women to make the end justify the means.

He embodied the cultural revolution version of Stalin/Hitler WWII "super
science".

I don't like the man one bit.

Kwanzaa is a good thing, the man is not.

Btw, I would have detailed it all in full detail if you had simply convinced
Eric to go with me shoe shopping since I don't know where to find good
Vans/Airwalk/Converse style shoes.

All I really wanted out of the deal was a pair of size 10 1/2 shoes and 6 to
twelve pairs of socks since I don't want my feet to wither away and die this
Winter. (All I have are 3 shoddy worn out pairs of socks and a pair of open-foot
sandals.)

My mom would have given me the money, for the shoes had Eric simply agreed to
take me out to his shoe hunt haunts.

Plus Eric needs new shoes anyhoo.

That indented code really is my own work in 20 minutes time, and it is indeed
flawlessly indented in order to create a complete nesting-trace.

If you are worried about me being a nutter. I am nowhere near the nutter that
other dude I met that you know from conventions.

I just want some good shoes and six to twelve pairs of decent toed socks out of
the deal of offering the injection expertise.

(I am pretty sure I know a hijack or two to inject backwards into prior to page
loading via forced re-cache, which is what would have to be done in-order to
thwart the new method which defeated the older TrackMeNot methodology. This is
why Opera's Dragonfly page inspector saw something that Firefox's Firebug
script debugger did not.)

You want deeper insight than this, convince XlogicX to take me with him
shoe/sock shopping.

-- T.R.Keal alias jargon (480 323 8892) <http://thekealshow.com/>

--------------------------------------------------------------------------------

Posted by **dxh** on Mon December 7th, 2009 09:42:37 PM

> **jargon wrote:**

> (I am pretty sure I know a hijack or two to inject backwards into prior to
> page loading via forced re-cache, which is what would have to be done in-order
> to thwart the new method which defeated the older TrackMeNot methodology. This
> is why Opera's Dragonfly page inspector saw something that Firefox's Firebug
> script debugger did not.)
>
> You want deeper insight than this, convince XlogicX to take me with him
> shoe/sock shopping.
>
> -- T.R.Keal alias jargon (480 323 8892) <http://thekealshow.com/>

No need to; The rwt code has been re-engineered to work in HayProj.  Plus I have
no idea how to convince any straight man to go shoe-shopping with someone
lacking boobs.
