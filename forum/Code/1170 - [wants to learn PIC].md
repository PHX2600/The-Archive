## [wants to learn PIC]
Posted by **XlogicX** on Fri December 11th, 2009 02:34:07 AM

[feels like asshole for not using Slipmodes PIC dev board sooner]

I still need to find the board before I finish packing completely (if I havn't already packed it).

I still think the propeller is far superior. But I like that there is a 8 pin PIC and that they cost abut $1 a piece. I'm thinking low cost swarm computing. I also like assembly a lot more lately, and most PICs are about 35 instructions, that's pretty RISC.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri December 11th, 2009 09:59:20 AM

I just finished reviewing a bare bones RISC design in my verilog class that only has 8 instructions. 

one byte ALU operations:
ADD - add two registers and store back to a destination reg
SUB - subtract two registers and store back to a destination reg
AND - and two registers and store back to a destination reg
NOT - not a single reg with itself and store back to a destination reg

two byte instructions for jumps and memory manipulation:
RD -read
WR - write
BR - branch ( basic jump )
BRZ - branch on zero ( jumps based on the zero flag )

it was just an in class exercise but we went through doing basic operations with these 8 instructions, pretty fun stuff.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri December 11th, 2009 09:49:11 PM

PIC is the micro controller i use the most haven't worked to much with propeller not that i think its bad just PIC and yes even arduino has served my need but i may just have to pick up some propeller stuff if its more powerful in the same size package i could  use it.

*EDIT Which programmer kit would you recommend?

--------------------------------------------------------------------------------

Posted by **XlogicX** on Sat December 12th, 2009 12:08:38 AM

It is much more powerful than the PIC, and very unique and fun to program.
If cost isn’t a consideration, go nuts with the Pro dev board (though it’s not small):
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerDevelopmentBoards/tabid/514/CategoryID/73/List/0/Level/a/ProductID/515/Default.aspx?SortField=ProductName,ProductName">http://www.parallax.com/Store/Microcont ... roductName</a><!-- m -->

If you want the most bang for the buck, go with the propeller demo board, I don’t have this one, but would recommend it the most since it has a lot of peripheral hardware:
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerDevelopmentBoards/tabid/514/CategoryID/73/List/0/Level/a/ProductID/340/Default.aspx?SortField=ProductName,ProductName">http://www.parallax.com/Store/Microcont ... roductName</a><!-- m -->

If you want simplicity, and something even cheaper, go with this (I own several of these, mine are the non-usb though):
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerDevelopmentBoards/tabid/514/CategoryID/73/List/0/Level/a/ProductID/509/Default.aspx?SortField=ProductName,ProductName">http://www.parallax.com/Store/Microcont ... roductName</a><!-- m -->

This one is new, wish I would have gotten it in the very beginning due to size and purpose:
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerDevelopmentBoards/tabid/514/CategoryID/73/List/0/Level/a/ProductID/602/Default.aspx?SortField=ProductName,ProductName">http://www.parallax.com/Store/Microcont ... roductName</a><!-- m -->

And for ultimate size considerations (though you will sacrifice some I/O), go with:
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerTools/tabid/143/CategoryID/19/List/0/SortField/0/Level/a/ProductID/448/Default.aspx">http://www.parallax.com/Store/Microcont ... fault.aspx</a><!-- m -->

Or if you just want the chip:
<!-- m --><a class="postlink" href="http://www.parallax.com/Store/Microcontrollers/PropellerChips/tabid/142/CategoryID/18/List/0/SortField/0/Level/a/ProductID/334/Default.aspx">http://www.parallax.com/Store/Microcont ... fault.aspx</a><!-- m -->

If you have any questions about programming it, I am now confident enough with the system to answer them. I have used practically every opcode (never thought I would get to that point).
