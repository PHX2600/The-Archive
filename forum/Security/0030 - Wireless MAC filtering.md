## Wireless MAC filtering
Posted by ***Hazard** on Thu January 17th, 2008 06:56:44 PM

Hey guys what do you think about wireless MAC filtering and intrusion detection logging for security? How would I go about pen testing in regards to a router using wireless MAC filter?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu January 17th, 2008 08:29:52 PM

MAC filtering is a joke to anyone who knows anything about wireless hacking.

The process I use to getting past this type of security is as follows:

1) [Optional] Use [http://www.netstumbler.com](NetStumbler) to determine the channel of the access point you wish to test.
2) Use [http://www.aircrack-ng.org/doku.php](Aircrack-NG) to identify a MAC address connected to the access point you wish to connect to.
3) Use [http://www.klcconsulting.net/smac](SMAC) to spoof your computers MAC address.
4) Connect
5) ???
6) PROFIT!

Best screen shot I currently have: <http://farm3.static.flickr.com/2417/2167807850_fa0bd684cd_o.jpg>

--------------------------------------------------------------------------------

Posted by ***Hazard** on Sun January 20th, 2008 09:21:50 PM

Fucking Hell.

Thanks Phlak. I forgot about SMAC, hell I used it to spoof my MAC during the Habbo raid. 

Can you recommend any articles or hardware re: wireless security to me? I'll look on my own in the meantime but I trust your judgment.  <!-- s:mrgreen: --><img src="{SMILIES_PATH}/icon_mrgreen.gif" alt=":mrgreen:" title="Mr. Green" /><!-- s:mrgreen: -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon January 21st, 2008 01:01:11 AM

I just did a quick Google search for "WEP cracking on Windows", and glanced over this: <http://www.tazforum.thetazzone.com/viewtopic.php?t=2069.>  It looks like it contains everything you need to know.

WEP cracking and MAC spoofing is fun stuff, and surprisingly easy to accomplish.

In terms of hardware, I'm using the Netgear WG511T PCMCIA wireless card because it uses the Atheros chipset which is required (that or an Orinoco chipset) to hax the WEPz.

--------------------------------------------------------------------------------

Posted by **ArchAngel** on Mon January 21st, 2008 01:08:45 PM

[quote:1t1fwdk0]3) Use SMAC to spoof your computers MAC address.[/quote:1t1fwdk0]

Also remember in windoze you can do this via the registry - start -> run -> "regedit" (without quotes) will get you to the main interface. Then look for one of the GUIDs under "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\" with a key named "NetworkAddress" that matches your MAC. (Or create the key if it doesn't exist, yet)

-ArchAngel

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon January 21st, 2008 04:26:53 PM

I knew there was a way to do it manually, but never looked for it.

--------------------------------------------------------------------------------

Posted by **oz1980** on Sat February 2nd, 2008 10:14:48 AM

Linux commands to finding and spoofing a mac address on a network:

This assumes that you are using Linux, your wireless interface is wlan, and that the AP mac is de:ad:00:00:be:ef and the client mac is de:ad:00:be:ef:02. Changes to the macs and interface should be made accordingly.

# iwlist wlan scan (finds an access point and gives a mac for it)
# ifconfig wlan down
# ifconfig wlan hw ether de:ad:00:00:be:ef
# ifconfig wlan up

Now use a sniffer to capture packets. I like Wireshark. The mac add of an allowed client can be found in the packets.

# ifconfig wlan down
# ifconfig wlan hw ether de:ad:00:be:ef:02
# ifconfig wlan up

Now, you can connect to the access point. Tried it with my router. I got no www use, but I was able to ping out. You could use Ping tunnel to get out to a server you have on the outside. I haven't tied using ssh or telnet. I was able to ping out, witch means that ICMP and DNS are allowed through.
