## Python/PHP text to speach
Posted by **Automated Penguin** on Tue October 14th, 2008 10:16:40 PM

I wrote a python program that searches the Merriam-Webster site for audio clips of words and plays them in order, creating a crude but hilarious tts program. this is that program ported to PHP


[url:c9hruxdm]http&#58;//blastwavelabs&#46;com/Media/Uploads/voice&#46;php?text=hello+phoenix+twenty+six+hundred+and+welcome+to+my+program[/url:c9hruxdm]

and heres the original python 

[code:c9hruxdm]
#!/usr/bin/python

import urllib, string, webbrowser, re


def findwav(word)&#58;
    url=&quot;http&#58;//www&#46;merriam-webster&#46;com/dictionary/&quot;+word
    res = urllib&#46;urlopen(url)

    
    while True&#58;   
        page = res&#46;readline()
        if len(page) ==0&#58;
            break # EOF
        
        txt=page

        re1='(javascript)'	# Word 1
        re2='(&#58;)'	        # Any Single Character 1
        re3='(popWin)'	        # Word 2
        re4='(\\(&#46;*\\))'	# Round Braces 1

        rg = re&#46;compile(re1+re2+re3+re4,re&#46;IGNORECASE|re&#46;DOTALL)
        m = rg&#46;search(txt)
        if m&#58;
            word1=m&#46;group(1)
            c1=m&#46;group(2)
            word2=m&#46;group(3)
            rbraces1=m&#46;group(4)
            return rbraces1


tts=raw_input(&quot;say what&#58; &quot;)&#46;split() # get a list of words to fetch

for word in tts&#58;
    try&#58;
        link= findwav(word)&#46;strip('()\'')
        link=link&#46;split(&quot;'&quot;)
        print link&#91;0&#93;
        url=&quot;http&#58;//www&#46;merriam-webster&#46;com&quot;+link&#91;0&#93;
        webbrowser&#46;open_new_tab(url)
    except&#58;
        print &quot;sorry, no wav D&#58;&quot;

    


[/code:c9hruxdm]

--------------------------------------------------------------------------------

Posted by **nak** on Wed October 15th, 2008 01:11:24 PM

That's really fun~

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 15th, 2008 07:04:26 PM

yeah pretty fun I just wish I knew a way to make it finish loading words in order, sometimes words get transposed or load ahead of others etc.
