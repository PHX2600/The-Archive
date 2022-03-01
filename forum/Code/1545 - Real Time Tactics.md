## Real Time Tactics
Posted by **AltF4** on Mon January 23rd, 2012 08:09:08 PM

I have been working on an Open Source video game for the last month or two and it's starting to see the light of day! More to the point, I feel like the code base is in a position where it makes sense to get some others on board. And so here I am! (Currently the team consists of myself, my friend M3D (a professional game developer), and my brother who has done all the 3D work)

Code is here:
<https&#58;//github&#46;com/altf4/RealTimeTactics>

What is this thing?

Real Time Tactics is an online multiplayer Tactics game (in the same vein as Final Fantasy Tactics). The real-time element comes out of necessity since you don't want to have to wait for your opponent to make their next turn. It works much like the FF7 turn system. (IE: Characters have discrete turns. But the game doesn't wait for you. Once it's your turn you have to hurry to make a move or else you're wasting time)

Since networking protocols are what I do for a day job, I'm also making a rather complex-ish game server for it to live on. It's effectively an Open Source battle.net clone. It has match creation, joining, listing, etc.. Will soon have embedded chat, ranked matchmaking, etc... Everything you'd expect from a system like that. Currently I have a GTK+ front end for the client. (And then OGRE for the actual game once a match gets launched)

The code base is in C++, written using Eclipse IDE, and on an Ubuntu desktop. There are no current plans for a wind0ze port. The entirety of the code is licensed under the GNU GPLv3, and art assets a Creative Commons license. 

I'd love to have anyone who is interested to come and join us!  A good way to get started would of course be to download the code and give it a run. The HACKING file should include sufficient instructions, but feel free to contact me about anything. After that, a current list of bugs and other issues can be found here:

<https&#58;//github&#46;com/altf4/RealTimeTactics/issues>

Finding something minor there may be a good place to get going in the code. I'd especially appreciate it if the Phoenix2600 were able to find some bugs, particularly security related issues. Many praises will be gained for the finding of exploitable bugs in the server code.

Thanks a lot!
-Alt

--------------------------------------------------------------------------------

Posted by **Valveritas** on Mon January 23rd, 2012 11:16:11 PM

Definitely up my alley, but it'll probably be awhile before I'll be setup so I can look at it and give any feedback, or even help.  But sounds like you've got a great project developing.

--------------------------------------------------------------------------------

Posted by **nak** on Tue January 24th, 2012 12:14:25 AM

on my way  <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D --> 

[code:sl5vmn7u]nak@none&#58;~/src$ mkdir RealTimeTactics
nak@none&#58;~/src$ cd RealTimeTactics/
nak@none&#58;~/src/RealTimeTactics$ git clone git&#58;//github&#46;com/altf4/RealTimeTactics&#46;git
Initialized empty Git repository in /home/nak/src/RealTimeTactics/RealTimeTactics/&#46;git/
remote&#58; Counting objects&#58; 2033, done&#46;
remote&#58; Compressing objects&#58; 100% (745/745), done&#46;
Receiving Objects&#46;&#46;&#46;[/code:sl5vmn7u]

PS
Also this is the 2nd HACKING file I've run into today, I downloaded the LAME MP3 encoder source and I was like &quot;Oh that's nice! More tarballs should have that&quot; and what do I see later, this <!-- s:o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":o" title="Surprised" /><!-- s:o -->

PPS
dunno if I want to install eclipse, its not... skinny ... will sleep on it :p

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue January 24th, 2012 06:59:12 AM

[quote=&quot;CultLeadr&quot;:22sb0ez8]Definitely up my alley, but it'll probably be awhile before I'll be setup so I can look at it and give any feedback, or even help.  But sounds like you've got a great project developing.[/quote:22sb0ez8]

Thanks! I plan to spend a lot of time on it this year for sure. I actually want to generalize the game server so that any networked game can use it. (And take advantage of the ranked matchmaking, etc...)

[quote=&quot;nak&quot;:22sb0ez8]on my way  <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D --> 
PS
Also this is the 2nd HACKING file I've run into today, I downloaded the LAME MP3 encoder source and I was like &quot;Oh that's nice! More tarballs should have that&quot; and what do I see later, this <!-- s:o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":o" title="Surprised" /><!-- s:o -->

PPS
dunno if I want to install eclipse, its not... skinny ... will sleep on it :p[/quote:22sb0ez8]

True, Eclipse is a complicated IDE. It would actually be a nice exercise to try and not use Eclipse. There is nothing that &quot;requires&quot; it in the project. Eclipse just uses makefiles for building, so you ought to be able to just hit &quot;make&quot; and build everything yourself.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon January 30th, 2012 03:37:41 PM

I'll definitely give this a try in the near future.  In fact, remind me at this Friday's meeting and I'll definitely try it out.

As for development assistance, I'm a web developer and also have some decent (2D) graphics skills.  Also, I'd be happy to contribute ideas as well.  If there's something specific I can assist with, let me know.

--------------------------------------------------------------------------------

Posted by **nak** on Mon January 30th, 2012 06:46:51 PM

[quote=&quot;AltF4&quot;:1xjgd72r]Eclipse just uses makefiles for building, so you ought to be able to just hit &quot;make&quot; and build everything yourself.[/quote:1xjgd72r]

you mean hit &quot;make&quot; in eclipse or [http&#58;//linux&#46;about&#46;com/library/cmd/blcmdl1_make&#46;htm](make)

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon January 30th, 2012 10:42:53 PM

[quote=&quot;PHLAK&quot;:105q43g7]I'll definitely give this a try in the near future.  In fact, remind me at this Friday's meeting and I'll definitely try it out.

As for development assistance, I'm a web developer and also have some decent (2D) graphics skills.  Also, I'd be happy to contribute ideas as well.  If there's something specific I can assist with, let me know.[/quote:105q43g7]

Actually, maybe I can give a mini-presentation on it's current status. Like 5-10 minutes tops. There isn't TOO much to show. But what I have looks promising, IMO. And I've been spending a lot of time on it, so I feel like showing it off to someone.

And any contributions of any type and quantity are more than welcome!

[quote=&quot;nak&quot;:105q43g7]you mean hit &quot;make&quot; in eclipse or [http&#58;//linux&#46;about&#46;com/library/cmd/blcmdl1_make&#46;htm](make)[/quote:105q43g7]

The second. <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> The standard &quot;make&quot; command, straight on your terminal. It runs the Makefile which will automagically build the project. If this doesn't work, then I'd like to know about it because it &quot;should&quot; just build straight from the makefile. (Assuming to apt-get all the dependencies listed in the HACKING file)

The only exception is the Gtk client, which requires pkg-config. You'll have to give me a little bit to find out how to properly invoke the correct pkg-config incantation that will make it build.

--------------------------------------------------------------------------------

Posted by **nak** on Tue January 31st, 2012 12:52:40 AM

[quote=&quot;AltF4&quot;:zwcjuw6i]The only exception is the Gtk client, which requires pkg-config. You'll have to give me a little bit to find out how to properly invoke the correct pkg-config incantation that will make it build.[/quote:zwcjuw6i]

Don't worry about it, just making sure that's what you meant before I attempted anything <!-- s:o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":o" title="Surprised" /><!-- s:o --> &lt;3

--------------------------------------------------------------------------------

Posted by **nak** on Wed February 1st, 2012 01:15:35 AM

love the ability to search for files in arch packages:
try to make

&gt;../src/Job.cpp:11:41: fatal error: boost/property_tree/ptree.hpp: No such file or directory
&gt;$ pkgfile ptree.hpp
&gt;extra/boost

install boost
make... repeat

--------------------------------------------------------------------------------

Posted by **nak** on Wed February 1st, 2012 02:01:31 AM

ok well shucks:
[code:1g07pr0d]/usr/include/glib-2&#46;0/glib/gtypes&#46;h&#58;34&#58;24&#58; fatal error&#58; glibconfig&#46;h&#58; No such file or directory
compilation terminated&#46;
make&#58; *** &#91;src/RTT_Client_GTK&#46;o&#93; Error 1
&#91;nak@arch Debug&#93;$ make CFLAGS=`pkg-config glib-2&#46;0 --cflags`
[/code:1g07pr0d]

I'm trying to do something like that because, glib-2.0 is hiding in:

[nak@arch Debug]$ locate glibconfig.h
/usr/lib/glib-2.0/include/glibconfig.h

I just need to figure out how to pass the cflags to the g++ or whatever I don't know, I'm going to bed lol

EDIT:
Ok, might as well post this: <http&#58;//stackoverflow&#46;com/questions/1146010/why-cant-i-build-a-hello-world-for-glib>

It's the issue I'm having -- but I don't know how to implement the solution with make

EDIT2:
Aight started hacking away at this again and found the file that needed editing:
&gt;&gt; debug/src/subdir.mk
Contains the g++ command, just had to stick -I/usr/lib/glib-2.0/include/ in front of g++

EDIT3:
Success!
[http://www.zimagez&#46;com/zimage/screenshot-020212-012602&#46;php:1g07pr0d][img](http&#58;//www&#46;zimagez.com/miniature/screenshot-020212-012602&#46;php[/img:1g07pr0d])

EDIT4:
Ok so I've got a couple clients running and the server, and I can't start a match <!-- s:( --><img src="{SMILIES_PATH}/icon_e_sad.gif" alt=":(" title="Sad" /><!-- s:( -->
Also, I found out arch linux doesn't have anyone keeping a sparsehash-1.10 package -- so, you may have introduced me to yet another educational experience <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P --> (perhaps maintaining an arch package)

The client authenticates no matter wat at the moment (even with blank name/pass), uhhhh dunno what else to say. I haven't checked out the source code.  GTK seems pretty cool, I should prolly learn that. I was hoping to see some 3D diddles tonight D: I'll wait till whenever I suppose.

kbye

--------------------------------------------------------------------------------

Posted by **nak** on Thu February 2nd, 2012 10:18:15 AM

I decided to do a new post for debugging runtime.
What is the directory structure of all the compiled components? I had to go into debug of each dir. and compile each one. Now I've put the .so from Common in /usr/lib 

When I got up this morning I suspected that the GTK client wasn't able to access the ogre_3d binary -- I guess I'll try stuffing them all into one directory and see how that goes.

EDIT 1:
K, looked at sauce:
//TODO: Start the game!!!

okay [img:169svxa1]http&#58;//i2&#46;kym-cdn&#46;com/entries/icons/original/000/003/617/okayguy&#46;jpg[/img:169svxa1]

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu February 2nd, 2012 06:08:16 PM

Wow, thanks for all the effort Nak! Let's see...

The Client_Core is a shared object file for which Client_GTK is just a front end. All the meat of what the client does happens in Client_Core, and then Client_GTK just acts as a GUI for it. So you can make any kind of front end you want! GTK, Qt, terminal, ascii art, whatever. 

The Client_Core shared object needs to be findable by the GTK application though. So you need to either:
A) Add the directory where libRTT_Client_Core.so is at into yout LD path.
(In Debian, you just add the full path to the end of /etc/ld.so.conf Then run sudo ldconfig)

B) Copy the libRTT_Client_Core.so into /usr/lib/
Though with this method you have to re-copy over the binary any time you make a change to it.

Also, yea, the game itself isn't yet quite hooked up into the game server. I'm hoping to do that within this week actually. The API is already defined for moving units around the gameboard remotely, I have to fill in the functionality.

And there is no real authentication on the server yet, except that you have to use a name not already in use. I do have password hashing code actually, but the GTK client just isn't using it. (It does need salt, too. That's issue #4<https&#58;//github&#46;com/altf4/RealTimeTactics/issues/4>) There needs to be a persistent file of valid usernames that the server can read from to authenticate for.

pkg-config needs both glib-2.0 and gtkmm-3.0 fed into it

What exact error do you get when you try to make a match?

--------------------------------------------------------------------------------

Posted by **nak** on Fri February 3rd, 2012 12:32:56 AM

I don't get any error, just nothing happened
Looking forward to the meeting tomorrow
