## Holes in phx2600
Posted by **hexatex** on Wed August 5th, 2009 11:00:48 AM

php.ini file is in the web root. I dont know if this is a current one but a strange find heh
phx2600.org/php.ini

and the version of wordpress on another site you run is outdated, I see you updated this site from 2.8.2 to 2.8.3
<!-- m --><a class="postlink" href="http://phx2600.org/readme.html">http://phx2600.org/readme.html</a><!-- m -->
but this site is behind
<!-- m --><a class="postlink" href="http://www.web-geek.net/readme.html">http://www.web-geek.net/readme.html</a><!-- m -->

I dont know much specific information about the security upgrade in this new package but I do know it has to do with privilege escalation

Oh and I'm sure this last one is a problem with phpbb and not your fault, but the login allows for user enumeration
if I type in 
user: hexatex
pass: fakepass

it tells me that my password is wrong. All failed login attempts should have identical errors.

actually then again the forum is public so I suppose the attacker could just browse the forum for user names. Are the usernames and display names always the same here? i dont remember. 

any how, thought you should know about these issues. I have another possible exploit but I wanna develop it more before i release it <!-- s;-) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";-)" title="Wink" /><!-- s;-) -->
Maby I'll show it at the next 2600 meeting.

Peace  <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Wed August 5th, 2009 06:36:55 PM

Thanks for the info, some of these issues have already been fixed and I'll be sure to look into the other issues when I have time.
