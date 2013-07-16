## C and Assembly - Part II: Revisiting part I
Posted by **opcode** on Mon January 14th, 2008 07:55:01 AM

In this example we will change our first program a little.

So if you could, go open up that source file.  If you don't have it, I have it pasted below:
Name this file [b:30uc6qn8]main.c[/b:30uc6qn8] and save it in a directory called part-02.
[code:30uc6qn8]
#include &lt;stdio&#46;h&gt;

long variable = 0;   /* A global variable */

int main(void) {
   printf(&quot;The value of variable is %d\n&quot;, variable);
   asm(&quot;mov	%eax, &#91;variable&#93;&quot;);
   asm(&quot;inc	%eax&quot;);
   asm(&quot;mov	&#91;variable&#93;, %eax&quot;);
   printf(&quot;The new value of variable is %d\n\n&quot;, variable);

   return 0;
}
[/code:30uc6qn8]

The first thing we are going to do is reduce that inline assembly code to just one line.  I'm doing this because it's important to know the different ways a single thing can be programmed.

Change it to the following:
[code:30uc6qn8]
#include &lt;stdio&#46;h&gt;

long variable = 0;   /* A global variable */

int main(void) {
   printf(&quot;The value of variable is %d\n&quot;, variable);
   asm(&quot;add	dword ptr &#91;variable&#93;, 0x00000001&quot;);
   printf(&quot;The new value of variable is %d\n\n&quot;, variable);

   return 0;
}
[/code:30uc6qn8]
First, we removed the two move instructions.
Second, we introduced a new instruction called '[b:30uc6qn8]add[/b:30uc6qn8]'.
Third, we are telling GCC to add 1 to a 32-bit variable with '[b:30uc6qn8]dword ptr[/b:30uc6qn8]'.
If we were adding 1 to a 16-bit value (equivilant to a variable type of [b:30uc6qn8]short[/b:30uc6qn8]), we would use [b:30uc6qn8]word ptr[/b:30uc6qn8] instead.
If we were adding 1 to an 8-bit value (equivilant to a variable type of [b:30uc6qn8]char[/b:30uc6qn8]), we would use [b:30uc6qn8]byte ptr[/b:30uc6qn8].

To give an idea how these affect output.  Change your code to the following:
[code:30uc6qn8]
#include &lt;stdio&#46;h&gt;

long variable = 255;   /* A global variable */

int main(void) {
   printf(&quot;The value of variable is %d\n&quot;, variable);
   asm(&quot;add	byte ptr &#91;variable&#93;, 0x01&quot;);
   printf(&quot;The new value of variable is %d\n\n&quot;, variable);

   return 0;
}
[/code:30uc6qn8]
Compile as so:
$ gcc -masm=intel ./main.c -o ./part-02
$ ./part-02
The value of variable is 255
The new value of variable is 0

What just happened?  Did you see that?  Our variable ([b:30uc6qn8]which is 32 bits by the way[/b:30uc6qn8]) went from 255 to 0!  We know an [b:30uc6qn8]unsigned long[/b:30uc6qn8] has a range of 0 to 4,294,967,295!  Why is this?

This happened because we changed our [b:30uc6qn8]add[/b:30uc6qn8] instruction to add [b:30uc6qn8]1[/b:30uc6qn8] to a byte in memory.  [b:30uc6qn8]byte ptr[/b:30uc6qn8] tells GCC it is using it as a byte pointer (this is similar to how C pointers work).  Since it will only operate on that one byte, the rest of the variable is left unchanged!  We can therefore perform operations on that byte while preserving the rest of the variable!!!

We can also rewrite this one more time to the following:
[code:30uc6qn8]
#include &lt;stdio&#46;h&gt;

long variable = 255;   /* A global variable */

int main(void) {
   printf(&quot;The value of variable is %d\n&quot;, variable);
   asm(&quot;inc	dword ptr &#91;variable&#93;&quot;);
   printf(&quot;The new value of variable is %d\n\n&quot;, variable);

   return 0;
}
[/code:30uc6qn8]
$ gcc -masm=intel ./main.c -o ./part-02
$ ./part-02
The value of variable is 255
The new value of variable is 256

This time, our variable goes from 255 to 256.  We end up using the increment instruction '[b:30uc6qn8]inc[/b:30uc6qn8]'.

As an exercise, rewrite the previous code to increment our variable's lowest 8-bits (hint: change what type of pointer it is).

If you're at all stuck, here is what it should look like:
[code:30uc6qn8]
#include &lt;stdio&#46;h&gt;

long variable = 255;   /* A global variable */

int main(void) {
   printf(&quot;The value of variable is %d\n&quot;, variable);
   asm(&quot;inc	byte ptr &#91;variable&#93;&quot;);
   printf(&quot;The new value of variable is %d\n\n&quot;, variable);

   return 0;
}
[/code:30uc6qn8]
$ gcc -masm=intel ./main.c -o ./part-02
$ ./part-02
The value of variable is 255
The new value of variable is 0

We could also change [b:30uc6qn8]dword ptr[/b:30uc6qn8] to [b:30uc6qn8]word ptr[/b:30uc6qn8] instead of just [b:30uc6qn8]byte ptr[/b:30uc6qn8].

The next part will cover CPU registers in more depth.

Does anyone have any questions otherwise?

--------------------------------------------------------------------------------

Posted by **dual** on Tue February 12th, 2008 10:24:34 PM

Moar please.
