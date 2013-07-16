## first one
Posted by **TerrorDrone** on Tue May 26th, 2009 09:14:07 AM

i know its not too much but this is my first real code working in python as i just started learning it 2 days ago
wish i would have sooner much easier than C

[code:14y25so4]# does ohms law calcualtions
# calculates watts with given data

def print_options()&#58;
    print 'Options'
    print ' What do you need to find?'
    print &quot; 'p' print options&quot;
    print &quot; 'v' volts&quot;
    print &quot; 'i'current&quot;
    print &quot; 'r' resistance&quot;
    print &quot; 'q' quit the program&quot;

def cal_volts (i,r)&#58;
    return  i * r

def cal_watts_v (i,r)&#58;
    return i * i * r

def cal_current (v,r)&#58;
    return v / r
def cal_watts_i (v,r)&#58;
    return v * v / r

def cal_resistance (v,i)&#58;
    return v / i
def cal_watts_r (v,i)&#58;
    return v * i

choice =&quot;p&quot;
while choice !='q'&#58;
    if choice == 'v'&#58;
         i = input('Amps&#58;')
         r = input ('Ohms&#58;')
         print 'volts&#58;',cal_volts (i,r)
         print 'watts&#58;' , cal_watts_v (i,r)
    elif choice == 'i'&#58;
         v = input ('Volts&#58;')
         r = input ('Ohms')
         print 'amps&#58;',cal_current (v,r)
         print 'watts&#58;', cal_watts_i (v,r)
    elif choice == 'r'&#58;
         v = input ('Volts&#58;')
         i = input ('Amps&#58;')
         print 'ohms&#58;',cal_resistance(v,i)
         print 'watts&#58;', cal_watts_r(v,i)
    elif choice != &quot;q&quot;&#58;
         print_options()
    choice = raw_input(&quot;option&#58; &quot;)

    

[/code:14y25so4]
next step is to add more calculations and have it work with input and output in engineering figures
*edit added watts calcualtions

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue May 26th, 2009 11:10:29 AM

Sweeet,

Yeah python is pretty epic, tons easier than C, some people put it down for being interpreted but not me. I work almost exclusively in python now, I only use C when I need the extra speed or more direct hardware access.

--------------------------------------------------------------------------------

Posted by **fightgar** on Wed May 27th, 2009 01:37:40 AM

I program by meditating really hard on &quot;I wish someone would write ....&quot; then I google it and I find out that someone wrote &quot;....&quot; and I'm like SWEET!

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed May 27th, 2009 02:37:25 PM

[quote=&quot;fightgar&quot;:l7qg8ghw]I program by meditating really hard on &quot;I wish someone would write ....&quot; then I google it and I find out that someone wrote &quot;....&quot; and I'm like SWEET![/quote:l7qg8ghw]

ahh the old jedi mind trick programming
&quot;this is the program you want to write&quot;

--------------------------------------------------------------------------------

Posted by **fightgar** on Thu May 28th, 2009 10:07:11 AM

Exactly terror &lt;3
But sometimes it just feels nice getting into the code yourself  <!-- s:geek: --><img src="{SMILIES_PATH}/icon_e_geek.gif" alt=":geek:" title="Geek" /><!-- s:geek: -->
