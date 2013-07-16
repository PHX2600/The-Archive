## Hacker vs Admin
Posted by **lialdd** on Tue November 16th, 2010 09:48:08 AM

If there were hypothetically a hacker in a medium-to-large-sized network, how would you tell? What tools would you use beside hunting down firewall sessions and event logs? How would you practically distinguish good traffic from bad? Assume Windows.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue November 16th, 2010 10:55:12 AM

Speaking from experience you would know when your front page turned into a collage of dick lamps asians, sea mammals, and disabled children.

Then you would just expel or suspend anyone using the network at that time.

On a for serious note check out this site for some great reads on detecting/preventing intrusions on live systems:

<!-- m --><a class="postlink" href="http://www.honeynet.org/">http://www.honeynet.org/</a><!-- m -->

Honeynets are a great way to do what you're talking about. Especially on a windows network.

--------------------------------------------------------------------------------

Posted by **nak** on Tue November 16th, 2010 10:57:17 AM

<!-- s:? --><img src="{SMILIES_PATH}/icon_e_confused.gif" alt=":?" title="Confused" /><!-- s:? -->

--------------------------------------------------------------------------------

Posted by **lialdd** on Tue November 16th, 2010 01:44:39 PM

[quote=&quot;nak&quot;:2owhnh4x]:?[/quote:2owhnh4x]

is that the &quot;not sure if want 80's bill gates&quot; emoticon?

thanks for the tip, i was thinking about a honeypot but from a practical perspective it wouldn't help aside from the initial stages of an intrusion... once an attack got privileges they would stay mostly within the real network and appear quite legitimate.

any tools to visualize what's &quot;happening&quot; on a network? obviously big holographic datacenters don't exist yet, but being able to say &quot;look! someone is doing _____ right now!&quot; would be quite useful.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue November 16th, 2010 02:00:08 PM

Yeah tons of network visualizers out there

<!-- m --><a class="postlink" href="http://www.google.com/search?q=network+visualization&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a">http://www.google.com/search?q=network+ ... =firefox-a</a><!-- m -->

But unless you're gonna sit there and watch it all day a standard log system with email alerts might be more reasonable.

tripwire, snort, many intrusion detections systems out there for that kind of thing.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu November 18th, 2010 02:31:04 PM

I'd have to agree with Penguin.  While somewhat old and archaic, there's no substitute for a good set of logs.

--------------------------------------------------------------------------------

Posted by **nak** on Fri December 24th, 2010 07:22:11 AM

[quote=&quot;lialdd&quot;:2kdrfwpe][quote=&quot;nak&quot;:2kdrfwpe]:?[/quote:2kdrfwpe]
is that the &quot;not sure if want 80's bill gates&quot; emoticon?
[/quote:2kdrfwpe]

Penguin was just telling a story that was hitting close to home and that's the emotion I was feeling at the time  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) --> 
If you're up for the task of trying to compile EtherApe (not EtheRape) on your windows box, feel free: <!-- m --><a class="postlink" href="http://etherape.sourceforge.net/">http://etherape.sourceforge.net/</a><!-- m -->

It's the only network visualizer I've used.  In flaggy I can bring in an open wifi hotspot, so I like to watch what's going on if I'm doing private thangs like I like to do (and those channels would be encrypted anyway, GPG keys anyone????), etherape and nmap scans while watching my arp table is all I really do... never ran into a problem with devious bastards there... even I behave!  Ettercap (which has a windows binary I believe) can also be used if you wanna fiddle with the other's ARP tables and check out what the jerkroids are really up to in detail on a switched netty... not really an &quot;admin&quot; tool though.
Wireshark isn't really a visualizer, but it's the primo packet sniffer imho.

Did you find a winner? Just curious...
A 3D visualizer would be sick-a-lick, flying around hacking the gibson... mmm baby
