## doppleganger's
Posted by **XlogicX** on Sat October 22nd, 2011 02:56:52 AM

For those that don't know what a doppleganger attack is, it's pretty much typo-squating for domains. Like registering gmqil.com. The typo has a 'q' instead of an 'a,' the 'q' is close in proximity on a keyboard to an 'a', so some people could potentially make the mistake. If you register gmqil.com, you could intercept some cool stuff from those that make the typo without realising it.

I guess a massive amount of fortune 500 companies got pwn'd this way a couple months ago, this was from a legitimate pen test though. But the pen tester intercepted some very confidential emails with this attack.

So about a month ago, I found a cool tool released on Packet Storm called urlcrazy, it's ruby based. I played with it a little. What it does is it generates a bunch of typo's using all kinds of techniques like character omission, repeat, swap, replacement, insertion, a missing dot, pluralizing, bit flipping, and just different TLD's (.com, .org, etc...) than the original. It then checks the generated list against actual registered ones out there. It even has a popularity index (not sure about accuracy though).

Anyway, here's how our site turns up:

[code:246epmf4]

xlogicx@XlogicX-UD:~/Desktop/urlcrazy-0.4$ ./urlcrazy www.phx2600.org
URLCrazy Domainname Typo Report
For       : www.phx2600.org
Keyboard  : qwerty
At        : Sat Oct 22 01:44:55 -0700 2011

# Please wait. 122 hostnames to process
Typo Type              Typo                Pop     DNS-A           DNS-MX                 Extn  
------------------------------------------------------------------------------------------------
Character Omission     ww.phx2600.org      44200   72.215.225.9                           org   
Character Omission     www.hx2600.org      13400   72.215.225.9                           org   
Character Omission     www.ph2600.org      14600   72.215.225.9                           org   
Character Omission     www.phx200.org      924     72.215.225.9                           org   
Character Omission     www.phx260.org      85      72.215.225.9                           org   
Character Omission     www.phx600.org      1090    72.215.225.9                           org   
Character Omission     www.px2600.org      1260    72.215.225.9                           org   
Character Omission     wwwphx2600.org              72.215.225.9                           org   
Character Repeat       www.phhx2600.org            72.215.225.9                           org   
Character Repeat       www.phx22600.org            72.215.225.9                           org   
Character Repeat       www.phx26000.org            72.215.225.9                           org   
Character Repeat       www.phx26600.org            72.215.225.9                           org   
Character Repeat       www.phxx2600.org    12600   72.215.225.9                           org   
Character Repeat       www.pphx2600.org            72.215.225.9                           org   
Character Repeat       wwww.phx2600.org            72.215.225.9                           org   
Character Swap         ww.wphx2600.org             72.215.225.9                           org   
Character Swap         www.hpx2600.org     20      72.215.225.9                           org   
Character Swap         www.ph2x600.org             72.215.225.9                           org   
Character Swap         www.phx2060.org             72.215.225.9                           org   
Character Swap         www.phx6200.org     68      72.215.225.9                           org   
Character Swap         www.pxh2600.org             72.215.225.9                           org   
Character Swap         wwwp.hx2600.org             72.215.225.9                           org   
Character Replacement  eww.phx2600.org     190     72.215.225.9                           org   
Character Replacement  qww.phx2600.org     42700   72.215.225.9                           org   
Character Replacement  wew.phx2600.org     10900   72.215.225.9                           org   
Character Replacement  wqw.phx2600.org     42800   72.215.225.9                           org   
Character Replacement  wwe.phx2600.org     201     72.215.225.9                           org   
Character Replacement  wwq.phx2600.org     42700   72.215.225.9                           org   
Character Replacement  www.ohx2600.org             72.215.225.9                           org   
Character Replacement  www.pgx2600.org             72.215.225.9                           org   
Character Replacement  www.phc2600.org     86      72.215.225.9                           org   
Character Replacement  www.phx1600.org     107     72.215.225.9                           org   
Character Replacement  www.phx2500.org     71      72.215.225.9                           org   
Character Replacement  www.phx26-0.org     297     72.215.225.9                           org   
Character Replacement  www.phx260-.org     22      72.215.225.9                           org   
Character Replacement  www.phx2609.org             72.215.225.9                           org   
Character Replacement  www.phx2690.org             72.215.225.9                           org   
Character Replacement  www.phx2700.org             72.215.225.9                           org   
Character Replacement  www.phx3600.org     23      72.215.225.9                           org   
Character Replacement  www.phz2600.org             72.215.225.9                           org   
Character Replacement  www.pjx2600.org             72.215.225.9                           org   
Character Insertion    weww.phx2600.org    42700   72.215.225.9                           org   
Character Insertion    wqww.phx2600.org    44200   72.215.225.9                           org   
Character Insertion    wwew.phx2600.org    44300   72.215.225.9                           org   
Character Insertion    wwqw.phx2600.org    44200   72.215.225.9                           org   
Character Insertion    www.phgx2600.org    661     72.215.225.9                           org   
Character Insertion    www.phjx2600.org            72.215.225.9                           org   
Character Insertion    www.phx21600.org            72.215.225.9                           org   
Character Insertion    www.phx23600.org            72.215.225.9                           org   
Character Insertion    www.phx260-0.org            72.215.225.9                           org   
Character Insertion    www.phx2600-.org    169000  72.215.225.9                           org   
Character Insertion    www.phx26009.org            72.215.225.9                           org   
Character Insertion    www.phx26090.org            72.215.225.9                           org   
Character Insertion    www.phx26500.org            72.215.225.9                           org   
Character Insertion    www.phx26700.org            72.215.225.9                           org   
Character Insertion    www.phxc2600.org            72.215.225.9                           org   
Character Insertion    www.phxz2600.org            72.215.225.9                           org   
Character Insertion    www.pohx2600.org            72.215.225.9                           org   
Character Insertion    wwwe.phx2600.org    42800   72.215.225.9                           org   
Character Insertion    wwwq.phx2600.org    42700   72.215.225.9                           org   
Missing Dot            wwwwww.phx2600.org  42700   72.215.225.9                           org   
Singular or Pluralise  phx2600.org         44400   96.126.115.54   ASPMX.L.GOOGLE.COM     org   
Singular or Pluralise  phx2600s.org        15400   72.215.225.9                           org   
Bit Flipping           7ww.phx2600.org                                                    org   
Bit Flipping           gww.phx2600.org     634     72.215.225.9                           org   
Bit Flipping           sww.phx2600.org     4930    72.215.225.9                           org   
Bit Flipping           uww.phx2600.org             72.215.225.9                           org   
Bit Flipping           vww.phx2600.org     42700   72.215.225.9                           org   
Bit Flipping           w7w.phx2600.org             72.215.225.9                           org   
Bit Flipping           wgw.phx2600.org             72.215.225.9                           org   
Bit Flipping           wsw.phx2600.org             72.215.225.9                           org   
Bit Flipping           wuw.phx2600.org     1900    72.215.225.9                           org   
Bit Flipping           wvw.phx2600.org     428     72.215.225.9                           org   
Bit Flipping           ww7.phx2600.org     29      72.215.225.9                           org   
Bit Flipping           wwg.phx2600.org     789     72.215.225.9                           org   
Bit Flipping           wws.phx2600.org             72.215.225.9                           org   
Bit Flipping           wwu.phx2600.org             72.215.225.9                           org   
Bit Flipping           wwv.phx2600.org     1470    72.215.225.9                           org   
Bit Flipping           www.0hx2600.org             72.215.225.9                           org   
Bit Flipping           www.ph82600.org     22      72.215.225.9                           org   
Bit Flipping           www.phh2600.org             72.215.225.9                           org   
Bit Flipping           www.php2600.org     24900   72.215.225.9                           org   
Bit Flipping           www.phx0600.org     27      72.215.225.9                           org   
Bit Flipping           www.phx2200.org     33      72.215.225.9                           org   
Bit Flipping           www.phx2400.org     69      72.215.225.9                           org   
Bit Flipping           www.phx2601.org             72.215.225.9                           org   
Bit Flipping           www.phx2602.org             72.215.225.9                           org   
Bit Flipping           www.phx2604.org             72.215.225.9                           org   
Bit Flipping           www.phx2608.org             72.215.225.9                           org   
Bit Flipping           www.phx260p.org     59      72.215.225.9                           org   
Bit Flipping           www.phx2610.org             72.215.225.9                           org   
Bit Flipping           www.phx2620.org             72.215.225.9                           org   
Bit Flipping           www.phx2640.org             72.215.225.9                           org   
Bit Flipping           www.phx2680.org             72.215.225.9                           org   
Bit Flipping           www.phx26p0.org             72.215.225.9                           org   
Bit Flipping           www.phx2v00.org             72.215.225.9                           org   
Bit Flipping           www.phx6600.org             72.215.225.9                           org   
Bit Flipping           www.phxr600.org             72.215.225.9                           org   
Bit Flipping           www.phy2600.org     33      72.215.225.9                           org   
Bit Flipping           www.pix2600.org     288     72.215.225.9                           org   
Bit Flipping           www.plx2600.org     45      72.215.225.9                           org   
Bit Flipping           www.pxx2600.org     30600   72.215.225.9                           org   
Bit Flipping           www.qhx2600.org             72.215.225.9                           org   
Bit Flipping           www.rhx2600.org             72.215.225.9                           org   
Bit Flipping           www.thx2600.org     156     72.215.225.9                           org   
Bit Flipping           www.xhx2600.org             72.215.225.9                           org   
Bit Flipping           wwwnphx2600.org             72.215.225.9                           org   
Wrong TLD              phx2600.ca          45400   72.215.225.9                           ca    
Wrong TLD              phx2600.ch          43900   72.215.225.9                           ch    
Wrong TLD              phx2600.com         132     64.202.189.170  smtp.secureserver.net  com   
Wrong TLD              phx2600.de          44000   72.215.225.9                           de    
Wrong TLD              phx2600.edu         48000   72.215.225.9                           edu   
Wrong TLD              phx2600.es          45300   72.215.225.9                           es    
Wrong TLD              phx2600.fr          44000   72.215.225.9                           fr    
Wrong TLD              phx2600.it          48100   72.215.225.9                           it    
Wrong TLD              phx2600.jp          43900   72.215.225.9                           jp    
Wrong TLD              phx2600.net         77      72.215.225.9                           net   
Wrong TLD              phx2600.nl          45400   72.215.225.9                           nl    
Wrong TLD              phx2600.no                  72.215.225.9                           no    
Wrong TLD              phx2600.ru          43900   72.215.225.9                           ru    
Wrong TLD              phx2600.se                  72.215.225.9                           se    
Wrong TLD              phx2600.us                  72.215.225.9                           us    

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

72.215.225.9 is just Cox's "page not found" proxy.  Whenever you hit a site that doesn't exist, Cox may intercept this and show you a page with sponsored links like this:

[url=http://dl.dropbox.com/u/785103/Screenshots/permalinks/225838.png:1zrte3pv][img:1zrte3pv]http://dl.dropbox.com/u/785103/Screenshots/permalinks/225838_640.png[/img:1zrte3pv]>

So it appears that every domain in that list other than phx2600.org and phx2600.com are not in use.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed November 2nd, 2011 12:57:11 AM

Yeah, guess I should have pasted the robtex info too:
ip72-215-225-9.at.at.cox.net

in the  72.192.0.0/11 RI AGGREGATE TRANSIT

I should type another typo to have cox catch it and see if the tool catches it
