## Source Engine Fix for &quot;OS paged pool memory low&quot; error
Posted by **nak** on Sat September 27th, 2008 01:38:10 PM

I know no one asked for this fix, but I thought I would upload this .REG file that fixed it.
[url:1b1bjscv]http&#58;//www&#46;wetwarehacks&#46;com/PagedPoolFix&#46;reg[/url:1b1bjscv]

This is what's in the file:
[code:1b1bjscv]Windows Registry Editor Version 5&#46;00

&#91;HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management&#93;
&quot;PagedPoolSize&quot;=dword&#58;18000000[/code:1b1bjscv]

If you want to fix manually, just navigate in regedit (start&gt;run&gt;regedit) to that value and change it from zero to 18000000 hex.  Enjoy your non-crashing TF2 (or portal or whatever)!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed October 1st, 2008 11:54:24 AM

NICE!  I've never gotten this error, but if I do I'll know how to fix it.  Thanks!
