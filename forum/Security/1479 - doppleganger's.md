## doppleganger's
Posted by **XlogicX** on Sat October 22nd, 2011 02:56:52 AM

For those that don't know what a doppleganger attack is, it's pretty much typo-squating for domains. Like registering gmqil.com. The typo has a 'q' instead of an 'a,' the 'q' is close in proximity on a keyboard to an 'a', so some people could potentially make the mistake. If you register gmqil.com, you could intercept some cool stuff from those that make the typo without realising it.

I guess a massive amount of fortune 500 companies got pwn'd this way a couple months ago, this was from a legitimate pen test though. But the pen tester intercepted some very confidential emails with this attack.

So about a month ago, I found a cool tool released on Packet Storm called urlcrazy, it's ruby based. I played with it a little. What it does is it generates a bunch of typo's using all kinds of techniques like character omission, repeat, swap, replacement, insertion, a missing dot, pluralizing, bit flipping, and just different TLD's (.com, .org, etc...) than the original. It then checks the generated list against actual registered ones out there. It even has a popularity index (not sure about accuracy though).

Anyway, here's how our site turns up:

[code:246epmf4]

xlogicx@XlogicX-UD&#58;~/Desktop/urlcrazy-0&#46;4$ &#46;/urlcrazy www&#46;phx2600&#46;org
URLCrazy Domainname Typo Report
For       &#58; www&#46;phx2600&#46;org
Keyboard  &#58; qwerty
At        &#58; Sat Oct 22 01&#58;44&#58;55 -0700 2011

# Please wait&#46; 122 hostnames to process
Typo Type              Typo                Pop     DNS-A           DNS-MX                 Extn  
------------------------------------------------------------------------------------------------
Character Omission     ww&#46;phx2600&#46;org      44200   72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;hx2600&#46;org      13400   72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;ph2600&#46;org      14600   72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;phx200&#46;org      924     72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;phx260&#46;org      85      72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;phx600&#46;org      1090    72&#46;215&#46;225&#46;9                           org   
Character Omission     www&#46;px2600&#46;org      1260    72&#46;215&#46;225&#46;9                           org   
Character Omission     wwwphx2600&#46;org              72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;phhx2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;phx22600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;phx26000&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;phx26600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;phxx2600&#46;org    12600   72&#46;215&#46;225&#46;9                           org   
Character Repeat       www&#46;pphx2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Repeat       wwww&#46;phx2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Swap         ww&#46;wphx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Swap         www&#46;hpx2600&#46;org     20      72&#46;215&#46;225&#46;9                           org   
Character Swap         www&#46;ph2x600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Swap         www&#46;phx2060&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Swap         www&#46;phx6200&#46;org     68      72&#46;215&#46;225&#46;9                           org   
Character Swap         www&#46;pxh2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Swap         wwwp&#46;hx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  eww&#46;phx2600&#46;org     190     72&#46;215&#46;225&#46;9                           org   
Character Replacement  qww&#46;phx2600&#46;org     42700   72&#46;215&#46;225&#46;9                           org   
Character Replacement  wew&#46;phx2600&#46;org     10900   72&#46;215&#46;225&#46;9                           org   
Character Replacement  wqw&#46;phx2600&#46;org     42800   72&#46;215&#46;225&#46;9                           org   
Character Replacement  wwe&#46;phx2600&#46;org     201     72&#46;215&#46;225&#46;9                           org   
Character Replacement  wwq&#46;phx2600&#46;org     42700   72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;ohx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;pgx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phc2600&#46;org     86      72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx1600&#46;org     107     72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx2500&#46;org     71      72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx26-0&#46;org     297     72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx260-&#46;org     22      72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx2609&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx2690&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx2700&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phx3600&#46;org     23      72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;phz2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Replacement  www&#46;pjx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Character Insertion    weww&#46;phx2600&#46;org    42700   72&#46;215&#46;225&#46;9                           org   
Character Insertion    wqww&#46;phx2600&#46;org    44200   72&#46;215&#46;225&#46;9                           org   
Character Insertion    wwew&#46;phx2600&#46;org    44300   72&#46;215&#46;225&#46;9                           org   
Character Insertion    wwqw&#46;phx2600&#46;org    44200   72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phgx2600&#46;org    661     72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phjx2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx21600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx23600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx260-0&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx2600-&#46;org    169000  72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx26009&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx26090&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx26500&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phx26700&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phxc2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;phxz2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    www&#46;pohx2600&#46;org            72&#46;215&#46;225&#46;9                           org   
Character Insertion    wwwe&#46;phx2600&#46;org    42800   72&#46;215&#46;225&#46;9                           org   
Character Insertion    wwwq&#46;phx2600&#46;org    42700   72&#46;215&#46;225&#46;9                           org   
Missing Dot            wwwwww&#46;phx2600&#46;org  42700   72&#46;215&#46;225&#46;9                           org   
Singular or Pluralise  phx2600&#46;org         44400   96&#46;126&#46;115&#46;54   ASPMX&#46;L&#46;GOOGLE&#46;COM     org   
Singular or Pluralise  phx2600s&#46;org        15400   72&#46;215&#46;225&#46;9                           org   
Bit Flipping           7ww&#46;phx2600&#46;org                                                    org   
Bit Flipping           gww&#46;phx2600&#46;org     634     72&#46;215&#46;225&#46;9                           org   
Bit Flipping           sww&#46;phx2600&#46;org     4930    72&#46;215&#46;225&#46;9                           org   
Bit Flipping           uww&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           vww&#46;phx2600&#46;org     42700   72&#46;215&#46;225&#46;9                           org   
Bit Flipping           w7w&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wgw&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wsw&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wuw&#46;phx2600&#46;org     1900    72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wvw&#46;phx2600&#46;org     428     72&#46;215&#46;225&#46;9                           org   
Bit Flipping           ww7&#46;phx2600&#46;org     29      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wwg&#46;phx2600&#46;org     789     72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wws&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wwu&#46;phx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wwv&#46;phx2600&#46;org     1470    72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;0hx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;ph82600&#46;org     22      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phh2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;php2600&#46;org     24900   72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx0600&#46;org     27      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2200&#46;org     33      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2400&#46;org     69      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2601&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2602&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2604&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2608&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx260p&#46;org     59      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2610&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2620&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2640&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2680&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx26p0&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx2v00&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phx6600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phxr600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;phy2600&#46;org     33      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;pix2600&#46;org     288     72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;plx2600&#46;org     45      72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;pxx2600&#46;org     30600   72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;qhx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;rhx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;thx2600&#46;org     156     72&#46;215&#46;225&#46;9                           org   
Bit Flipping           www&#46;xhx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Bit Flipping           wwwnphx2600&#46;org             72&#46;215&#46;225&#46;9                           org   
Wrong TLD              phx2600&#46;ca          45400   72&#46;215&#46;225&#46;9                           ca    
Wrong TLD              phx2600&#46;ch          43900   72&#46;215&#46;225&#46;9                           ch    
Wrong TLD              phx2600&#46;com         132     64&#46;202&#46;189&#46;170  smtp&#46;secureserver&#46;net  com   
Wrong TLD              phx2600&#46;de          44000   72&#46;215&#46;225&#46;9                           de    
Wrong TLD              phx2600&#46;edu         48000   72&#46;215&#46;225&#46;9                           edu   
Wrong TLD              phx2600&#46;es          45300   72&#46;215&#46;225&#46;9                           es    
Wrong TLD              phx2600&#46;fr          44000   72&#46;215&#46;225&#46;9                           fr    
Wrong TLD              phx2600&#46;it          48100   72&#46;215&#46;225&#46;9                           it    
Wrong TLD              phx2600&#46;jp          43900   72&#46;215&#46;225&#46;9                           jp    
Wrong TLD              phx2600&#46;net         77      72&#46;215&#46;225&#46;9                           net   
Wrong TLD              phx2600&#46;nl          45400   72&#46;215&#46;225&#46;9                           nl    
Wrong TLD              phx2600&#46;no                  72&#46;215&#46;225&#46;9                           no    
Wrong TLD              phx2600&#46;ru          43900   72&#46;215&#46;225&#46;9                           ru    
Wrong TLD              phx2600&#46;se                  72&#46;215&#46;225&#46;9                           se    
Wrong TLD              phx2600&#46;us                  72&#46;215&#46;225&#46;9                           us    

[/code:246epmf4]

So, we are not actually 72.215.225.9, of which all of these typos point to. My best guess is that it is a COX proxy:
<!-- m --><a class="postlink" href="http://www.robtex.com/ip/72.215.225.9.html">http://www.robtex.com/ip/72.215.225.9.html</a><!-- m -->
None of them seem to resolve anyway though.

Who knows what's going on though...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon October 24th, 2011 08:29:07 AM

Maybe our mighty site admin PHLAK can shed some light on this?

Anyway I heard about those attacks as well, quite clever and entertaining.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue November 1st, 2011 10:48:47 AM

72.215.225.9 is just Cox's &quot;page not found&quot; proxy.  Whenever you hit a site that doesn't exist, Cox may intercept this and show you a page with sponsored links like this:

[url=http&#58;//dl&#46;dropbox&#46;com/u/785103/Screenshots/permalinks/225838&#46;png:1zrte3pv][img:1zrte3pv]http&#58;//dl&#46;dropbox&#46;com/u/785103/Screenshots/permalinks/225838_640&#46;png[/img:1zrte3pv][/url:1zrte3pv]

So it appears that every domain in that list other than phx2600.org and phx2600.com are not in use.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed November 2nd, 2011 12:57:11 AM

Yeah, guess I should have pasted the robtex info too:
ip72-215-225-9.at.at.cox.net

in the  72.192.0.0/11 RI AGGREGATE TRANSIT

I should type another typo to have cox catch it and see if the tool catches it
