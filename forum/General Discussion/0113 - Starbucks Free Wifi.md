## Starbucks Free Wifi
Posted by **dual** on Sat June 7th, 2008 04:30:06 PM

tankilo was interested in the new free wifi at Starbucks and I was in a crappy mood, so I'll post observations here.

With a registered Starbucks card, $5 minimum, used once per month, patrons get two consecutive hours of wireless access per day:

<!-- m --><a class="postlink" href="http://www.starbucks.com/retail/wireless.asp">http://www.starbucks.com/retail/wireless.asp</a><!-- m -->

The service launched 3 June and I tested it Friday morning. Sign up and sign in were quite slow due to server load. The SSID is attwifi and DHCP hands out 10. addresses. The tmobile SSID was still present, though I think they're going away. After sign in, access was fast and reliable, and it seems that no ports are blocked.

AFAIK, the cards are standard 16-digit, 8-digit scratch-off PIN Starbucks cards. The card has a two-track mag stripe. One track has a string of numbers, which we'll call string1, the print run name, here RNASPRINGCARDFY08, and then another string of numbers, string2. The other track has "string1=string2." The last four digits of string2 are the last four of the card number.

Without a Starbucks card, only UDP on 53 is allowed, so at least you can use dig. I recommend signing up at home with fake docs. Other than that, make sure to get your coffee in a mug and ask for the cup discount!

--------------------------------------------------------------------------------

Posted by **dual** on Sun June 8th, 2008 03:51:52 PM

From Slashdot, [url=http://wifinetnews.com/archives/008345.html:2rf1qho7]T-Mobile Sues Starbucks over Premature Free Wi-Fi>.

--------------------------------------------------------------------------------

Posted by **dual** on Tue June 10th, 2008 07:45:45 AM

Screen shots for completeness.

[attachment=1:2bftgm3a]<!-- ia1 -->attwifi1.png<!-- ia1 -->[/attachment:2bftgm3a]
[attachment=0:2bftgm3a]<!-- ia0 -->attwifi2.png<!-- ia0 -->[/attachment:2bftgm3a]

--------------------------------------------------------------------------------

Posted by **nak** on Tue June 10th, 2008 03:52:43 PM

Coolio, although I have the luxury of not living next door to a star$s

--------------------------------------------------------------------------------

Posted by ***Hazard** on Sat June 14th, 2008 01:25:05 PM

[quote="nak":1kk2zb49]Coolio, although I have the luxury of not living next door to a star$s[/quote:1kk2zb49]

I do however live near a ?-$'s but I already pay for my HSI service from Cawks. :p

--------------------------------------------------------------------------------

Posted by **dual** on Sun June 29th, 2008 01:26:22 AM

It seems it's back to T-Mobile and no longer free.

--------------------------------------------------------------------------------

Posted by **dual** on Tue October 14th, 2008 08:15:05 AM

Free AT&amp;T wifi is working with the same deal. Also, an employee just told me that the 2 hour limit is arbitrary and that regular customers chill on the wireless for up to 8 hours.

You can still do a lot of stuff if you don't want to pay. You can go to att and starbucks.com, whitepages.com, yellowpages.com (testuser: testuser) and <!-- m --><a class="postlink" href="http://www.know-where.com/clients/">http://www.know-where.com/clients/</a><!-- m --> and subsequently CLIENT.know-where.com/CLIENT. Along with UDP digs and ping.
