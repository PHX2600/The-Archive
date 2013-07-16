## C and Assembly - Part I
Posted by **opcode** on Fri January 11th, 2008 04:59:37 AM

This post is to introduce programmers to x86 assembly language.  Before you run
away, the code uses the C language and basic inline assembly.  By doing this,
anyone may begin writing a C program and see how assembly instructions work.

Anyone with GCC can compile this.

Lets start:
Open an editor of your choice and save the following file as 'main.c'

   #include &lt;stdio&#46;h&gt;

   long variable = 0; /* A global variable */

   int main(void) {
      printf(&quot;The value of variable is %l\n&quot;, variable);
      variable++;
      printf(&quot;The new value of variable is %l\n\n&quot;, variable);

      return 0;
   }

After saving this, open a console and in the directory of your source file, type:

   $ gcc ./main.c -o ./part-01

This will compile our small program into an executable.  Then type

   $ ./part-01

The value of variable is 0
The new value of variable is 1

Simple, I know.  But let's now change a piece of it into assembly language.  Open main.c again and change it to the following:

   #include &lt;stdio&#46;h&gt;

   long variable = 0; /* A global variable */

   int main(void) {
      printf(&quot;The value of variable is %l\n&quot;, variable);
      asm(&quot;mov	%eax, &#91;variable&#93;&quot;);
      asm(&quot;inc	%eax&quot;);
      asm(&quot;mov	&#91;variable&#93;, %eax&quot;);
      printf(&quot;The new value of variable is %l\n\n&quot;, variable);

      return 0;
   }

This time from the command prompt, type the following:

   $ gcc -masm=intel ./main.c -o ./part-01

When you run the program again:

   $ ./part-01

The value of variable is 0
The new value of variable is 1

As you can see, you acquire the same result.

While those three lines of x86 assembly language can be written in one line, I
want to expose the programmer to more than one instruction.

Assembly code in the Intel syntax has the following format:

   Instruction		destination, source

While that syntax looks confusing, look at the way equations and programs
operate in the real world! For example: y = mx + b

The variable 'y' is the destination of the operation 'mx + b'.  Likewise when
writing C programs, the destination variable sits on the left side of the equal
sign.  We will maintain this syntax hereon.

Just like any high level language, the CPU has its own variables called
registers.  They are named A, B, C and D.  When we want to use these registers
as 32-bit values (i.e. long), they simply become EAX, EBX, ECX and EDX.  Don't
let that change scare you away; its there to help you!

The first assembly instruction we encounter is 'mov' which is short for...you
guessed it, 'move.'  It moves data from one location to another.  In this case,
we take the contents of our variable 'variable' and store it into the CPU
register EAX.  EAX now equals 0.

Second, we have the 'inc' instruction which increments a value.  Since EAX = 0,
after the 'inc %eax' instruction, EAX then equals 1.

Third, we store the value of EAX (which is now 1) into the variable 'variable'.

I know this wasn't much, but I'm not certain what difficulties people have or
would like to know about assembly, but if anyone wishes to have more simple
examples, I'm willing to put together some more C and assembly code so people
can see how it works.  Just give me some ideas and I'll be happy to post some
more.

--------------------------------------------------------------------------------

Posted by **nak** on Fri January 11th, 2008 10:55:55 AM

Cool! Thanks for the tutorial.

--------------------------------------------------------------------------------

Posted by **dual** on Tue February 12th, 2008 10:18:44 PM

Thanks for the tutorial!

--------------------------------------------------------------------------------

Posted by **Valveritas** on Wed February 13th, 2008 06:27:16 AM

Looks great.  It's it necessary to be adept with C to get something out of this
tutorial? I'm guessing not, but thought I'd ask just in case. ;)

--------------------------------------------------------------------------------

Posted by **RetroTech1541** on Tue July 29th, 2008 03:05:51 AM

I never could figure out how to do that, I was full of questions. Thanks for the
tut, you got me to check something of my todo list.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue July 29th, 2008 04:09:05 PM

nice good info for us hardware guys who wanna see how the other half lives. LOL
