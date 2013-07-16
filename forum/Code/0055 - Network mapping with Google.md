## Network mapping with Google
Posted by **oz1980** on Wed February 6th, 2008 12:16:48 PM

I bet we have read or heard of the book &quot;Google Hacking for Penetration Tester&quot;. Well, it gave commands to do network mapping. I thought, what if there was a script that allowed you to put in a domain, and it will give you a list of subdomains that you can later look up later. So I wrote a shell script that would do the trick. it will save the list in a file with the domain you put in, and it will also print it to the screen. 

[code:1w37wx94]

#dnssearch&#46;sh
#    by Uriah C&#46;
#requires lynx, sed, awk, and linux
#  Feel free to make a Windows port if you wish
###############################################

echo &quot;domain&#58;&quot;
read domain

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=1&amp;q=site&#58;www&#46;$domain&quot; &gt; tmp

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;q=site&#58;$domain+-www&#46;*&quot; &gt;&gt; tmp

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=100&amp;q=site&#58;$domain+-www&#46;*&quot; &gt;&gt; tmp

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=200&amp;q=site&#58;$domain+-www&#46;*&quot; &gt;&gt; tmp

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=300&amp;q=site&#58;$domain+-www&#46;*&quot; &gt;&gt; tmp

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?&amp;q=site&#58;ftp&#58;//*&#46;$domain&quot; &gt;&gt; tmp

sed -n 's/\&#46; http&#58;\/\/&#91;&#91;&#58;alpha&#58;&#93;&#93;*&#46;'$domain'\//&amp; /p' tmp | awk '{print $2}' | sort -u &gt; $domain&#46;dns

sed -n 's/\&#46; ftp&#58;\/\/&#91;&#91;&#58;alpha&#58;&#93;&#93;*&#46;'$domain'\//&amp; /p' tmp | awk '{print $2}' | sort -u &gt;&gt; $domain&#46;dns
rm &#46;/tmp

cat &#46;/$domain&#46;dns

[/code:1w37wx94]

Thanks to the authors of the book for providing the basis for the script.

--------------------------------------------------------------------------------

Posted by **nak** on Wed February 6th, 2008 01:27:40 PM

I haven't heard of the book, seems like it would be a fun read.  Although, I have heard of j0hnny and his google hack site, pretty neat stuff there. <!-- m --><a class="postlink" href="http://johnny.ihackstuff.com/ghdb.php">http://johnny.ihackstuff.com/ghdb.php</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **dual** on Tue February 12th, 2008 10:12:48 PM

Great script.  Thanks!  It's definitely going in my toolkit.

--------------------------------------------------------------------------------

Posted by **dual** on Wed February 13th, 2008 12:44:58 AM

I tweaked it a bit for my tastes...

[code:nwvd17o3]
# dnssearch&#46;sh - by Uriah C&#46;
#
# Requires Linux, awk, lynx and sed
#
# Feel free to make a Windows port if you wish
##############################################

TEMP=&quot;tmp&#46;$$&quot;

if &#91; -z &quot;$1&quot; &#93;; then
        echo &quot;Usage&#58; dnssearch&#46;sh &lt;domain&gt;&quot;
        exit
fi

lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=1&amp;q=site&#58;www&#46;$1&quot; &gt; $TEMP
lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;q=site&#58;$1+-www&#46;*&quot; &gt;&gt; $TEMP
lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=100&amp;q=site&#58;$1+-www&#46;*&quot; &gt;&gt; $TEMP
lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=200&amp;q=site&#58;$1+-www&#46;*&quot; &gt;&gt; $TEMP
lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?num=100&amp;start=300&amp;q=site&#58;$1+-www&#46;*&quot; &gt;&gt; $TEMP
lynx -dump &quot;http&#58;//www&#46;google&#46;com/search?&amp;q=site&#58;ftp&#58;//*&#46;$1&quot; &gt;&gt; $TEMP

sed -n 's/\&#46; http&#58;\/\/&#91;&#91;&#58;alpha&#58;&#93;&#93;*&#46;'$1'\//&amp; /p' $TEMP | awk '{print $2}' | sort -u &gt; $1&#46;dns
sed -n 's/\&#46; ftp&#58;\/\/&#91;&#91;&#58;alpha&#58;&#93;&#93;*&#46;'$1'\//&amp; /p' $TEMP | awk '{print $2}' | sort -u &gt;&gt; $1&#46;dns

rm $TEMP

cat $1&#46;dns
[/code:nwvd17o3]
