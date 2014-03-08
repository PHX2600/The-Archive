## Express Card Wifi?!
Posted by **AltF4Warrior** on Fri January 30th, 2009 11:06:39 AM

Hey,

So my shiny new laptop comes with some crappy Broadcom wifi chipset. It works
for "typical" browsing, of course, but not much else. I spent days trying to get
the thing to work in monitor mode to no avail. Luckily, it came came with an
expansion slot. :) Unluckily, it's an ExpressCard slot, :( and apparently there
are virtually no wifi cards made to the new specs.

Just wondering if any of you guys have any good ExpressCards that you like.
There does appear to be a Belkin (1) that has either a Ralink or an Atheros
depending on version, but I dunno. Remote-exploit has it as untested. (2)

Or perhaps there's some kind of adapter you pick up to make PCMCIA cards work
with an ExpressCard slot.

Thanks!
-Alt

(1) <http://catalog.belkin.com/IWCatProductPage.process?Product_Id=299617#>

(2) <http://wiki.remote-exploit.org/index.php/Talk:HCL:Wireless>

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun February 1st, 2009 01:48:54 PM

I got a Netgear WG511T card that uses an Atheros chipset. This thing has served
me well, even got it working with Aircrack on Windows.

--------------------------------------------------------------------------------

Posted by **AltF4Warrior** on Mon February 2nd, 2009 09:11:21 AM

Yea, but that's a CardBus card.

<http://en.wikipedia.org/wiki/ExpressCard>

ExpressCard is the new format for expansion cards that friggin' every laptop now
has. And the old style CardBus don't fit.

It's kind of a stupid situation right now. Every laptop comes with only
ExpressCard slots, but every card you buy won't fit!  :evil:

--------------------------------------------------------------------------------

Posted by **AltF4Warrior** on Fri February 6th, 2009 02:27:31 PM

Okay, I found an answer to my own question. :)

D-Link has an ExpressCard with an Atheros chipset:
<http://www.dlink.com/products/?pid=550>

It's their dwl-643. I picked it up yesterday and it worked "out of the box" in
Backtrack 3. The madwifi drivers work swimmingly. I haven't tried Ath5k yet,
though.

But anyway, Monitor mode and injection were both perfect. And it was only $60 at
Fry's, as opposed to the $85 D-Link lists.

I also found this:
<http://www.echotechwireless.com/SRC_UBIQUITI_NETWORKS_WLAN_PC_CARD_802_11a_b_g_300_p/src.htm>

It's got an external antenna hookup, but is twice as expensive...
