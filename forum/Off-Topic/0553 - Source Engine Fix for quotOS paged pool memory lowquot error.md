## Source Engine Fix for "OS paged pool memory low" error
Posted by **nak** on Sat September 27th, 2008 01:38:10 PM

I know no one asked for this fix, but I thought I would upload this .REG file that fixed it.
<http://www.wetwarehacks.com/PagedPoolFix.reg>

This is what's in the file:
[code:1b1bjscv]Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management]
"PagedPoolSize"=dword:18000000[/code:1b1bjscv]

If you want to fix manually, just navigate in regedit (start>run>regedit) to that value and change it from zero to 18000000 hex.  Enjoy your non-crashing TF2 (or portal or whatever)!

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed October 1st, 2008 11:54:24 AM

NICE!  I've never gotten this error, but if I do I'll know how to fix it.  Thanks!
