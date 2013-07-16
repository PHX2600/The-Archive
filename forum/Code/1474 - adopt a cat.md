## adopt a cat
Posted by **RetroTech1541** on Sat October 15th, 2011 07:29:52 PM

Saw logic's post showing us a method for scanning and reporting scans of minecraft servers. thought it was very cool. the people that do minecraft video's on youtube don't seem like they are expecting a buffer overrun. i did notice his script had use for cat so i though i'd hand out my cat real quick which after compilation takes 5 to 6 k of disk after a strip. cat is a real simple ascii mode copy command and the code isn't complex, but there is a loop in the copy function and a bonus loop in main makes an argument processor. i remember thinking in the 90s that command.com was missing loops real bad and it should have them which got me hunting down a copy of os/2 for it's scripting language rexx. a linux distro was really what the doctor was prescribing, it's like, want a full featured batch command language on an ordinary pc? take your pick. didn't have amiga and the st lacked it too. anyway, not sure how many milliseconds you can save by compiling your own cat optimized for your linux, but you can if you want. anyway, show a gui bigot a script like the minecraft scanner or as basic as cat and either one they will think, what do i click? <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

[code:2bf1rhwm]
/*
 * File&#58; cat&#46;c
 * Vers&#58; 0&#46;13
 * Auth&#58; rt1541
 * Date&#58; 6&#58;00 PM MST 11/12/2010
 * Desc&#58; *nix 'cat' workalike - concatenate files
 * todo&#58; parameters,
 *       '-' pass stdin as input
 */

/*
 * Import headers
 */
#include &lt;stdio&#46;h&gt;

/*
 * Function prototypes
 */
int cat(FILE*);

/*
 * Function definitions
 */

/*
 * Function&#58; main
 * Accepts&#58; filenames for files to output to stdout
 * 	    If no filename is given, main will input
 *          from stdout
 */
int main(int argc, char* argv&#91;&#93;) {

	int n;
	char c;
	FILE* fileIn;

	if(argc == 0)
		cat(stdout);
	for(n = 1; n &lt; argc; n++) {
		fileIn = fopen(argv&#91;n&#93;, &quot;r&quot;);
		if(fileIn != NULL)
			cat(fileIn);
	}
        if(fileIn != NULL &amp;&amp; n &gt; 0) fclose(fileIn);
	return 0;
}

/*
 * Function&#58; cat
 * Accepts&#58; Pointer to type file
 * Performs&#58; Inputs a character at a time and 

outputs
 *	     to standard out
 * Returns&#58; 0 on success
 */
int cat(FILE* fileIn) {
	char c;

        /* 
           &#91;NOTE&#93;
           Here's a puzzle
           Can you see a way to only use the assignment &quot;c = fgetc(fileIn)&#58;&quot;
           Once but not output a visible null terminator on ms-windows w/o
           increasing the total line length of the function&#46;
           &#91;/NOTE&#93; */
	for(c = fgetc(fileIn); c != EOF; c = fgetc(fileIn))
		fputc(c, stdout);
	return 0;
}
[/code:2bf1rhwm]

--------------------------------------------------------------------------------

Posted by **nak** on Fri October 21st, 2011 07:30:55 PM

*sober-edit*
OK. Now that I've looked at the code (I am a C newbie still, thanks for helping me with that program years ago <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> )
I am sort of unclear on the puzzle you present.
I know a null terminator is \x00 -- is it visible on windows? I don't really have a windows computer with a compiler here.

I'm not sure if this would do what you're talking about&#058;

[code:227484j1]    int cat(FILE* fileIn) {
       char c;
       while((c =fgetc(fileIn)) != EOF)
          fputc(c, stdout);
       return 0;
    }[/code:227484j1]

I'll do some experiments on for loops vs. while loops, just for kicks in a bit.

*another edit*
This is the original disassembly of the cat function using `while`
[code:227484j1]0804854d &lt;cat&gt;&#58;
 804854d&#58;       55                      push   %ebp
 804854e&#58;       89 e5                   mov    %esp,%ebp
 8048550&#58;       83 ec 28                sub    $0x28,%esp
 8048553&#58;       eb 16                   jmp    804856b &lt;cat+0x1e&gt;
 8048555&#58;       8b 15 20 a0 04 08       mov    0x804a020,%edx
 804855b&#58;       0f be 45 f7             movsbl -0x9(%ebp),%eax
 804855f&#58;       89 54 24 04             mov    %edx,0x4(%esp)
 8048563&#58;       89 04 24                mov    %eax,(%esp)
 8048566&#58;       e8 91 fe ff ff          call   80483fc &lt;fputc@plt&gt;
 804856b&#58;       8b 45 08                mov    0x8(%ebp),%eax
 804856e&#58;       89 04 24                mov    %eax,(%esp)
 8048571&#58;       e8 76 fe ff ff          call   80483ec &lt;fgetc@plt&gt;
 8048576&#58;       88 45 f7                mov    %al,-0x9(%ebp)
 8048579&#58;       80 7d f7 ff             cmpb   $0xff,-0x9(%ebp)
 804857d&#58;       75 d6                   jne    8048555 &lt;cat+0x8&gt;
 804857f&#58;       b8 00 00 00 00          mov    $0x0,%eax
 8048584&#58;       c9                      leave
 8048585&#58;       c3                      ret
 8048586&#58;       90                      nop[/code:227484j1]

this is the disassembly for the original `if` implementation
[code:227484j1]0804854d &lt;cat&gt;&#58;
 804854d&#58;	55                   	push   %ebp
 804854e&#58;	89 e5                	mov    %esp,%ebp
 8048550&#58;	83 ec 28             	sub    $0x28,%esp
 8048553&#58;	8b 45 08             	mov    0x8(%ebp),%eax
 8048556&#58;	89 04 24             	mov    %eax,(%esp)
 8048559&#58;	e8 8e fe ff ff       	call   80483ec &lt;fgetc@plt&gt;
 804855e&#58;	88 45 f7             	mov    %al,-0x9(%ebp)
 8048561&#58;	eb 24                	jmp    8048587 &lt;cat+0x3a&gt;
 8048563&#58;	8b 15 20 a0 04 08    	mov    0x804a020,%edx
 8048569&#58;	0f be 45 f7          	movsbl -0x9(%ebp),%eax
 804856d&#58;	89 54 24 04          	mov    %edx,0x4(%esp)
 8048571&#58;	89 04 24             	mov    %eax,(%esp)
 8048574&#58;	e8 83 fe ff ff       	call   80483fc &lt;fputc@plt&gt;
 8048579&#58;	8b 45 08             	mov    0x8(%ebp),%eax
 804857c&#58;	89 04 24             	mov    %eax,(%esp)
 804857f&#58;	e8 68 fe ff ff       	call   80483ec &lt;fgetc@plt&gt;
 8048584&#58;	88 45 f7             	mov    %al,-0x9(%ebp)
 8048587&#58;	80 7d f7 ff          	cmpb   $0xff,-0x9(%ebp)
 804858b&#58;	75 d6                	jne    8048563 &lt;cat+0x16&gt;
 804858d&#58;	b8 00 00 00 00       	mov    $0x0,%eax
 8048592&#58;	c9                   	leave  
 8048593&#58;	c3                   	ret    
 8048594&#58;	90                   	nop[/code:227484j1]

*edit again -- I guess I've been learning stuff today...*
Ok learned a bit more, EOF == -1 (pretty much right?) ... and I really don't understand &quot;visible null terminator&quot; so, I guess I'll do something else now. Like cut up a zucchini, put it on a frozen pizza and toss it in the oven where it belongs.

--------------------------------------------------------------------------------

Posted by **nak** on Wed October 26th, 2011 11:34:00 PM

[code:2u35zc2w]    /*
    * Import headers
    */
    #include &lt;stdio&#46;h&gt;

    /*
    * Function prototypes
    */
    int cat(FILE*);

    /*
    * Function definitions
    */

    /*
    * Function&#58; main
    * Accepts&#58; filenames for files to output to stdout
    *        If no filename is given, main will input
    *          from stdout
    */
    int main(int argc, char* argv&#91;&#93;) {

       int n;
       char c;
       FILE* fileIn;
       if(argc == 1){
          cat(stdout);
          printf(&quot;Missing file arguments&#46; Exiting&#46;\n&quot;);
          return 0;
       }
       for(n = 1; n &lt; argc; n++) {
          fileIn = fopen(argv&#91;n&#93;, &quot;r&quot;);
          if(fileIn != NULL)
             cat(fileIn);
       }
   
       if(fileIn != NULL &amp;&amp; n &gt; 0) fclose(fileIn);
       return 0;
    }

    /*
    * Function&#58; cat
    * Accepts&#58; Pointer to type file
    * Performs&#58; Inputs a character at a time and
    * outputs to standard out
    * Returns&#58; 0 on success
    */
    int cat(FILE* fileIn) {
       char c;

            /*
               Here's a puzzle
               Can you see a way to only use the assignment &quot;c = fgetc(fileIn)&#58;&quot;
               Once but not output a visible null terminator on ms-windows w/o
               increasing the total line length of the function&#46;
            */
       while((c=fgetc(fileIn)) != -1)
          fputc(c, stdout);
       return 0;
    }
[/code:2u35zc2w]

Well, I learned about the FILE* pointer... pretty cool, and fixed up argc == 0 (it's always going to be 1 because of the binary name right? and made it so it doesn't segfault on argc == 1, ie no arguments)

Maybe I'll get the hang of this C thing someday <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->
