## Setting up your own proxy server
Posted by **Rax** on Thu February 5th, 2009 07:58:01 PM

I'd like to set up a proxy server (not necessarily anonymous) on my Ubuntu box. I'd like to be able to point a browser to my proxy, from any other location, and surf to sites that could be restricted on the network that I happen to be sitting on.

Ideally, it wouldn't involve any client software. An SSL tunnel would be a pretty good solution, I guess. Browse to the proxy, authenticate, and redirect traffic through the tunnel.

So, give me a couple of pointers in the right direction here, folks.

--------------------------------------------------------------------------------

Posted by **fightgar** on Thu February 5th, 2009 08:44:14 PM

Apache + <!-- m --><a class="postlink" href="http://sourceforge.net/projects/poxy/">http://sourceforge.net/projects/poxy/</a><!-- m --> for surfing the porn at work

--------------------------------------------------------------------------------

Posted by **dual** on Fri February 6th, 2009 06:16:30 AM

Ubuntu 8.04 LTS Server Edition
<!-- m --><a class="postlink" href="http://www.ubuntu.com/getubuntu/download">http://www.ubuntu.com/getubuntu/download</a><!-- m -->

customhardylamp.sh
<!-- m --><a class="postlink" href="http://dualisanoob.com/linux/dot/customhardylamp.sh.txt">http://dualisanoob.com/linux/dot/customhardylamp.sh.txt</a><!-- m -->

Net::SSLeay
<!-- m --><a class="postlink" href="http://packages.ubuntu.com/hardy/libnet-ssleay-perl">http://packages.ubuntu.com/hardy/libnet-ssleay-perl</a><!-- m -->

CGIProxy
<!-- m --><a class="postlink" href="http://www.jmarshall.com/tools/cgiproxy/">http://www.jmarshall.com/tools/cgiproxy/</a><!-- m -->

Profit!
