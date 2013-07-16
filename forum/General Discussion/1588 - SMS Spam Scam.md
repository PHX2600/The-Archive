## SMS Spam Scam
Posted by **dual** on Wed April 4th, 2012 07:32:48 AM

Got this text yesterday.

[code:204d5qu4]http&#58;//www&#46;smscaster&#46;com
You have been selected to
receive a FREE apple
product&#46; Go to
www&#46;LimitedFreeStuff&#46;com
to fill in your shipping
address and claim your[/code:204d5qu4]

LimitedFreeStuff.com forwards to vipbidders.com and is a standard address harvester. Clicking unsubscribe goes to edebitinc.com.

Running mild on edebitinc.com gets...

[code:204d5qu4]mail&#46;edebitinc&#46;com&#46;     14400   IN      CNAME   edebitinc&#46;com&#46;
edebitinc&#46;com&#46;          14400   IN      A       67&#46;227&#46;163&#46;113
dev&#46;edebitinc&#46;com&#46;      14400   IN      A       67&#46;227&#46;163&#46;113
localhost&#46;edebitinc&#46;com&#46; 14400  IN      A       127&#46;0&#46;0&#46;1
www&#46;edebitinc&#46;com&#46;      14400   IN      CNAME   edebitinc&#46;com&#46;
edebitinc&#46;com&#46;          14400   IN      A       67&#46;227&#46;163&#46;113
ftp&#46;edebitinc&#46;com&#46;      14400   IN      A       67&#46;227&#46;163&#46;113
webmail&#46;edebitinc&#46;com&#46;  14400   IN      A       67&#46;227&#46;163&#46;113
stats&#46;edebitinc&#46;com&#46;    14400   IN      A       67&#46;227&#46;163&#46;113[/code:204d5qu4]

A login for stats.edebitinc.com is stats: stats. There you can see the referrers feeding the scam site...

[code:204d5qu4]http&#58;//www&#46;mobilepornxxx&#46;mobi/index-320&#46;php?res=320
http&#58;//getdrugs2u&#46;com/join/signup&#46;php?step=2
[/code:204d5qu4]

which correlate to Site IDs.

[code:204d5qu4]drg2u
etxtc
mpxxx
uketc[/code:204d5qu4]

etxtc is easytextchat.com. Going into the referrers you can see the similarities in the affiliate network.

[code:204d5qu4]http&#58;//affiliates&#46;profitkingsmedia&#46;com/Welcome/LogInAndSignUp&#46;aspx?FP=C&amp;FR=1&amp;S=1
http&#58;//affiliates&#46;eaglewebassets&#46;com/Welcome/LogInAndSignUp&#46;aspx?FP=C&amp;FR=1&amp;S=4[/code:204d5qu4]

Hopefully a small, interesting look into profiting from clicky users.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed April 4th, 2012 10:45:25 AM

Nice research dual

--------------------------------------------------------------------------------

Posted by **dual** on Thu April 5th, 2012 08:10:41 PM

Thanks. And limitedfreestuff.com is already gone.
