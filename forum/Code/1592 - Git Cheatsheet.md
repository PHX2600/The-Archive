## Git Cheatsheet
Posted by **nak** on Sat April 7th, 2012 01:29:07 PM

I'm not very good at git, although I've been using it for 7 months now.
here are the commands I use:

The github new repo cheatsheet:
[code:2qejbpnh]Global setup&#58;
 Set up git
  git config --global user&#46;name &quot;Ur Name&quot;
  git config --global user&#46;email Ur@Email&#46;com
      
Next steps&#58;
  mkdir asdf
  cd asdf
  git init
  touch README
  git add README
  git commit -m 'first commit'
  git remote add origin git@github&#46;com&#58;naked/asdf&#46;git
  git push -u origin master
      
Existing Git Repo?
  cd existing_git_repo
  git remote add origin git@github&#46;com&#58;naked/asdf&#46;git
  git push -u origin master[/code:2qejbpnh]

Now that we have a repository set up, we add the files we want to track (git creates a hidden .git folder with all the revisions of the files we are tracking, do an ls -a to see it and check it out)

git add file1.css
git add file2.html
git add file3.js
[b:2qejbpnh]git commit -a[/b:2qejbpnh]

The -a looks for all changed tracked files (think 'all'), so after you 'add' and then update a file with a new feature 'commit' will create a restore point.

if you make some changes and have really screwed stuff up you can do:
[b:2qejbpnh]git reset --hard[/b:2qejbpnh]
this will removed all &quot;staged&quot; changes and restore your project to your last commit.

or
[b:2qejbpnh]git reset --hard bc40409[/b:2qejbpnh]
To 'roll back' or reset to a specific commit while losing all your current work.

You can see all your previous commits by doing 
[b:2qejbpnh]git log[/b:2qejbpnh]

git clone <!-- m --><a class="postlink" href="git://url">git://url</a><!-- m -->  -- To clone a repo from the latest commit

I've been using [b:2qejbpnh]git pull[/b:2qejbpnh] for the first time the last week or so, say you have a project and have a development machine and a production server, you do a:
(on the dev. machine)
git commit -a
[b:2qejbpnh]git push origin master[/b:2qejbpnh]  -- this pushes all the commits locally to the remote repo (github)

(on the production server)
[b:2qejbpnh]git pull[/b:2qejbpnh] -- will pull all the changes to the repo in order to catch up to the latest commit

There's lots more and I'm sure PHLAK could write something better. There's a ton more features (I'm sure) but these are the commands I use regularly and they get me by.  It might be a very useful to watch a 10 minute screencast that just goes over some practical git maneuvers. Just a thought <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **AltF4** on Sat April 7th, 2012 09:50:01 PM

Also:

To turn on all color options by default
[code:uv11zuo8]git config --global color&#46;ui true[/code:uv11zuo8]

Another really super handy thing is to switch to a nicer diff viewer, like meld. Got instructions from here:
<!-- m --><a class="postlink" href="http://nathanhoad.net/how-to-meld-for-git-diffs-in-ubuntu-hardy">http://nathanhoad.net/how-to-meld-for-g ... untu-hardy</a><!-- m -->

You do:

[code:uv11zuo8]sudo apt-get install meld
gedit ~/&#46;gitdiff&#46;py[/code:uv11zuo8]

Put in the following to ~/.gitdiff.py
[code:uv11zuo8]#!/usr/bin/python

import sys
import os

os&#46;system('meld &quot;%s&quot; &quot;%s&quot;' % (sys&#46;argv&#91;2&#93;, sys&#46;argv&#91;5&#93;))[/code:uv11zuo8]

Then tell git to use your python script for diffs:

[code:uv11zuo8]git config --global diff&#46;external /home/YOURNAME/diff&#46;py[/code:uv11zuo8]

To test it, make a change on some files and then run:
[code:uv11zuo8]git diff[/code:uv11zuo8]

--------------------------------------------------------------------------------

Posted by **nak** on Mon April 9th, 2012 12:03:56 PM

Very cool, I haven't even used `git diff` yet, might try the meld thing eventually.
This would be a good phx2600 wiki article  <!-- s:P --><img src="{SMILIES_PATH}/icon_razz.gif" alt=":P" title="Razz" /><!-- s:P -->

--------------------------------------------------------------------------------

Posted by **XlogicX** on Tue April 10th, 2012 12:38:04 AM

This is great, thanks guys

--------------------------------------------------------------------------------

Posted by **nak** on Fri May 25th, 2012 02:33:11 AM

[youtube:7pjyn3ue]ZDR433b0HJY[/youtube:7pjyn3ue]
about 20 minutes in it gets practical

--------------------------------------------------------------------------------

Posted by **wook** on Sun June 24th, 2012 12:16:56 AM

Nak, 
How big of a project(s) are you using GIT for?  I am wanting to utilize Git and possibly Gradle with my CI build server.  I have concerns about the learning curve , and confusion based on team and project size.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri July 6th, 2012 12:24:09 PM

[quote=&quot;wook&quot;:282n5oun]Nak, 
How big of a project(s) are you using GIT for?[/quote:282n5oun]

I can't speak for Nak, but Git was originally designed by Linus Torvalds as the source control system for the Linux kernal and has been serving that purpose extreamly well since implemented.  Basically what I'm saying is if Git is powerful enough to handle projects with the scale and complexity of the Linux kernel, it'll be able to handle anything you can throw at it.

--------------------------------------------------------------------------------

Posted by **nak** on Thu July 12th, 2012 01:00:43 PM

Hey chums!
Just got this in my inbox: [url:jiwql6df]http&#58;//www&#46;codeschool&#46;com/courses/try-git[/url:jiwql6df] I haven't tried it, but I've taken their rails for zombies course and it wasn't too bad. I figure this might help break the ice.

Also I PM'd you with infos wook <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

--------------------------------------------------------------------------------

Posted by **wook** on Thu July 12th, 2012 11:03:45 PM

Thanks Nak. I am going to give this a try. i am thinking about applying Git, Gradle, BDD, Bamboo and Cfengine or Puppet together for a Continuous Delivery pipeline at work. It should be a fun little undertaking considering how long it took to get them to use Ant, SVN and Maven instead of PVCS and unix scripts to build.
