## CHASM - Contextual Hybrid (Dis)Assembler 0x00
Posted by **jargon** on Tue August 25th, 2009 09:44:03 AM

[url:jshjzcsz]http&#58;//puzzlum&#46;retromachineshop&#46;com/chasm/[/url:jshjzcsz]
I made this over the past 6 days! It is a flat assembler/disassembler I wrote in PHP that can have new syntax and opcodes saved in plain/text &quot;.chasm&quot; files for it to use.

 <!-- s:mrgreen: --><img src="{SMILIES_PATH}/icon_mrgreen.gif" alt=":mrgreen:" title="Mr. Green" /><!-- s:mrgreen: -->

It is a flat assembler/disassembler, so no fancy tricks. <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P --> ..No macros or anything like that, and no predefined routines. Also, Currently it is probably only powerful enough for small sections of 6502 and Zilog Z80. I need to work on it more if I want it to work with such processors as PPC. However, it does theoretically support the PPC method of having different bit depth opcodes.

Nearly a year ago is when I originally wrote the 6502.chasm file. I just never got around to writing chasm until now. I need to add a method to parse syntax with multiple value fields. Right now CHASM doesn't support this.

Enjoy!

Jovis of EFnet's #n64dev ( [url:jshjzcsz]irc&#58;//irc&#46;efnet&#46;net/n64dev[/url:jshjzcsz] ) inspired me to actually sit down and write CHASM. He apparently wrote a N64 disassembler way back in 1997 or so. Here is a link to Jovis's Nintendo 64 disassembler: [url:jshjzcsz]http&#58;//www&#46;dextrose-forum&#46;com/index&#46;php?s=3&amp;m=19&amp;f=7#f7[/url:jshjzcsz]
