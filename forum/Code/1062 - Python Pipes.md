## Python Pipes
Posted by **AltF4Warrior** on Wed August 12th, 2009 09:22:55 PM

So I'm trying to pick up Python as a good scripting language. (I won't lie. It's for 'sploits. C is just really cumbersome sometimes)

Anyway, I'm having a headache with piping output to another program. Like this...

Say I have a program that takes a string input via STDIN, not command line args. (Like a gets() call) I want to pass it a string created in a python script. Kind of like this:

python -c &quot;print '\x90'*128 + shellcode + returnaddress&quot; | ./vulnprogram

And the above works... but it has to be done on it's own line. I'm looking for a way to do it actually inside a script, not a one-off python command. There's probably an easy way that I just missed in my Googling. 

Thanks!
