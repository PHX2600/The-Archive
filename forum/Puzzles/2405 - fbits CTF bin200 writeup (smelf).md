## fbits CTF bin200 writeup (smelf)
Posted by **AltF4** on Tue March 19th, 2013 09:06:55 PM

We receive a binary called &quot;smelf&quot; for this challenge. You can find this file and all the others we used during the challenge here: <!-- m --><a class="postlink" href="https://github.com/PHX2600/forbiddenbits-2013/tree/master/smelf">https://github.com/PHX2600/forbiddenbit ... ster/smelf</a><!-- m -->

Running the &quot;file&quot; command on it shows us that it is in fact a 64 bit GNU/Linux executable:

[code:3b0ar81s]smelf&#58; ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2&#46;6&#46;15, BuildID&#91;sha1&#93;=0x4b595fd7b18fbb4426a226d97d24c894d4e2530c, stripped[/code:3b0ar81s]

The important takeaways from this is that:
A) You'll need a 64 bit GNU/Linux machine for this
B) It's dynamically loaded, so we can use ltrace  (though we don't wind up using it for this challenge)
C) Debugging symbols have been stripped. So reverse engineering becomes slightly more annoying.

Let's try running the program and see what we get:

[code:3b0ar81s]&#46;/smelf 
Segmentation fault (core dumped)[/code:3b0ar81s]

Well that's curious... Maybe we can try giving it an argument?
[code:3b0ar81s]
&#46;/smelf lolwut
Wrong![/code:3b0ar81s]

Ah ha. It printed &quot;Wrong!&quot;. I guess that means that some input would be &quot;Right&quot;, which would likely be the flag. Let's take a look at what strings are in the executable, which usually gives us a decent glimpse into the sort of things it may be doing.
[code:3b0ar81s]
strings smelf
/lib64/ld-linux-x86-64&#46;so&#46;2
_YKD
__gmon_start__
libc&#46;so&#46;6
exit
printf
strlen
__libc_start_main
GLIBC_2&#46;2&#46;5
fff&#46;
fffff&#46;
l$ L
t$(L
|$0H
Wrong!
Done!
$	I6	
*KLH
[/code:3b0ar81s]
You can see that the string &quot;Wrong!&quot; is there. And right below it is the string &quot;Done!&quot;. Good, that must be what it prints when you get the password right. So how about we try to work backwards. Let's disassemble the binary, and see where &quot;Done!&quot; is printed, and what needs to happen to make it print that. Note that there is no obvious &quot;flag&quot; text in the strings, here. (That would be too easy) The flag will likely be encrypted or encoded in some way as to make trivial grabbing of it impossible.

Run a disassembly using objdump:
[code:3b0ar81s]objdump -D -M intel smelf &gt; disassembly[/code:3b0ar81s]

This will disassemble the executable, showing all sections (-D flag) and display it in intel syntax (-M intel), outputting it all to a text file named disassembly (&gt; disassembly) The disassembly is too large to fully paste here, but you can run it on your own. I'll post snippets as needed.

Where do we start in this mess? Let's first find our string &quot;Done!&quot;, and see where it is referenced. It will likely be in one of the data sections, like .data or .rodata (read only data). Objdump doesn't print the strings nicely for us, unfortunately. (Is there a plugin or something to do this?) It will display the data sections in their raw bytes and also interpreted as code. So we need to instead look for &quot;44 6f 6e 65 21 00&quot;. You will find it in the .rodata section after all!

[code:3b0ar81s]  400833&#58;	44 6f                	rex&#46;R outs dx,DWORD PTR ds&#58;&#91;rsi&#93;
  400835&#58;	6e                   	outs   dx,BYTE PTR ds&#58;&#91;rsi&#93;
  400836&#58;	65 21 00             	and    DWORD PTR gs&#58;&#91;rax&#93;,eax[/code:3b0ar81s]

Pay no attention to the bogus assembly instructions to the right. That's just objdump trying in vain to interpret the data as code. Our string starts at address 400833, so now we need to search the disassembly for where this address is located. And we find one here:
[code:3b0ar81s]
  4006f0&#58;	b8 33 08 40 00       	mov    eax,0x400833
  4006f5&#58;	48 89 c7             	mov    rdi,rax
  4006f8&#58;	b8 00 00 00 00       	mov    eax,0x0
  4006fd&#58;	e8 8e fd ff ff       	call   400490 &lt;printf@plt&gt;[/code:3b0ar81s]

You can see that the pointer to the string &quot;Done!&quot; is being loaded into rdi as an argument to the printf function. Okay, great. Now we have to answer the question: &quot;How do we get execution to get here&quot; Let's zoom out a little bit and see how this printf is used in the context of whatever function it's in. With debugging symbols removed, function boundaries aren't displayed, so let's try to add some in. The &quot;ret&quot; instruction usually denotes the end of a function, so just do a simple string replace in the dump. Replace &quot;ret&quot; with &quot;ret\n\n&quot;. That will give you some visual aid to see where the functions are.

Now we can see the whole function:

 [code:3b0ar81s] 400601&#58;	55                   	push   rbp
  400602&#58;	48 89 e5             	mov    rbp,rsp
  400605&#58;	53                   	push   rbx
  400606&#58;	48 83 ec 28          	sub    rsp,0x28
  40060a&#58;	48 89 7d d8          	mov    QWORD PTR &#91;rbp-0x28&#93;,rdi
  40060e&#58;	89 75 d4             	mov    DWORD PTR &#91;rbp-0x2c&#93;,esi
  400611&#58;	48 8b 45 d8          	mov    rax,QWORD PTR &#91;rbp-0x28&#93;
  400615&#58;	48 89 c7             	mov    rdi,rax
  400618&#58;	e8 a3 fe ff ff       	call   4004c0 &lt;strlen@plt&gt;
  40061d&#58;	48 83 f8 1d          	cmp    rax,0x1d
  400621&#58;	76 1c                	jbe    40063f &lt;strlen@plt+0x17f&gt;
  400623&#58;	b8 2c 08 40 00       	mov    eax,0x40082c
  400628&#58;	48 89 c7             	mov    rdi,rax
  40062b&#58;	b8 00 00 00 00       	mov    eax,0x0
  400630&#58;	e8 5b fe ff ff       	call   400490 &lt;printf@plt&gt;
  400635&#58;	bf 00 00 00 00       	mov    edi,0x0
  40063a&#58;	e8 61 fe ff ff       	call   4004a0 &lt;exit@plt&gt;
  40063f&#58;	c7 45 ec 00 00 00 00 	mov    DWORD PTR &#91;rbp-0x14&#93;,0x0
  400646&#58;	e9 8a 00 00 00       	jmp    4006d5 &lt;strlen@plt+0x215&gt;
  40064b&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40064e&#58;	48 98                	cdqe   
  400650&#58;	48 89 c3             	mov    rbx,rax
  400653&#58;	48 03 5d d8          	add    rbx,QWORD PTR &#91;rbp-0x28&#93;
  400657&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40065a&#58;	48 98                	cdqe   
  40065c&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  400660&#58;	0f b6 00             	movzx  eax,BYTE PTR &#91;rax&#93;
  400663&#58;	89 c6                	mov    esi,eax
  400665&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  400668&#58;	48 98                	cdqe   
  40066a&#58;	48 83 c0 01          	add    rax,0x1
  40066e&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  400672&#58;	0f b6 00             	movzx  eax,BYTE PTR &#91;rax&#93;
  400675&#58;	89 c2                	mov    edx,eax
  400677&#58;	c0 fa 07             	sar    dl,0x7
  40067a&#58;	c0 ea 06             	shr    dl,0x6
  40067d&#58;	01 d0                	add    eax,edx
  40067f&#58;	83 e0 03             	and    eax,0x3
  400682&#58;	28 d0                	sub    al,dl
  400684&#58;	0f be c0             	movsx  eax,al
  400687&#58;	c1 e0 03             	shl    eax,0x3
  40068a&#58;	8b 55 d4             	mov    edx,DWORD PTR &#91;rbp-0x2c&#93;
  40068d&#58;	89 d7                	mov    edi,edx
  40068f&#58;	89 c1                	mov    ecx,eax
  400691&#58;	d3 ef                	shr    edi,cl
  400693&#58;	89 f8                	mov    eax,edi
  400695&#58;	31 f0                	xor    eax,esi
  400697&#58;	88 03                	mov    BYTE PTR &#91;rbx&#93;,al
  400699&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40069c&#58;	48 98                	cdqe   
  40069e&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  4006a2&#58;	0f b6 10             	movzx  edx,BYTE PTR &#91;rax&#93;
  4006a5&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  4006a8&#58;	48 98                	cdqe   
  4006aa&#58;	0f b6 80 30 10 60 00 	movzx  eax,BYTE PTR &#91;rax+0x601030&#93;
  4006b1&#58;	38 c2                	cmp    dl,al
  4006b3&#58;	74 1c                	je     4006d1 &lt;strlen@plt+0x211&gt;
  4006b5&#58;	b8 2c 08 40 00       	mov    eax,0x40082c
  4006ba&#58;	48 89 c7             	mov    rdi,rax
  4006bd&#58;	b8 00 00 00 00       	mov    eax,0x0
  4006c2&#58;	e8 c9 fd ff ff       	call   400490 &lt;printf@plt&gt;
  4006c7&#58;	bf 00 00 00 00       	mov    edi,0x0
  4006cc&#58;	e8 cf fd ff ff       	call   4004a0 &lt;exit@plt&gt;
  4006d1&#58;	83 45 ec 01          	add    DWORD PTR &#91;rbp-0x14&#93;,0x1
  4006d5&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  4006d8&#58;	48 63 d8             	movsxd rbx,eax
  4006db&#58;	48 8b 45 d8          	mov    rax,QWORD PTR &#91;rbp-0x28&#93;
  4006df&#58;	48 89 c7             	mov    rdi,rax
  4006e2&#58;	e8 d9 fd ff ff       	call   4004c0 &lt;strlen@plt&gt;
  4006e7&#58;	48 39 c3             	cmp    rbx,rax
  4006ea&#58;	0f 82 5b ff ff ff    	jb     40064b &lt;strlen@plt+0x18b&gt;
  4006f0&#58;	b8 33 08 40 00       	mov    eax,0x400833
  4006f5&#58;	48 89 c7             	mov    rdi,rax
  4006f8&#58;	b8 00 00 00 00       	mov    eax,0x0
  4006fd&#58;	e8 8e fd ff ff       	call   400490 &lt;printf@plt&gt;
  400702&#58;	48 83 c4 28          	add    rsp,0x28
  400706&#58;	5b                   	pop    rbx
  400707&#58;	c9                   	leave  
  400708&#58;	c3                   	ret[/code:3b0ar81s]

Notice that our target print is near the bottom. Let's tear this function apart, bit by bit until we understand what's going on. Along the way, we'll write the C code that will duplicate what the binary is doing.

[code:3b0ar81s]  400601&#58;	55                   	push   rbp
  400602&#58;	48 89 e5             	mov    rbp,rsp
  400605&#58;	53                   	push   rbx
  400606&#58;	48 83 ec 28          	sub    rsp,0x28
  40060a&#58;	48 89 7d d8          	mov    QWORD PTR &#91;rbp-0x28&#93;,rdi
  40060e&#58;	89 75 d4             	mov    DWORD PTR &#91;rbp-0x2c&#93;,esi[/code:3b0ar81s]

This is all just a part of the function prologue: ordinary stuff you find at the top of every function. It saves the state of some registers that we're about to use, so that when we return, they will be in place again. What you want to pay attention to in the prologue is what is being moved onto local stack memory. Local memory will be referenced as [rbp-XXX] (below the base pointer) In this case, it's the rdi and esi (&quot;destination&quot; and &quot;source&quot; registers). Meaning that our function takes two input parameters, but we don't know what they are just yet.

[code:3b0ar81s]  400611&#58;	48 8b 45 d8          	mov    rax,QWORD PTR &#91;rbp-0x28&#93;
  400615&#58;	48 89 c7             	mov    rdi,rax
  400618&#58;	e8 a3 fe ff ff       	call   4004c0 &lt;strlen@plt&gt;[/code:3b0ar81s]

Here, we see one of our input parameters being fed into strlen(). So that means it must be a pointer to a string.
[code:3b0ar81s]
  40061d&#58;	48 83 f8 1d          	cmp    rax,0x1d
  400621&#58;	76 1c                	jbe    40063f &lt;strlen@plt+0x17f&gt;[/code:3b0ar81s]

The return value of a function is put in rax (the &quot;A&quot; register). So here we are comparing the string's returned length to 0x1d (29 in decimal). If the length is below this limit, then we jump to 40063f. Otherwise we go to the next instruction (if we're length 30 or more). Let's take a peek at the next few instructions to see what happens in we're over the length limit:

[code:3b0ar81s]  400623&#58;	b8 2c 08 40 00       	mov    eax,0x40082c
  400628&#58;	48 89 c7             	mov    rdi,rax
  40062b&#58;	b8 00 00 00 00       	mov    eax,0x0
  400630&#58;	e8 5b fe ff ff       	call   400490 &lt;printf@plt&gt;
  400635&#58;	bf 00 00 00 00       	mov    edi,0x0
  40063a&#58;	e8 61 fe ff ff       	call   4004a0 &lt;exit@plt&gt;[/code:3b0ar81s]

Looks like we print something and then exit. Why, I'd bet good money that what it prints is &quot;Wrong!&quot;. Let's see if that's true. The pointer 0x40082c is loaded as an argument to the printf function. What happens to be at address 0x40082c?

[code:3b0ar81s]  40082c&#58;	57                   	push   rdi
  40082d&#58;	72 6f                	jb     40089e &lt;strlen@plt+0x3de&gt;
  40082f&#58;	6e                   	outs   dx,BYTE PTR ds&#58;&#91;rsi&#93;
  400830&#58;	67 21 00             	and    DWORD PTR &#91;eax&#93;,eax[/code:3b0ar81s]

ASCII bytes for &quot;Wrong!&quot;. Cool! So it appears that our password is at most 29 characters. Not something I'd want to brute force. Let's step back and see where we jump to if our string is less than 29 characters: (address 40063f)

[code:3b0ar81s]  40063f&#58;	c7 45 ec 00 00 00 00 	mov    DWORD PTR &#91;rbp-0x14&#93;,0x0
  400646&#58;	e9 8a 00 00 00       	jmp    4006d5 &lt;strlen@plt+0x215&gt;
[/code:3b0ar81s]
This zero's out a section in memory (some local variable). Let's call this variable &quot;i&quot;. judging from how it's used later in the function, it is probably an integer. Then it jumps to somewhere down in the function. So let's follow the jump:

[code:3b0ar81s]  4006d5&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  4006d8&#58;	48 63 d8             	movsxd rbx,eax
  4006db&#58;	48 8b 45 d8          	mov    rax,QWORD PTR &#91;rbp-0x28&#93;
  4006df&#58;	48 89 c7             	mov    rdi,rax
  4006e2&#58;	e8 d9 fd ff ff       	call   4004c0 &lt;strlen@plt&gt;[/code:3b0ar81s]

This loads &quot;i&quot; into the rbx register, and our password ([rbp-0x28]) into strlen again.

[code:3b0ar81s]  4006e7&#58;	48 39 c3             	cmp    rbx,rax
  4006ea&#58;	0f 82 5b ff ff ff    	jb     40064b &lt;strlen@plt+0x18b&gt;[/code:3b0ar81s]

Then we compare the two. If &quot;i&quot; is less than the password length, then we jump backwards in the function, which means that we continue to loop. If &quot;i&quot; is equal or greater than the string's length, we continue. The next few instructions just so happen to be:
[code:3b0ar81s]
  4006f0&#58;	b8 33 08 40 00       	mov    eax,0x400833
  4006f5&#58;	48 89 c7             	mov    rdi,rax
  4006f8&#58;	b8 00 00 00 00       	mov    eax,0x0
  4006fd&#58;	e8 8e fd ff ff       	call   400490 &lt;printf@plt&gt;[/code:3b0ar81s]

Which is our &quot;Done!&quot; string getting printed. Awesome. We're getting closer to knowing how to get the correct password. Let's take this opportunity to write out what we know in terms of C code.

[code:3b0ar81s]#include &quot;stdlib&#46;h&quot;
#include &quot;stdio&#46;h&quot;
#include &quot;string&#46;h&quot;
int main(int argc, char **argv)
{
	if(strlen(argv&#91;1&#93;) &gt; 29)
	{
		printf(&quot;Wrong!&quot;);
		exit(0);
	}
	int i = 0;
	while( i &lt; strlen(argv&#91;1&#93;) )
	{
		//NOT REVERSED YET
		i++;
	}
	printf(&quot;Done!&quot;)
}
[/code:3b0ar81s]
Now let's look at the assembly for the area at the top of the loop. This is the place that we jump to if &quot;i&quot; is less than the password's length. (40064b)

[code:3b0ar81s]  40064b&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40064e&#58;	48 98                	cdqe   
  400650&#58;	48 89 c3             	mov    rbx,rax
  400653&#58;	48 03 5d d8          	add    rbx,QWORD PTR &#91;rbp-0x28&#93;[/code:3b0ar81s]

Remember that this is a 64 bit executable.So when you move a double word (32 bits), as we do in the first instruction, it only takes up the lower half of the register. The cdqe extends the value out into the rest of the register so that we don't accidentally have left over junk there. So what this does is add together &quot;i&quot; and our input password. Equivalent to saying:

[code:3b0ar81s]//Saved in rbx
char *pointer = &amp;password&#91;i&#93;;[/code:3b0ar81s]

Next is:

[code:3b0ar81s]  400657&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40065a&#58;	48 98                	cdqe   
  40065c&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  400660&#58;	0f b6 00             	movzx  eax,BYTE PTR &#91;rax&#93;
  400663&#58;	89 c6                	mov    esi,eax[/code:3b0ar81s]

This is almost the same code, except that you can see that we're getting the actual value of password[i] out, not a pointer to it.

[code:3b0ar81s]//Saved in esi
char first = password&#91;i&#93;;[/code:3b0ar81s]

[code:3b0ar81s]  400665&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  400668&#58;	48 98                	cdqe   
  40066a&#58;	48 83 c0 01          	add    rax,0x1
  40066e&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  400672&#58;	0f b6 00             	movzx  eax,BYTE PTR &#91;rax&#93;
  400675&#58;	89 c2                	mov    edx,eax[/code:3b0ar81s]

Again, this is really similar. We get &quot;i&quot; out of memory, add one to it, then get the character value of password at that value. Equivalent to:

[code:3b0ar81s]//Saved in edx and eax
char second = password&#91;i+1&#93;;
char secondCopy = second;
[/code:3b0ar81s]
Now things get a little crazy. The function does a whole bunch of bit shifts, masks, and lookups. Just take it one step at a time.
[code:3b0ar81s]
  400677&#58;	c0 fa 07             	sar    dl,0x7[/code:3b0ar81s]

This is an &quot;arithmetic&quot; bit shift right. This is different than an ordinary shift, look it up online if you don't know what it means. But it's not all that important that you do.

[code:3b0ar81s]//arithmetic shift
secondCopy = secondCopy &gt;&gt; 7;
[/code:3b0ar81s]
Next:

[code:3b0ar81s]  40067a&#58;	c0 ea 06             	shr    dl,0x6[/code:3b0ar81s]

Which is a &quot;logical&quot; bit shift right. In C code, you have to do a cast to an unsigned integer to force this to happen:

[code:3b0ar81s]//logical shift
secondCopy = ((unsigned char)secondCopy) &gt;&gt; 6;
[/code:3b0ar81s]
Next:

[code:3b0ar81s]  40067d&#58;	01 d0                	add    eax,edx
  40067f&#58;	83 e0 03             	and    eax,0x3
  400682&#58;	28 d0                	sub    al,dl
  400684&#58;	0f be c0             	movsx  eax,al
  400687&#58;	c1 e0 03             	shl    eax,0x3[/code:3b0ar81s]

Which in C would translate to:

[code:3b0ar81s]second += secondCopy;
second &amp;= 3;
second -= secondCopy;
second = second &lt;&lt; 3;[/code:3b0ar81s]

Next:

[code:3b0ar81s]  40068a&#58;	8b 55 d4             	mov    edx,DWORD PTR &#91;rbp-0x2c&#93;[/code:3b0ar81s]

Now this is interesting. We finally get around to using the other input parameter that the function had. You can also see that [rbp-0x2c] is not used anywhere else in this function. This parameter was initially set into esi, so let's see if we can find out what was passed into it. Search the disassembly for where our function is called and you will find:

[code:3b0ar81s]  400718&#58;	8b 15 32 09 20 00    	mov    edx,DWORD PTR &#91;rip+0x200932&#93;        # 601050 &lt;strlen@plt+0x200b90&gt;
  &#46;&#46;&#46;
  400729&#58;	89 d6                	mov    esi,edx
  40072b&#58;	48 89 c7             	mov    rdi,rax
  40072e&#58;	e8 ce fe ff ff       	call   400601[/code:3b0ar81s]

You can see that a pointer to address 601050 is passed into this parameter. I wonder what is at that memory location:
[code:3b0ar81s]
  601050&#58;	78 56                	js     6010a8 &lt;strlen@plt+0x200be8&gt;
  601052&#58;	34 12                	xor    al,0x12[/code:3b0ar81s]

In the .data section, we can see that this points to 0x12345678. A hardcoded value, interesting. Continuing on with our function... 

[code:3b0ar81s]  40068a&#58;	8b 55 d4             	mov    edx,DWORD PTR &#91;rbp-0x2c&#93;
  40068d&#58;	89 d7                	mov    edi,edx
  40068f&#58;	89 c1                	mov    ecx,eax
  400691&#58;	d3 ef                	shr    edi,cl
  400693&#58;	89 f8                	mov    eax,edi[/code:3b0ar81s]

In C this would be:

[code:3b0ar81s]//offset == second parameter
uint32_t offsetCopy = offset &gt;&gt; second;[/code:3b0ar81s]

We are shifting this input &quot;offset&quot; to the right a bunch of times according to the value we just computed based off of the password.

[code:3b0ar81s]  400695&#58;	31 f0                	xor    eax,esi
  400697&#58;	88 03                	mov    BYTE PTR &#91;rbx&#93;,al[/code:3b0ar81s]

We then xor this new value with password[i], and save it back into the password array.

[code:3b0ar81s]password&#91;i&#93; = password&#91;i&#93; ^ offsetCopy;[/code:3b0ar81s]

Next is:

[code:3b0ar81s]  400699&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  40069c&#58;	48 98                	cdqe   
  40069e&#58;	48 03 45 d8          	add    rax,QWORD PTR &#91;rbp-0x28&#93;
  4006a2&#58;	0f b6 10             	movzx  edx,BYTE PTR &#91;rax&#93;[/code:3b0ar81s]

This looks familar by now, doesn't it? We're taking &quot;i&quot; and adding it to password, saving the value there into register edx. Next up is:
[code:3b0ar81s]
  4006a5&#58;	8b 45 ec             	mov    eax,DWORD PTR &#91;rbp-0x14&#93;
  4006a8&#58;	48 98                	cdqe   
  4006aa&#58;	0f b6 80 30 10 60 00 	movzx  eax,BYTE PTR &#91;rax+0x601030&#93;[/code:3b0ar81s]

Ahh! Here we go. This time, we're looking up the &quot;i&quot;th value in a byte array starting at 0x601030. This is a buffer we haven't seen yet. What's in this buffer? (look in the .data section)
[code:3b0ar81s]
  601030&#58;	4c 10 49 00          
  601034&#58;	24 09          
  601036&#58;	49                   
  601037&#58;	36 09 05 1e 26 25 4b 	
  60103e&#58;	00 74 65 41          
  601042&#58;	00 1e               
  601044&#58;	2a 4b 00             
  601047&#58;	1e                   	
  601048&#58;	2a 4b 4c             	
  60104b&#58;	48[/code:3b0ar81s]

Looks like some random bytes. Likely encrypted bytes. This must be our encrypted password! We're getting close! Next up, the executable does:
[code:3b0ar81s]
  4006b1&#58;	38 c2                	cmp    dl,al
  4006b3&#58;	74 1c                	je     4006d1 &lt;strlen@plt+0x211&gt;[/code:3b0ar81s]

This compares the password[i] that we just modified, and ciphertext[i]. If they are not equal, then we fall through to a quit code:

[code:3b0ar81s]  4006b5&#58;	b8 2c 08 40 00       	mov    eax,0x40082c
  4006ba&#58;	48 89 c7             	mov    rdi,rax
  4006bd&#58;	b8 00 00 00 00       	mov    eax,0x0
  4006c2&#58;	e8 c9 fd ff ff       	call   400490 &lt;printf@plt&gt;
  4006c7&#58;	bf 00 00 00 00       	mov    edi,0x0
  4006cc&#58;	e8 cf fd ff ff       	call   4004a0 &lt;exit@plt&gt;[/code:3b0ar81s]

So in C this would be:
[code:3b0ar81s]
if(password&#91;i&#93; != ciphertext&#91;i&#93;)
{
	printf(&quot;Wrong!&quot;);
	exit(0);
}[/code:3b0ar81s]

And that's it! We've now completely reverse engineered the executable. The whole source code looks like this: (slightly modified to be more readable in places. But logically equivalent)

[code:3b0ar81s]#include &quot;stdlib&#46;h&quot;
#include &quot;stdio&#46;h&quot;
#include &quot;string&#46;h&quot;
#include &quot;stdint&#46;h&quot;

char ciphertext&#91;&#93; = &quot;\x4c\x10\x49\x00\x24\x09\x49\x36\x09\x05\x1e\x26\x25\x4b\x00\x74\x65\x41\x00\x1e\x2a\x4b\x00\x1e\x2a\x4b\x4c\x48\x00\x00\x00\x00\x78\x56\x34\x12&quot;;

uint32_t offset = 0x12345678;

int main(int argc, char **argv)
{
	char *input = argv&#91;1&#93;;
	char originalInput&#91;50&#93;;
	memset(originalInput, '\0', sizeof(originalInput));
	strncpy(originalInput, input, sizeof(originalInput));

	int length = strlen(input);
	if(length &gt;= 30)
	{
		printf(&quot;Too long\n&quot;);
		return 30;
	}

	for(int i = 0; i &lt; length; i++)
	{
		char first = input&#91;i&#93;;
		char second = input&#91;i+1&#93;;
		char secondCopy = second;
		
		//arithmetic shift
		secondCopy = secondCopy &gt;&gt; 7;
		//logical shift
		secondCopy = ((unsigned char)secondCopy) &gt;&gt; 6;	
		//add back in
		second += secondCopy;
		//mask out all but 2 LSBs
		second &amp;= 3;
		second -= secondCopy;
		second = second &lt;&lt; 3;

		uint32_t offsetCopy = offset &gt;&gt; second;

		//actually change the input string itself
		input&#91;i&#93; = input&#91;i&#93; ^ offsetCopy;

		if(input&#91;i&#93; != ciphertext&#91;i&#93;)
		{
			printf(&quot;i=%d\n&quot;, i);
			return i;
		}
		printf(&quot;Got one\n&quot;);
		fflush(NULL);

	}
	printf(&quot;SUCCESS!\n&quot;);
	printf(&quot;original input=%s\n&quot;, originalInput);
	fflush(NULL);
	return 0;
}[/code:3b0ar81s]

Now we know the ciphertext, the key, and the encryption algorithm, and so we should be able to find the plaintext that made it. There are two possible strategies here:

a) We could work &quot;forward&quot;. You see, there is a side channel attack against this encryption scheme. The password is NOT checked at the very end of the encryption. It's done at each character. This means that you don't have to try every 256^29 possible password combinations. You would only have to try 256 * 29 combinations. A big deal. Once you found the correct password[i], you don't have to bother computing it again.

The trouble with this method is twofold. The first is that to make ciphertext[i], we combine password[i] AND password[i+1]. So actually in order to brute force the password, we'd have to try every two byte combination, all the way up to 29 characters. Increasing the complexity and making implementation annoying.

Second is that the encryption scheme was not terribly well written. There are multiple &quot;valid&quot; passwords which can satisfy the requirements. For example, the string &quot;4&quot; is a valid password! Go ahead and try it!

[code:3b0ar81s]&#46;/smelf 4
Done![/code:3b0ar81s]

But unfortunately, &quot;4&quot; is not the flag. (I tried submitting it!) This would mean that our brute forcing program would not be able to easily know when it is done. This makes a O(256 * 29) brute forcer difficult...

b)  We could work &quot;backwards&quot;. As we noted above, ciphertext[i] is like so:

[quote:3b0ar81s]ciphertext[i] = plaintext[i] ^ mod(plaintext[i+1]);[/quote:3b0ar81s]

Where &quot;mod&quot; is that crazy set of bit shifts and lookups and such. This MUST mean that plaintext is exactly 1 character longer than ciphertext. And that extra character is almost surely a trailing NULL. So then, we know:

[quote:3b0ar81s]plaintext[last] = ciphertext[last] ^ mod(NULL)
plaintext[last] = ciphertext[last] ^ NULL
plaintext[last] = ciphertext[last][/quote:3b0ar81s]

So we know the last value of the plaintext now! (it's hiding in plaintext) Now we can cascade this all the way down the line backwards. Using last plaintext value, we can find the second to last value. And so on. Here is some C code to do exactly that:

[code:3b0ar81s]#include &quot;stdlib&#46;h&quot;
#include &quot;stdio&#46;h&quot;
#include &quot;string&#46;h&quot;
#include &quot;stdint&#46;h&quot;

char ciphertext&#91;&#93; = &quot;\x4c\x10\x49\x00\x24\x09\x49\x36\x09\x05\x1e\x26\x25\x4b\x00\x74\x65\x41\x00\x1e\x2a\x4b\x00\x1e\x2a\x4b\x4c\x48&quot;;

uint32_t offset = 0x12345678;

char mod(char second)
{
	char secondCopy = second;
	//arithmetic shift
	secondCopy = secondCopy &gt;&gt; 7;
	//logical shift
	secondCopy = ((unsigned char)secondCopy) &gt;&gt; 6;	
	//add back in
	second += secondCopy;
	//mask out all but 2 LSBs
	second &amp;= 3;
	second -= secondCopy;
	second = second &lt;&lt; 3;
	uint32_t offsetCopy = offset &gt;&gt; second;
	return offset &gt;&gt; second;
}

int main(int argc, char **argv)
{
	int length = sizeof(ciphertext);
	char plaintext&#91;sizeof(ciphertext) + 1&#93;;
	memset(plaintext, '\0', sizeof(plaintext));

	for(int i = length-2; i &gt;= 0; i--)
	{
		//actually change the input string itself
		plaintext&#91;i&#93; = ciphertext&#91;i&#93; ^ mod(plaintext&#91;i+1&#93;);
	}
	printf(&quot;plaintext=%s\n&quot;, plaintext);
	return 0;
}[/code:3b0ar81s]

Run this code and will will get:

[code:3b0ar81s]&#46;/solve
plaintext=xF146_1$_1f4734f394f834f8340[/code:3b0ar81s]

And that's your flag! To verify, try running it back through smelf:
[code:3b0ar81s]
&#46;/smelf xF146_1$_1f4734f394f834f8340
Done![/code:3b0ar81s]

200 Points to team Pi Backwards! And off to the next challenge!
