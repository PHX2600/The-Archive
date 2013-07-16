## ProtoType: Traffic analysis attack
Posted by **AltF4** on Fri November 4th, 2011 10:44:52 PM

Hey everyone,

Here is the code that I demo'd briefly at the meeting today:

<!-- m --><a class="postlink" href="https://github.com/altf4/ProtoType">https://github.com/altf4/ProtoType</a><!-- m -->

It's about 850 lines of C++, and it's a traffic analysis attack on identifying encrypted protocols. The idea goes like this...

Imagine intercepting a two way encrypted traffic stream, and you want to know what sorts of things are going on inside the stream. The only information we can measure from the stream are:

1) Packet size. Since the vast majority of encryption schemes (notable TLS) don't pad data. Encrypted packet sizes remain the same as unencrypted.
2) Packet Interarrival times. The timing between packets. 
3) Direction of packets. 

So we use this information to statistically determine what protocol is likely in use inside the encrypted stream. One can easily imagine how BitTorrent traffic would look very different than Web Surfing for instance. Specifically, it uses the k-Nearest Neighbors algorithm for classification. 
(<!-- m --><a class="postlink" href="https://secure.wikimedia.org/wikipedia/en/wiki/K-nearest_neighbor_algorithm">https://secure.wikimedia.org/wikipedia/ ... _algorithm</a><!-- m -->)

The software is in &quot;Alpha&quot; status right now. It just barely works in a proof of concept kind of fashion. There's a lot that needs to be done to be really usable and reliable still. If you want to help, go ahead and fork my code and get hacking! I'm glad to answer any questions and such. 

-Alt

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri November 4th, 2011 11:58:02 PM

Can't wait to see this thing mature

--------------------------------------------------------------------------------

Posted by **nak** on Sat November 5th, 2011 05:02:13 PM

Very cool, so you could sniff VPN traffic (which some methods use TLS... which I've just familiarized myself with) and make a &quot;computed guess&quot; at what's happening inside the stream?

That would be useful for &quot;big brothers&quot; to send warnings to people &quot;We've noticed bittorrent traffic, or excessive streaming data over the VPN&quot; and scare 'em

What have you been using to encrypt test traffic? I saw you running youtube to get chunked traffic, and I guess just some normal web browsing?

I don't know C++, barely have touched C... but sounds like a neat project. I've interfaced with libpcap and C back in the day (with help from retrotech!) but never since.  I did check your code out last night after I got home (not in depth)

I am interesting in seeing this mature along with logic <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

Maybe this would be of interest for you? To get more packets, different encryption schemes etc: [url:392cqdzi]http&#58;//pcapr&#46;net/home[/url:392cqdzi] -- I haven't used it myself, let me know if it's awesome and I might sign up <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sat November 5th, 2011 05:50:05 PM

Here's that k-means clustering I was talking about.

<!-- m --><a class="postlink" href="http://en.wikipedia.org/wiki/K-means_clustering">http://en.wikipedia.org/wiki/K-means_clustering</a><!-- m -->

Plenty of demo code online. Might be worth looking into.
