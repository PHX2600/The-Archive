## Perl and it's interpretation of hex
Posted by **XlogicX** on Mon February 6th, 2012 01:11:08 AM

Firstly, I love Perl, but I don't favor higher level languages in general, and I did find an example of why in Perl (though it doesn't happen as often with this language). The short story is that low level languages do what you tell them to, high level doesn't always.

The long story:
I could write a line like below:
[code:2iye811l]my $string = &quot;\x58\x59&quot;;[/code:2iye811l]

If I printed this:
[code:2iye811l]print $string;[/code:2iye811l]
I would actually get: XY
That's fine, that's actually what I'm going for; a true hex output.

The complication comes from getting that same \x58\x59 from a file:
[code:2iye811l]my $string = &lt;&gt;;
print $string;[/code:2iye811l]
I would actually get: \x58\x59
Huh? and yes, I get the same result from chomping it. Perl just interprets this differently for some reason. So, just in case anybody else wanted to know how to do this from a file:
[code:2iye811l]my $string = &lt;&gt;;
print pack(&quot;C*&quot;, map { $_ ? hex($_) &#58;() } split(/\\x/, $string));
[/code:2iye811l]
This breaks \x58\x59 up into pieces defined by the RegEx of /\\x/ (\x) so we get two pieces (58 and 59), the rest of that command converts/packs the two ASCII characters as if they were hex, and two bytes turns into one. Everything in the world is right again <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **nak** on Mon February 6th, 2012 10:43:38 AM

yeah, working with binary in scripting languages is something that has to be learned over time <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->
I encountered similar issues with python and got around it using the [http&#58;//docs&#46;python&#46;org/library/struct&#46;html]('struct' module) -- &quot;Interpret strings as packed binary data&quot;

Scripting languages deal with strings mostly and _try_ to make people's lives easier <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

Node.JS has a really good implementation for dealing with binary: <!-- m --><a class="postlink" href="http://nodejs.org/docs/latest/api/buffers.html#buffers">http://nodejs.org/docs/latest/api/buffers.html#buffers</a><!-- m -->
So you can write javascript that does low level binary manipulation!

But I don't know perl at all <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( --> so I can't say if there's any easier way of dealing with binary, but cool looking hack either way <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Mon February 6th, 2012 11:43:37 PM

What I hate is that the first code example I gave does output actual hex, but only if it's a hard-coded string. If you give it the exact data from a file (of which doesn't have the linefeed or any other garbage), then it treats it differently. This is merely because the source of the data (of which is identical) is different.

That's ok though, perl has been treating me great otherwise. I was playing with some funny anti-forensics ideas and decided to learn perl to weaponize it. perl was easy enough to learn/use that I have a weaponized version a week later. Now it's time to add features. Let the feature creep begin.

--------------------------------------------------------------------------------

Posted by **nak** on Tue February 7th, 2012 01:29:33 AM

[quote=&quot;XlogicX&quot;:1fn8koie]What I hate is that the first code example I gave does output actual hex, but only if it's a hard-coded string. If you give it the exact data from a file (of which doesn't have the linefeed or any other garbage), then it treats it differently. This is merely because the source of the data (of which is identical) is different.

That's ok though, perl has been treating me great otherwise. I was playing with some funny anti-forensics ideas and decided to learn perl to weaponize it. perl was easy enough to learn/use that I have a weaponized version a week later. Now it's time to add features. Let the feature creep begin.[/quote:1fn8koie]

Ah I think I see what you mean.
my $string = &quot;\x58\x59&quot;

That is in the original perl file, and the \x is a special escape character that says &quot;The next 2 characters is supposed to be a hex number&quot; (you already know this I know, but hear me out...)

SO when you load from a text file with: \x58\x59
You're getting an ASCII string with data like so:
\x5C\x78\x35\x38           \x5C\x78\x35\x39
(without the spaces)
you can pop open your file in a hex editor to check it out.
I tried to google how to read binary in perl, but I cried as I tried to scan over and make sense of this: [url:1fn8koie]http&#58;//oreilly&#46;com/catalog/cookbook/chapter/ch08&#46;html#19069[/url:1fn8koie]

Its late and I'm feeling a little loopy, but I will continue... and hope I'm not misinterpreting your situation <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

So.. if you're storing escaped hex values in an ascii file, your way is a fine way of getting the hex digits out, then decoding them into characters.
But, depending on your application, you might be making a lot of extra steps where you could be writing straight binary(hex) without dealing with all those \x_hex_escapes

Hope that was semi coherent, but there should be a way to deal with binary file modes in perl... THERE MUST! in python its like f.open('file', 'rb') #reading binary

something like that... gl!

--------------------------------------------------------------------------------

Posted by **XlogicX** on Tue February 7th, 2012 03:36:59 PM

There really should be an easier way, but at least I found something that works. And yeah, knew about the \x convention. It is useful...when it's hardcoded, but not from a file. Whatever though, on to bigger and greater things with this project.
