## Expanding loops to make program faster
Posted by **XlogicX** on Wed September 23rd, 2009 12:40:58 AM

[quote:1sabmgr2]Please excuse any code/syntax errors, this is just proof of concept (but pays off in practical use). This post is also of a context of a lower level language, some compilers may optimize this for you anyway (but don't always expect it).[/quote:1sabmgr2]

This is really only a concern when you need your code to run just a little bit faster. There is more than one type of ‘efficient’ code, some people would say that all else equal, the program that has less lines of code is the most efficient, others may say that the fastest program is the most efficient. My point is that those two traits can be mutually exclusive; less lines of code can actually make your program slower.

Say I want to take a number ‘x,’ and put it in location ‘y.’ The next pass through, you want to add 2 to ‘x’ and put that value in the next ‘y’ index location. You want to do this 5 times.

Psuedocode example:
[code:1sabmgr2]Int y&#91;4&#93;
Int inc = 0
For (x, x&lt;10, 2)
    store x in y&#91;inc&#93;
    inc++
[/code:1sabmgr2]

5 lines of code. This looks all and good. Here is what is really going on (though this looks more like a ‘ do while’ loop, it’s still about the same amount of code):
[code:1sabmgr2]Int y&#91;4&#93; = 0
Int inc = 0
X == 0
Store x in y&#91;inc&#93;
inc++
X = X + 2
If x &lt; 10, then
	Store x in y&#91;inc&#93;
inc++
X = X + 2
If x &lt; 10, then
	Store x in y&#91;inc&#93;
inc++
X = X + 2
If x &lt; 10, then
	Store x in y&#91;inc&#93;
inc++
X = X + 2
If x &lt; 10, then
	Store x in y&#91;inc&#93;
inc++
X = X + 2
If x &lt; 10, then
	(oh, it’s not, program stops here)
[/code:1sabmgr2]

Ok, so that was 23 instructions, what if we knew that the loop would always run 5 times? We would get:

[code:1sabmgr2]Int y&#91;4&#93; = 0
Int inc = 0
X == 0
Store x in y&#91;inc&#93;
inc++
X = X + 2
Store x in y&#91;inc&#93;
inc++
X = X + 2
Store x in y&#91;inc&#93;
inc++
X = X + 2
Store x in y&#91;inc&#93;
inc++
X = X + 2
Store x in y&#91;inc&#93;
inc++
X = X + 2
[/code:1sabmgr2]

That’s 18 instructions. I bet we could also say that we knew the y index would increment by 1 each time; it could be hard coded for more efficiency.
[code:1sabmgr2]
Int y&#91;4&#93; = 0
X == 0
Store x in y&#91;0&#93;
X = X + 2
Store x in y&#91;1&#93;
X = X + 2
Store x in y&#91;2&#93;
X = X + 2
Store x in y&#91;3&#93;
X = X + 2
Store x in y&#91;4&#93;
X = X + 2
[/code:1sabmgr2]

12 instructions, getting better. In some situations, it would also be safe to say that we would know that x is always initialized at 0 (though this is less practical, it really is the case in the explanation above the code). If this were the case, we would have
[code:1sabmgr2]
Int y&#91;4&#93; = 0
Store 0 in y&#91;0&#93;
Store 2 in y&#91;1&#93;
Store 4 in y&#91;2&#93;
Store 6 in y&#91;3&#93;
Store 8 in y&#91;4&#93;
[/code:1sabmgr2]

That’s 6 lines of code. It doesn’t look as efficient. A clever programmer would look at that, see a pattern and want to write a cool looking loop that makes it more “efficient.” The problem is that this 6 line program will run in around 6 clocks, where the 5 line program will run in around 23 clocks. Big difference.

I know there may have been too many assumptions to get at the 6 line program, but the 18 line program is very practical, you typically do know how many times you want to go through a loop. It really starts to add up if you try to run that loop thousands/millions of times in a second; adding those extra clocks in each loop will destroy you. The only trade off is you have to have enough memory/program-space for those extra instructions. When working with a microcontroller, sometimes this can be a concern (with 2k-32k of main memory, typically). And ‘expanding’ the loop can take up a lot of memory if you expect the loop to occur much more than 5 times.

This is why I like microcontrollers, it makes you actually have to think about this type of stuff.
