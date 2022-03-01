## Dissecting Google Search Results (for Haystack Project)
Posted by **dxh** on Sun November 15th, 2009 12:16:08 PM

Hey everyone,

I'm working on getting clickthrough obfuscation working for Haystack Project, but alas, that part is a bit harder than I figured it would be.  As it turns out, simply going to the link with a Google cookie enabled isn't enough to register a clickthrough in your Google Search History.  After grabbing the generated (read: optimized to the point of being nightmarish to read) html source code, it seems that they have a JavaScript function that rewrites the URL of a search result when clicked (left or right click, it happens on the onmousedown event).  For example, before you click on a search result link, it looks like this:

```
&lt;a class=&quot;l&quot; onmousedown=&quot;return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')&quot; href=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot; realurl=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot;&gt;
```			
After clicking on it (left or right), it looks like this.

```
&lt;a class=&quot;l&quot; onmousedown=&quot;return rwt(this,'','','res','2','AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg','&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ','0CAsQFjAB')&quot; href=&quot;/url?sa=t&amp;source=web&amp;ct=res&amp;cd=2&amp;ved=0CAsQFjAB&amp;url=http%3A%2F%2Fhelderribeiro&#46;net%2F%3Ftag%3Dgpl&amp;ei=PZP_St_PDYy8sgPR2N2eCg&amp;usg=AFQjCNES_tkCImLOf7awY5kS_uhn9a3Ryg&amp;sig2=o9xmv5ZAf-z4w1bYl7nbUQ&quot; realurl=&quot;http&#58;//helderribeiro&#46;net/?tag=gpl&quot;&gt;
```
My goal is to fake-navigate (set the source of an invisible iframe) to the URL in the second code block, but I have no idea where the rwt() fucntion is defined, and thus can't .click() the search result &lt;a&gt; element with only the generated html, which doesn't mention rwt() or even a .js file that might include it, thus driving me bananas.

Any ideas, leet haxors?  <!-- s:geek: --><img src="{SMILIES_PATH}/icon_e_geek.gif" alt=":geek:" title="Geek" /><!-- s:geek: -->

--------------------------------------------------------------------------------

Posted by **dxh** on Fri November 27th, 2009 12:30:08 AM

If anyone wants to take a look at the whole result page's source, this is what Opera's DragonFly page inspector pulled up.

<http&#58;//pastebin&#46;com/f455a00ff>

It seems that DragonFly found something useful that Firebug didn't seem to:

[code:34609mxw]
&lt;script&gt;google&#46;y={};google&#46;x=function(e,g){google&#46;y&#91;e&#46;id&#93;=&#91;e,g&#93;;return false};window&#46;rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window&#46;event&#46;srcElement;while(a){if(a&#46;href)break;a=a&#46;parentNode}}var b=encodeURIComponent||escape,c;c=a&#46;href;var n=&#91;&quot;/url?sa=t&quot;,&quot;\x26source\x3dweb&quot;,e?&quot;&amp;oi=&quot;+b(e)&#58;&quot;&quot;,f?&quot;&amp;cad=&quot;+b(f)&#58;&quot;&quot;,&quot;&amp;ct=&quot;,b(j||&quot;res&quot;),&quot;&amp;cd=&quot;,b(k),&quot;&amp;ved=&quot;,b(m),&quot;&amp;url=&quot;,b(c)&#46;replace(/\+/g,&quot;%2B&quot;),&quot;&amp;ei=&quot;,&quot;PoIPS6elGZH-tQPviYTmAQ&quot;,g?&quot;&amp;usg=&quot;+g&#58;&quot;&quot;,l&#93;&#46;join(&quot;&quot;);a&#46;href=n;a&#46;onmousedown=&quot;&quot;}catch(o){}return true};
window&#46;gbar={qs&#58;function(){},tg&#58;function(e){var o={id&#58;'gbar'};for(i in e)o&#91;i&#93;=e&#91;i&#93;;google&#46;x(o,function(){gbar&#46;tg(o)})}};
&lt;/script&gt;
[/code:34609mxw]

Not exactly the most maintainable looking code to read, but its a start.

--------------------------------------------------------------------------------

Posted by **dxh** on Sun November 29th, 2009 01:10:38 AM

[quote=&quot;dxh&quot;:2u9l7w2r]
[code:2u9l7w2r]
&lt;script&gt;google&#46;y={};google&#46;x=function(e,g){google&#46;y&#91;e&#46;id&#93;=&#91;e,g&#93;;return false};window&#46;rwt=function(a,e,f,j,k,g,l,m){try{if(a===window){a=window&#46;event&#46;srcElement;while(a){if(a&#46;href)break;a=a&#46;parentNode}}var b=encodeURIComponent||escape,c;c=a&#46;href;var n=&#91;&quot;/url?sa=t&quot;,&quot;\x26source\x3dweb&quot;,e?&quot;&amp;oi=&quot;+b(e)&#58;&quot;&quot;,f?&quot;&amp;cad=&quot;+b(f)&#58;&quot;&quot;,&quot;&amp;ct=&quot;,b(j||&quot;res&quot;),&quot;&amp;cd=&quot;,b(k),&quot;&amp;ved=&quot;,b(m),&quot;&amp;url=&quot;,b(c)&#46;replace(/\+/g,&quot;%2B&quot;),&quot;&amp;ei=&quot;,&quot;PoIPS6elGZH-tQPviYTmAQ&quot;,g?&quot;&amp;usg=&quot;+g&#58;&quot;&quot;,l&#93;&#46;join(&quot;&quot;);a&#46;href=n;a&#46;onmousedown=&quot;&quot;}catch(o){}return true};
window&#46;gbar={qs&#58;function(){},tg&#58;function(e){var o={id&#58;'gbar'};for(i in e)o&#91;i&#93;=e&#91;i&#93;;google&#46;x(o,function(){gbar&#46;tg(o)})}};
&lt;/script&gt;
[/code:2u9l7w2r]

Not exactly the most maintainable looking code to read, but its a start.[/quote:2u9l7w2r]

FYI, if anyone can translate this ultra-optimized code into something readable and tell me what rwt()'s parameters are supposed to be, I will buy you coffee at the next meeting.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun November 29th, 2009 01:49:24 PM

Just saw this post.  I too have noticed the JS link swapping Google does on their search results pages and considered this pretty big vulnerability as a phishing tactic.  As for getting the URL the way you're talking about I'll have to think about.  Maybe we can go over it at the next meeting and (hopefully) come up with a solution.  At the moment however, I do not have the time.  I'll see if I can make some though, and let you know if I figure anything out.

--------------------------------------------------------------------------------

Posted by **dxh** on Tue December 1st, 2009 09:40:51 PM

TrackMeNot was able to get clickthrough obfuscation working at one point, but Google changed the code and its broken, according to one of their developers.  They seem to have similar aims with HayProj, although their algorithms and technical goals seem slightly different.

--------------------------------------------------------------------------------

Posted by **dxh** on Fri December 11th, 2009 10:07:58 PM

[quote=&quot;dxh&quot;:2z7lo0rc]TrackMeNot was able to get clickthrough obfuscation working at one point, but Google changed the code and its broken, according to one of their developers.  They seem to have similar aims with HayProj, although their algorithms and technical goals seem slightly different.[/quote:2z7lo0rc]

Speaking of which, their code is CC licensed, so I can post it here.  Credits: <http&#58;//mrl&#46;nyu&#46;edu/~dhowe/trackmenot/>.  It used to work, they're working on updating it soon:

[code:2z7lo0rc]  /***************************************************************************
  Get the redirect link, so it appears we click on a link
  ***************************************************************************/
  function simulateClick (urls, engine) 
  {
    if (!tmn&#46;enabled || urls&#46;length &lt; 1) return false;
    
    // -----------------------------------------------
    if (false) { var urlStr = &quot;&quot;;  // tmp&#58; debugging
      for (var i = 0;i &lt; urls&#46;length; i++) 
        urlStr += i+&quot;) &quot;+urls&#91;i&#93;+&quot;\n\n&quot;;
      cout(&quot;SIMULATE_CLICK&#46;URLS&#58;\n&quot;+urlStr);
    }
    // -----------------------------------------------
    
    var queryIndex = tmn&#46;_roll(0,urls&#46;length-1);
    if (urls&#91;queryIndex&#93; == undefined) {
      tmn&#46;_cerr(&quot;Undefined url at idx=&quot;+queryIndex+&quot; list-length=&quot;+urls&#46;length);
      return;
    }

    // Split into click-url and link-text 
    var both = urls&#91;queryIndex&#93;;
    var arr = both&#46;split(tmn&#46;delim);   
    var clickUrl = arr&#91;0&#93;, query = arr&#91;1&#93;;
    if (query == &quot;&quot;) query = &quot;???&quot;;

    var nextReq = tmn&#46;cc&#91;&quot;@mozilla&#46;org/xmlextras/xmlhttprequest;1&quot;&#93;
        &#46;createInstance(tmn&#46;ci&#46;nsIXMLHttpRequest);
        
    try {
      nextReq&#46;open(&quot;GET&quot;, clickUrl, true);
    } catch (e) {
      tmn&#46;_cerr(&quot;error opening click-through request for '&quot;+clickUrl+&quot;'&quot;);
      return;
    }
    
    tmn&#46;_log(&quot;&#91;QUERY&#93; engine=&quot;+engine+&quot; | mode=click &quot;
      +&quot;| query='&quot;+query+&quot;' | url=&quot;+clickUrl);
  
    if (nextReq&#46;channel instanceof tmn&#46;ci&#46;nsISupportsPriority) { 
      nextReq&#46;channel&#46;priority = tmn&#46;ci
          &#46;nsISupportsPriority&#46;PRIORITY_LOWEST;
    }
          
    if (tmn&#46;enabled) nextReq&#46;send(&quot;&quot;); // double-check

    // CAN WE PERHAPS CALL tmn&#46;_scheduleSearch() HERE? -dch
    var requestTimer = tmn&#46;_getQueryWindow()&#46;setTimeout(function() {nextReq&#46;abort();}, 5000);
    nextReq&#46;onreadystatechange=function(aEvt) {
      if (nextReq&#46;readyState==4) {
        clearTimeout(requestTimer);
        return true;
      }
    }
  }
[/code:2z7lo0rc]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon December 14th, 2009 09:00:43 AM

Just ordered a new laptop last night, so I'm finally going to be able to get back into coding on my free time and want to help... however, I kind of need some up-to-date code to work of of (nudge, nudge, wink, wink). <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->

--------------------------------------------------------------------------------

Posted by **dxh** on Mon December 14th, 2009 08:32:20 PM

[quote=&quot;PHLAK&quot;:2fr1siso]Just ordered a new laptop last night, so I'm finally going to be able to get back into coding on my free time and want to help... however, I kind of need some up-to-date code to work of of (nudge, nudge, wink, wink). <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->[/quote:2fr1siso]

Its in the works; I think I have clickthroughs figured out, but it will invole getting the site integrated to use a greasemonkey script and also regex, which I'm not that great at yet, so it'll come slowly, but very soon.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue December 15th, 2009 05:43:08 PM

The point of putting it up on Github is so others (aka, myself) can help.

--------------------------------------------------------------------------------

Posted by **dxh** on Sat January 2nd, 2010 12:55:06 AM

[quote=&quot;PHLAK&quot;:a9ogn1j6]The point of putting it up on Github is so others (aka, myself) can help.[/quote:a9ogn1j6]

Alright, I got over my don't-check-broken-code-in mentality and posted what I have so far in the alpha directory: <http&#58;//hmm&#46;ph/9pu>

Basically, I can't get the button on the page to call a function in the GS script, despite defining the webSearch function as part of the window object where it should be accesible anywhere.  The examples of this sort of thing I've seen in other scripts involve building the html button element and adding it on the page, which I might end up doing.

The clickthrough obfuscation part does work though.  <!-- s8-) --><img src="{SMILIES_PATH}/icon_cool.gif" alt="8-)" title="Cool" /><!-- s8-) --> 

Also, 150+ views for less than one page, holy kaw!
