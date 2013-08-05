## fbits CTF bin200 writeup (smelf)
Posted by **AltF4** on Tue March 19th, 2013 09:06:55 PM

We receive a binary called "smelf" for this challenge. You can find this file
and all the others we used during the challenge here:
<https://github.com/PHX2600/forbiddenbits-2013/tree/master/smelf>

Running the "file" command on it shows us that it is in fact a 64 bit GNU/Linux
executable:

    smelf: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0x4b595fd7b18fbb4426a226d97d24c894d4e2530c, stripped

The important takeaways from this is that:

  1. You'll need a 64 bit GNU/Linux machine for this
  2. It's dynamically loaded, so we can use ltrace (though we don't wind up
  using it for this challenge)f
  3. Debugging symbols have been stripped. So reverse engineering becomes
  slightly more annoying.

Let's try running the program and see what we get:

    ./smelf
    Segmentation fault (core dumped)

Well that's curious... Maybe we can try giving it an argument?

    ./smelf lolwut
    Wrong!

Ah ha. It printed "Wrong!". I guess that means that some input would be "Right",
which would likely be the flag. Let's take a look at what strings are in the
executable, which usually gives us a decent glimpse into the sort of things it
may be doing.

    strings smelf
    /lib64/ld-linux-x86-64.so.2
    _YKD
    __gmon_start__
    libc.so.6
    exit
    printf
    strlen
    __libc_start_main
    GLIBC_2.2.5
    fff.
    fffff.
    l$ L
    t$(L
    |$0H
    Wrong!
    Done!
    $	I6
    *KLH

You can see that the string "Wrong!" is there. And right below it is the string
"Done!". Good, that must be what it prints when you get the password right. So
how about we try to work backwards. Let's disassemble the binary, and see where
"Done!" is printed, and what needs to happen to make it print that. Note that
there is no obvious "flag" text in the strings, here. (That would be too easy)
The flag will likely be encrypted or encoded in some way as to make trivial
grabbing of it impossible.

Run a disassembly using objdump:

    objdump -D -M intel smelf > disassembly

This will disassemble the executable, showing all sections (-D flag) and display
it in intel syntax (-M intel), outputting it all to a text file named
disassembly (> disassembly) The disassembly is too large to fully paste here,
but you can run it on your own. I'll post snippets as needed.

Where do we start in this mess? Let's first find our string "Done!", and see
where it is referenced. It will likely be in one of the data sections, like
.data or .rodata (read only data). Objdump doesn't print the strings nicely for
us, unfortunately. (Is there a plugin or something to do this?) It will display
the data sections in their raw bytes and also interpreted as code. So we need to
instead look for "44 6f 6e 65 21 00". You will find it in the .rodata section
after all!

      400833:	44 6f                	rex.R outs dx,DWORD PTR ds:[rsi]
      400835:	6e                   	outs   dx,BYTE PTR ds:[rsi]
      400836:	65 21 00             	and    DWORD PTR gs:[rax],eax

Pay no attention to the bogus assembly instructions to the right. That's just
objdump trying in vain to interpret the data as code. Our string starts at
address 400833, so now we need to search the disassembly for where this address
is located. And we find one here:

      4006f0:	b8 33 08 40 00       	mov    eax,0x400833
      4006f5:	48 89 c7             	mov    rdi,rax
      4006f8:	b8 00 00 00 00       	mov    eax,0x0
      4006fd:	e8 8e fd ff ff       	call   400490 <printf@plt>

You can see that the pointer to the string "Done!" is being loaded into rdi as
an argument to the printf function. Okay, great. Now we have to answer the
question: "How do we get execution to get here" Let's zoom out a little bit and
see how this printf is used in the context of whatever function it's in. With
debugging symbols removed, function boundaries aren't displayed, so let's try to
add some in. The "ret" instruction usually denotes the end of a function, so
just do a simple string replace in the dump. Replace "ret" with "ret\n\n". That
will give you some visual aid to see where the functions are.

Now we can see the whole function:

      400601:	55                   	push   rbp
      400602:	48 89 e5             	mov    rbp,rsp
      400605:	53                   	push   rbx
      400606:	48 83 ec 28          	sub    rsp,0x28
      40060a:	48 89 7d d8          	mov    QWORD PTR [rbp-0x28],rdi
      40060e:	89 75 d4             	mov    DWORD PTR [rbp-0x2c],esi
      400611:	48 8b 45 d8          	mov    rax,QWORD PTR [rbp-0x28]
      400615:	48 89 c7             	mov    rdi,rax
      400618:	e8 a3 fe ff ff       	call   4004c0 <strlen@plt>
      40061d:	48 83 f8 1d          	cmp    rax,0x1d
      400621:	76 1c                	jbe    40063f <strlen@plt+0x17f>
      400623:	b8 2c 08 40 00       	mov    eax,0x40082c
      400628:	48 89 c7             	mov    rdi,rax
      40062b:	b8 00 00 00 00       	mov    eax,0x0
      400630:	e8 5b fe ff ff       	call   400490 <printf@plt>
      400635:	bf 00 00 00 00       	mov    edi,0x0
      40063a:	e8 61 fe ff ff       	call   4004a0 <exit@plt>
      40063f:	c7 45 ec 00 00 00 00 	mov    DWORD PTR [rbp-0x14],0x0
      400646:	e9 8a 00 00 00       	jmp    4006d5 <strlen@plt+0x215>
      40064b:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      40064e:	48 98                	cdqe
      400650:	48 89 c3             	mov    rbx,rax
      400653:	48 03 5d d8          	add    rbx,QWORD PTR [rbp-0x28]
      400657:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      40065a:	48 98                	cdqe
      40065c:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      400660:	0f b6 00             	movzx  eax,BYTE PTR [rax]
      400663:	89 c6                	mov    esi,eax
      400665:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      400668:	48 98                	cdqe
      40066a:	48 83 c0 01          	add    rax,0x1
      40066e:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      400672:	0f b6 00             	movzx  eax,BYTE PTR [rax]
      400675:	89 c2                	mov    edx,eax
      400677:	c0 fa 07             	sar    dl,0x7
      40067a:	c0 ea 06             	shr    dl,0x6
      40067d:	01 d0                	add    eax,edx
      40067f:	83 e0 03             	and    eax,0x3
      400682:	28 d0                	sub    al,dl
      400684:	0f be c0             	movsx  eax,al
      400687:	c1 e0 03             	shl    eax,0x3
      40068a:	8b 55 d4             	mov    edx,DWORD PTR [rbp-0x2c]
      40068d:	89 d7                	mov    edi,edx
      40068f:	89 c1                	mov    ecx,eax
      400691:	d3 ef                	shr    edi,cl
      400693:	89 f8                	mov    eax,edi
      400695:	31 f0                	xor    eax,esi
      400697:	88 03                	mov    BYTE PTR [rbx],al
      400699:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      40069c:	48 98                	cdqe
      40069e:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      4006a2:	0f b6 10             	movzx  edx,BYTE PTR [rax]
      4006a5:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      4006a8:	48 98                	cdqe
      4006aa:	0f b6 80 30 10 60 00 	movzx  eax,BYTE PTR [rax+0x601030]
      4006b1:	38 c2                	cmp    dl,al
      4006b3:	74 1c                	je     4006d1 <strlen@plt+0x211>
      4006b5:	b8 2c 08 40 00       	mov    eax,0x40082c
      4006ba:	48 89 c7             	mov    rdi,rax
      4006bd:	b8 00 00 00 00       	mov    eax,0x0
      4006c2:	e8 c9 fd ff ff       	call   400490 <printf@plt>
      4006c7:	bf 00 00 00 00       	mov    edi,0x0
      4006cc:	e8 cf fd ff ff       	call   4004a0 <exit@plt>
      4006d1:	83 45 ec 01          	add    DWORD PTR [rbp-0x14],0x1
      4006d5:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      4006d8:	48 63 d8             	movsxd rbx,eax
      4006db:	48 8b 45 d8          	mov    rax,QWORD PTR [rbp-0x28]
      4006df:	48 89 c7             	mov    rdi,rax
      4006e2:	e8 d9 fd ff ff       	call   4004c0 <strlen@plt>
      4006e7:	48 39 c3             	cmp    rbx,rax
      4006ea:	0f 82 5b ff ff ff    	jb     40064b <strlen@plt+0x18b>
      4006f0:	b8 33 08 40 00       	mov    eax,0x400833
      4006f5:	48 89 c7             	mov    rdi,rax
      4006f8:	b8 00 00 00 00       	mov    eax,0x0
      4006fd:	e8 8e fd ff ff       	call   400490 <printf@plt>
      400702:	48 83 c4 28          	add    rsp,0x28
      400706:	5b                   	pop    rbx
      400707:	c9                   	leave
      400708:	c3                   	ret

Notice that our target print is near the bottom. Let's tear this function apart,
bit by bit until we understand what's going on. Along the way, we'll write the C
code that will duplicate what the binary is doing.

      400601:	55                   	push   rbp
      400602:	48 89 e5             	mov    rbp,rsp
      400605:	53                   	push   rbx
      400606:	48 83 ec 28          	sub    rsp,0x28
      40060a:	48 89 7d d8          	mov    QWORD PTR [rbp-0x28],rdi
      40060e:	89 75 d4             	mov    DWORD PTR [rbp-0x2c],esi

This is all just a part of the function prologue: ordinary stuff you find at the
top of every function. It saves the state of some registers that we're about to
use, so that when we return, they will be in place again. What you want to pay
attention to in the prologue is what is being moved onto local stack memory.
Local memory will be referenced as [rbp-XXX] (below the base pointer) In this
case, it's the rdi and esi ("destination" and "source" registers). Meaning that
our function takes two input parameters, but we don't know what they are just
yet.

      400611:	48 8b 45 d8          	mov    rax,QWORD PTR [rbp-0x28]
      400615:	48 89 c7             	mov    rdi,rax
      400618:	e8 a3 fe ff ff       	call   4004c0 <strlen@plt>

Here, we see one of our input parameters being fed into strlen(). So that means
it must be a pointer to a string.

      40061d:	48 83 f8 1d          	cmp    rax,0x1d
      400621:	76 1c                	jbe    40063f <strlen@plt+0x17f>

The return value of a function is put in rax (the "A" register). So here we are
comparing the string's returned length to 0x1d (29 in decimal). If the length is
below this limit, then we jump to 40063f. Otherwise we go to the next
instruction (if we're length 30 or more). Let's take a peek at the next few
instructions to see what happens in we're over the length limit:

      400623:	b8 2c 08 40 00       	mov    eax,0x40082c
      400628:	48 89 c7             	mov    rdi,rax
      40062b:	b8 00 00 00 00       	mov    eax,0x0
      400630:	e8 5b fe ff ff       	call   400490 <printf@plt>
      400635:	bf 00 00 00 00       	mov    edi,0x0
      40063a:	e8 61 fe ff ff       	call   4004a0 <exit@plt>

Looks like we print something and then exit. Why, I'd bet good money that what
it prints is "Wrong!". Let's see if that's true. The pointer 0x40082c is loaded
as an argument to the printf function. What happens to be at address 0x40082c?

      40082c:	57                   	push   rdi
      40082d:	72 6f                	jb     40089e <strlen@plt+0x3de>
      40082f:	6e                   	outs   dx,BYTE PTR ds:[rsi]
      400830:	67 21 00             	and    DWORD PTR [eax],eax

ASCII bytes for "Wrong!". Cool! So it appears that our password is at most 29
characters. Not something I'd want to brute force. Let's step back and see where
we jump to if our string is less than 29 characters: (address 40063f)

      40063f:	c7 45 ec 00 00 00 00 	mov    DWORD PTR [rbp-0x14],0x0
      400646:	e9 8a 00 00 00       	jmp    4006d5 <strlen@plt+0x215>

This zero's out a section in memory (some local variable). Let's call this
variable "i". judging from how it's used later in the function, it is probably
an integer. Then it jumps to somewhere down in the function. So let's follow the
jump:

      4006d5:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      4006d8:	48 63 d8             	movsxd rbx,eax
      4006db:	48 8b 45 d8          	mov    rax,QWORD PTR [rbp-0x28]
      4006df:	48 89 c7             	mov    rdi,rax
      4006e2:	e8 d9 fd ff ff       	call   4004c0 <strlen@plt>

This loads "i" into the rbx register, and our password ([rbp-0x28]) into strlen
again.

      4006e7:	48 39 c3             	cmp    rbx,rax
      4006ea:	0f 82 5b ff ff ff    	jb     40064b <strlen@plt+0x18b>

Then we compare the two. If "i" is less than the password length, then we jump
backwards in the function, which means that we continue to loop. If "i" is equal
or greater than the string's length, we continue. The next few instructions just
so happen to be:

      4006f0:	b8 33 08 40 00       	mov    eax,0x400833
      4006f5:	48 89 c7             	mov    rdi,rax
      4006f8:	b8 00 00 00 00       	mov    eax,0x0
      4006fd:	e8 8e fd ff ff       	call   400490 <printf@plt>

Which is our "Done!" string getting printed. Awesome. We're getting closer to
knowing how to get the correct password. Let's take this opportunity to write
out what we know in terms of C code.

    #include "stdlib.h"
    #include "stdio.h"
    #include "string.h"
    int main(int argc, char **argv)
    {
    	if(strlen(argv[1]) > 29)
    	{
    		printf("Wrong!");
    		exit(0);
    	}
    	int i = 0;
    	while( i < strlen(argv[1]) )
    	{
    		//NOT REVERSED YET
    		i++;
    	}
    	printf("Done!")
    }

Now let's look at the assembly for the area at the top of the loop. This is the
place that we jump to if "i" is less than the password's length. (40064b)

[code:3b0ar81s]  40064b:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
  40064e:	48 98                	cdqe
  400650:	48 89 c3             	mov    rbx,rax
  400653:	48 03 5d d8          	add    rbx,QWORD PTR [rbp-0x28][/code:3b0ar81s]

Remember that this is a 64 bit executable.So when you move a double word (32
bits), as we do in the first instruction, it only takes up the lower half of the
register. The cdqe extends the value out into the rest of the register so that
we don't accidentally have left over junk there. So what this does is add
together "i" and our input password. Equivalent to saying:

    //Saved in rbx
    char *pointer = &password[i];

Next is:

      400657:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      40065a:	48 98                	cdqe
      40065c:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      400660:	0f b6 00             	movzx  eax,BYTE PTR [rax]
      400663:	89 c6                	mov    esi,eax

This is almost the same code, except that you can see that we're getting the
actual value of password[i] out, not a pointer to it.

    //Saved in esi
    char first = password[i];

      400665:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      400668:	48 98                	cdqe
      40066a:	48 83 c0 01          	add    rax,0x1
      40066e:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      400672:	0f b6 00             	movzx  eax,BYTE PTR [rax]
      400675:	89 c2                	mov    edx,eax

Again, this is really similar. We get "i" out of memory, add one to it, then get
the character value of password at that value. Equivalent to:

    //Saved in edx and eax
    char second = password[i+1];
    char secondCopy = second;

Now things get a little crazy. The function does a whole bunch of bit shifts,
masks, and lookups. Just take it one step at a time.

      400677:	c0 fa 07             	sar    dl,0x7

This is an "arithmetic" bit shift right. This is different than an ordinary
shift, look it up online if you don't know what it means. But it's not all that
important that you do.

    //arithmetic shift
    secondCopy = secondCopy >> 7;

Next:

      40067a:	c0 ea 06             	shr    dl,0x6

Which is a "logical" bit shift right. In C code, you have to do a cast to an
unsigned integer to force this to happen:

    //logical shift
    secondCopy = ((unsigned char)secondCopy) >> 6;

Next:

      40067d:	01 d0                	add    eax,edx
      40067f:	83 e0 03             	and    eax,0x3
      400682:	28 d0                	sub    al,dl
      400684:	0f be c0             	movsx  eax,al
      400687:	c1 e0 03             	shl    eax,0x3

Which in C would translate to:

    second += secondCopy;
    second &= 3;
    second -= secondCopy;
    second = second << 3;

Next:

      40068a:	8b 55 d4             	mov    edx,DWORD PTR [rbp-0x2c]

Now this is interesting. We finally get around to using the other input
parameter that the function had. You can also see that [rbp-0x2c] is not used
anywhere else in this function. This parameter was initially set into esi, so
let's see if we can find out what was passed into it. Search the disassembly for
where our function is called and you will find:

      400718:	8b 15 32 09 20 00    	mov    edx,DWORD PTR [rip+0x200932]        # 601050 <strlen@plt+0x200b90>
      ...
      400729:	89 d6                	mov    esi,edx
      40072b:	48 89 c7             	mov    rdi,rax
      40072e:	e8 ce fe ff ff       	call   400601

You can see that a pointer to address 601050 is passed into this parameter. I
wonder what is at that memory location:


      601050:	78 56                	js     6010a8 <strlen@plt+0x200be8>
      601052:	34 12                	xor    al,0x12

In the .data section, we can see that this points to 0x12345678. A hardcoded
value, interesting. Continuing on with our function...

      40068a:	8b 55 d4             	mov    edx,DWORD PTR [rbp-0x2c]
      40068d:	89 d7                	mov    edi,edx
      40068f:	89 c1                	mov    ecx,eax
      400691:	d3 ef                	shr    edi,cl
      400693:	89 f8                	mov    eax,edi

In C this would be:

    //offset == second parameter
    uint32_t offsetCopy = offset >> second;

We are shifting this input "offset" to the right a bunch of times according to
the value we just computed based off of the password.

      400695:	31 f0                	xor    eax,esi
      400697:	88 03                	mov    BYTE PTR [rbx],al

We then xor this new value with password[i], and save it back into the password
array.

    password[i] = password[i] ^ offsetCopy;

Next is:

      400699:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      40069c:	48 98                	cdqe
      40069e:	48 03 45 d8          	add    rax,QWORD PTR [rbp-0x28]
      4006a2:	0f b6 10             	movzx  edx,BYTE PTR [rax]

This looks familar by now, doesn't it? We're taking "i" and adding it to
password, saving the value there into register edx. Next up is:

      4006a5:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
      4006a8:	48 98                	cdqe
      4006aa:	0f b6 80 30 10 60 00 	movzx  eax,BYTE PTR [rax+0x601030]

Ahh! Here we go. This time, we're looking up the "i"th value in a byte array
starting at 0x601030. This is a buffer we haven't seen yet. What's in this
buffer? (look in the .data section)

      601030:	4c 10 49 00
      601034:	24 09
      601036:	49
      601037:	36 09 05 1e 26 25 4b
      60103e:	00 74 65 41
      601042:	00 1e
      601044:	2a 4b 00
      601047:	1e
      601048:	2a 4b 4c
      60104b:	48

Looks like some random bytes. Likely encrypted bytes. This must be our encrypted
password! We're getting close! Next up, the executable does:

      4006b1:	38 c2                	cmp    dl,al
      4006b3:	74 1c                	je     4006d1 <strlen@plt+0x211>

This compares the password[i] that we just modified, and ciphertext[i]. If they
are not equal, then we fall through to a quit code:

      4006b5:	b8 2c 08 40 00       	mov    eax,0x40082c
      4006ba:	48 89 c7             	mov    rdi,rax
      4006bd:	b8 00 00 00 00       	mov    eax,0x0
      4006c2:	e8 c9 fd ff ff       	call   400490 <printf@plt>
      4006c7:	bf 00 00 00 00       	mov    edi,0x0
      4006cc:	e8 cf fd ff ff       	call   4004a0 <exit@plt>

So in C this would be:

    if(password[i] != ciphertext[i])
    {
    	printf("Wrong!");
    	exit(0);
    }

And that's it! We've now completely reverse engineered the executable. The whole
source code looks like this: (slightly modified to be more readable in places.
But logically equivalent)

    #include "stdlib.h"
    #include "stdio.h"
    #include "string.h"
    #include "stdint.h"

    char ciphertext[] = "\x4c\x10\x49\x00\x24\x09\x49\x36\x09\x05\x1e\x26\x25\x4b\x00\x74\x65\x41\x00\x1e\x2a\x4b\x00\x1e\x2a\x4b\x4c\x48\x00\x00\x00\x00\x78\x56\x34\x12";

    uint32_t offset = 0x12345678;

    int main(int argc, char **argv)
    {
    	char *input = argv[1];
    	char originalInput[50];
    	memset(originalInput, '\0', sizeof(originalInput));
    	strncpy(originalInput, input, sizeof(originalInput));

    	int length = strlen(input);
    	if(length >= 30)
    	{
    		printf("Too long\n");
    		return 30;
    	}

    	for(int i = 0; i < length; i++)
    	{
    		char first = input[i];
    		char second = input[i+1];
    		char secondCopy = second;

    		//arithmetic shift
    		secondCopy = secondCopy >> 7;
    		//logical shift
    		secondCopy = ((unsigned char)secondCopy) >> 6;
    		//add back in
    		second += secondCopy;
    		//mask out all but 2 LSBs
    		second &= 3;
    		second -= secondCopy;
    		second = second << 3;

    		uint32_t offsetCopy = offset >> second;

    		//actually change the input string itself
    		input[i] = input[i] ^ offsetCopy;

    		if(input[i] != ciphertext[i])
    		{
    			printf("i=%d\n", i);
    			return i;
    		}
    		printf("Got one\n");
    		fflush(NULL);

    	}
    	printf("SUCCESS!\n");
    	printf("original input=%s\n", originalInput);
    	fflush(NULL);
    	return 0;
    }

Now we know the ciphertext, the key, and the encryption algorithm, and so we
should be able to find the plaintext that made it. There are two possible
strategies here:

a) We could work "forward". You see, there is a side channel attack against this
encryption scheme. The password is NOT checked at the very end of the
encryption. It's done at each character. This means that you don't have to try
every 256^29 possible password combinations. You would only have to try 256 * 29
combinations. A big deal. Once you found the correct password[i], you don't have
to bother computing it again.

The trouble with this method is twofold. The first is that to make
ciphertext[i], we combine password[i] AND password[i+1]. So actually in order to
brute force the password, we'd have to try every two byte combination, all the
way up to 29 characters. Increasing the complexity and making implementation
annoying.

Second is that the encryption scheme was not terribly well written. There are
multiple "valid" passwords which can satisfy the requirements. For example, the
string "4" is a valid password! Go ahead and try it!

    ./smelf 4
    Done!

But unfortunately, "4" is not the flag. (I tried submitting it!) This would mean
that our brute forcing program would not be able to easily know when it is done.
This makes a O(256 * 29) brute forcer difficult...

b)  We could work "backwards". As we noted above, ciphertext[i] is like so:

    ciphertext[i] = plaintext[i] ^ mod(plaintext[i+1]);

Where "mod" is that crazy set of bit shifts and lookups and such. This MUST mean
that plaintext is exactly 1 character longer than ciphertext. And that extra
character is almost surely a trailing NULL. So then, we know:

    plaintext[last] = ciphertext[last] ^ mod(NULL)
    plaintext[last] = ciphertext[last] ^ NULL
    plaintext[last] = ciphertext[last]

So we know the last value of the plaintext now! (it's hiding in plaintext) Now
we can cascade this all the way down the line backwards. Using last plaintext
value, we can find the second to last value. And so on. Here is some C code to
do exactly that:

    #include "stdlib.h"
    #include "stdio.h"
    #include "string.h"
    #include "stdint.h"

    char ciphertext[] = "\x4c\x10\x49\x00\x24\x09\x49\x36\x09\x05\x1e\x26\x25\x4b\x00\x74\x65\x41\x00\x1e\x2a\x4b\x00\x1e\x2a\x4b\x4c\x48";

    uint32_t offset = 0x12345678;

    char mod(char second)
    {
    	char secondCopy = second;
    	//arithmetic shift
    	secondCopy = secondCopy >> 7;
    	//logical shift
    	secondCopy = ((unsigned char)secondCopy) >> 6;
    	//add back in
    	second += secondCopy;
    	//mask out all but 2 LSBs
    	second &= 3;
    	second -= secondCopy;
    	second = second << 3;
    	uint32_t offsetCopy = offset >> second;
    	return offset >> second;
    }

    int main(int argc, char **argv)
    {
    	int length = sizeof(ciphertext);
    	char plaintext[sizeof(ciphertext) + 1];
    	memset(plaintext, '\0', sizeof(plaintext));

    	for(int i = length-2; i >= 0; i--)
    	{
    		//actually change the input string itself
    		plaintext[i] = ciphertext[i] ^ mod(plaintext[i+1]);
    	}
    	printf("plaintext=%s\n", plaintext);
    	return 0;
    }

Run this code and will will get:

    ./solve
    plaintext=xF146_1$_1f4734f394f834f8340

And that's your flag! To verify, try running it back through smelf:

    ./smelf xF146_1$_1f4734f394f834f8340
    Done!

200 Points to team Pi Backwards! And off to the next challenge!
