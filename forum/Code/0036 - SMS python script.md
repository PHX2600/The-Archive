## SMS python script
Posted by **nak** on Sun January 27th, 2008 12:02:34 AM

I wrote this a little while back when my friend wanted to know when there was a blog posted for a contest, so I hacked this script up for him:

[code:h8nil0kr]
#Imports regular expressions, http stuff and time modules
import re, httplib, urllib, time

#makes HTTP object
conn = httplib&#46;HTTPConnection(&quot;kotaku&#46;com&quot;)

conn&#46;request(&quot;GET&quot;, &quot;/index&#46;php&quot;) #the page to get
resp = conn&#46;getresponse() #get it
data = resp&#46;read() #put the data in a variable
myRegExp = re&#46;compile('&lt;a href=&quot;http&#58;//kotaku&#46;com/gaming/contest/&#46;*&lt;/a&gt;') #sets up regular expression, it's worth it to become familiar with RegEx!!!
link = myRegExp&#46;findall(data) #finds the patterns that match myRegExp in the data, stores in array 'link'
topPost = &quot;&lt;a href=\&quot;http&#58;//kotaku&#46;com/gaming/contest/these-thirty-finalists-will-fight-for-500-328895&#46;php\&quot;&gt;These Thirty Finalists Will Fight for $500!&lt;/a&gt;&quot; #The &quot;top post&quot; of the blog that matches the RE at the time of writing
while 1 == 1&#58; #infinite loop!
    while link&#91;0&#93; == topPost&#58; #Checks to see if the top blog post that matches the RE has changed&#46;&#46;&#46;
        print &quot;Hasn't changed&#46; Waiting 10 Seconds&#46;\n&quot;
        time&#46;sleep(10)
    
    print &quot;New contest post!! &quot; + link&#91;0&#93; + &quot;\nSending text message&#46;&#46;&#46;\n&quot;
    topPost = link&#91;0&#93; #stores new 'top post'
    params = urllib&#46;urlencode({'number'&#58; '6025359994', 'message'&#58; link&#91;0&#93; + '%21%21', 'provider'&#58;'vtext&#46;com', 'submit'&#58; 'Send+Message%21'}) #parameters for the SMS post to txtmsgpro, change the 6025359994 to your number
    headers = {&quot;Accept&quot;&#58; &quot;text/xml,application/xml,application/xhtml+xml,text/html;q=0&#46;9,text/plain;q=0&#46;8,image/png,*_/*;q=0&#46;5&quot;,
               &quot;Cookie&quot;&#58; &quot;__qca=45bda1f2-c4f2c-57894-feac3; __qcb=1789952817&quot;,
               &quot;Content-type&quot;&#58; &quot;application/x-www-form-urlencoded&quot;} #headers!
    conn = httplib&#46;HTTPConnection(&quot;www&#46;textmessagepro&#46;com&quot;) # http object again
    conn&#46;request(&quot;POST&quot;, &quot;/&quot;, params, headers) #post that info!
    print &quot;Text Sent!\n&quot;
[/code:h8nil0kr]

Maybe this will be of use!
*edit for having 'a' in the first sentence where it shouldn't have been, and to comment code*

--------------------------------------------------------------------------------

Posted by **Valveritas** on Thu January 31st, 2008 01:49:26 PM

Does this run offline or do you embed it somewhere?  I don't know anything about python scripts, but I've often been interested in a program that did something like this for sites that have no way of telling you when they're updated.  

Anyway, I'd like to try it once I figure out how.   <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) -->

--------------------------------------------------------------------------------

Posted by **nak** on Thu January 31st, 2008 02:38:07 PM

It runs on your desktop computer, I was in windows XP when I wrote it, but any computer with the python interpretor should run it.

I commented the code, hopefully it makes a little more sense! If you want I could try and modify it for a particular site, whatever you had in mind, goatse.cx? ;D jk &lt;3 Sorry about that!

--------------------------------------------------------------------------------

Posted by **Valveritas** on Thu January 31st, 2008 03:54:39 PM

Well, not having Python I downloaded Python 2.5.1 for Windows, and started my crash course adventure.

I tried running it as is, and got this output:

[quote:1p39zevc]
Traceback (most recent call last):
  File &quot;J:\+_DOWNLOAD_+\Pyhton_nak.py&quot;, line 14, in &lt;module&gt;
    while link[0] == topPost: #Checks to see if the top blog post that matches the RE has changed...
IndexError: list index out of range
[/quote:1p39zevc]

Hmm.

--------------------------------------------------------------------------------

Posted by **nak** on Thu January 31st, 2008 07:13:20 PM

The contest was a while back so there aren't any 'contest' tagged blog posts at the moment!
...but if we changed:

[code:12gq0d7c]myRegExp = re&#46;compile('&lt;a href=&quot;http&#58;//kotaku&#46;com/gaming/contest/&#46;*&lt;/a&gt;')[/code:12gq0d7c]

to

[code:12gq0d7c]myRegExp = re&#46;compile('&lt;a href=&quot;http&#58;//kotaku&#46;com/&#46;*&lt;/a&gt;')[/code:12gq0d7c]

it should work, but it will send a text message because the original contest post isnt there anymore, then it wont send anything until another update happens if you leave the script running.

Hopefully that made sense,  <!-- s:mrgreen: --><img src="{SMILIES_PATH}/icon_mrgreen.gif" alt=":mrgreen:" title="Mr. Green" /><!-- s:mrgreen: -->

--------------------------------------------------------------------------------

Posted by **Valveritas** on Thu January 31st, 2008 08:18:53 PM

Running now. That seems to work.  However, no SMS message was sent with the script. Works directly from textmessagepro.com though.  Provider/carrier problem?  I don't see where to edit that in the script, correctly.

Here's what I'd like to do, I'd like to check this [url=http&#58;//vinfis&#46;100webspace&#46;net/phpBB2/index&#46;php:29p76i6f]forum[/url:29p76i6f] for a change in the number of total posts and then send an email to me instead of an SMS message.  Basically, anything above 858 (which is what it's at now).  Remember that PHP script you modded that's suppose to send an email when there's a new message? Well, I never got around to telling you, but it stopped working after the first run.  I tried to fix it, but no luck.  So, back to this script... uh, I'm not sure your script would work as is for what I'd like to do with it.  I can think of other uses, but this is just one use that comes to mind right now.

I'll play around with it, but I don't know what I'm doing. Heh.  I guess it'll probably require a little more than just changing the text here and there.  

If this is too much time and effort don't worry about it.

p.s. It bugs me that there is no horizontal scroll bar for the Python editor.  All the text off screen was very hard to read.

--------------------------------------------------------------------------------

Posted by **phigan** on Fri February 1st, 2008 11:01:28 AM

[code:3fqi7zl3]params = urllib&#46;urlencode({'number'&#58; '##########', 'message'&#58; link&#91;0&#93; + '%21%21', 'provider'&#58;'vtext&#46;com', 'submit'&#58; 'Send+Message%21'}) #parameters for the SMS post to txtmsgpro, change the ########## to your number[/code:3fqi7zl3]

Well, notice the provider part.. Are you using Verizon? If so, vtext.com should work. Otherwise, you might need other info.

p.s. If that editor sucks, use a different one like EditPlus or TextPad. You can probably find Python syntax highlighting and code completion plugins for both of those.

--------------------------------------------------------------------------------

Posted by **nak** on Fri February 1st, 2008 12:03:26 PM

I couldn't get autodetect to work... so just put the domain name that matches your service provider!

message.alltel.com = Alltel
paging.ascwireless.com = Ameritech
bellsouth.cl = Bellsouth
myboostmobile.com = Boost
csouth1.com = Cellular South
mobile.celloneusa.com = CellularOne
mobile.mycingular.com = Cingular
mmode.com = Cingular Blue (AT &amp; T)
sms.edgewireless.com = Edge Wireless
mymetropcs.com = Metro PCS
messaging.nextel.com = Nextel
sms.pscel.com = PSC Wireless
pager.qualcomm.com = Qualcomm
qwestmp.com = Qwest
messaging.sprintpcs.com = Sprint PCS
tmomail.net = T-Mobile
vtext.com = Verizon
vmobl.com = Virgin Mobile

--------------------------------------------------------------------------------

Posted by **Valveritas** on Fri February 1st, 2008 01:31:13 PM

Thanks for the list.  I'm using T-mobile, so I changed the domain to that.  It worked, and that's in spite of my incompetence getting in the way.  Wow!  There was no message, and some attached picture that couldn't be viewed.  I don't usually get SMS messages, so hmm.  Well, at least I learned a few things.

--------------------------------------------------------------------------------

Posted by **oz1980** on Sat February 2nd, 2008 11:03:51 AM

you could make it more useful by adding a site, number, and provider prompts. 

site = input(&quot;Which site would you like to watch: &quot;)
Phone_number = input(&quot;what is your phone number: &quot;)
sms_porvider = input(&quot;what service provider do you use: &quot;)

#Then in write a sieries of if statements that will allow for a the provider to change.
if sms_provider == verison
     sms_provider = vtext.com
# and so on.

then in the previous code, you can then use the variables instead of actually putting a site into the code. User input would help to be more user friendly for those that are not hackers and get lost in code. Its been a while since I used python, so I think I wanted to use input instead of raw_input. correct me if I am wrong... Time to bust out my python book again...

--------------------------------------------------------------------------------

Posted by **oz1980** on Sat February 2nd, 2008 11:07:10 AM

sorry, indent didn't show up in the if statement, so I will use dots as a mark for the indent:

if sms_provider == verison
.....sms_provider = vtext.com

--------------------------------------------------------------------------------

Posted by **Valveritas** on Sat February 2nd, 2008 05:10:24 PM

Yeah Nak, stop slacking off and start making this thing more user friendly.  I want to see you put at least 12 hours into this before dawn.  <!-- s:lol: --><img src="{SMILIES_PATH}/icon_lol.gif" alt=":lol:" title="Laughing" /><!-- s:lol: -->

--------------------------------------------------------------------------------

Posted by **nak** on Sat February 2nd, 2008 07:46:56 PM

LOL, that's agent orange's job to make exploits point and click! The user friendly idea is a good one, but it was just a quick hack job for my friend about a month ago... he didn't win the contest unfortunately, but he got me a sweet shirt with a brain and USB ports on it (for my bday)  <!-- s:geek: --><img src="{SMILIES_PATH}/icon_e_geek.gif" alt=":geek:" title="Geek" /><!-- s:geek: -->
