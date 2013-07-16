## Where'd ghostshell go?
Posted by **nak** on Wed November 12th, 2008 06:34:54 PM

I know, the shell has transcended... to SCRIPT

Need's a little work, but you get the idea  <!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) --> 

[code:24p2zv8a]#! /usr/bin/env/python

import time, random, feedparser, re, urllib
from scrape import *

feed = &#91;'http&#58;//feeds&#46;technorati&#46;com/frontpage/index&#46;xml',
        'http&#58;//feeds&#46;computerworld&#46;com/Computerworld/Cybercrime/News&#46;xml',
        'http&#58;//feeds&#46;feedburner&#46;com/linuxhaxor/zvzl&#46;xml',
        'http&#58;//search&#46;techrepublic&#46;com&#46;com/search/xml&#46;html?t=0&amp;s=0&amp;o=1&amp;mode=rss',
        'http&#58;//blog&#46;washingtonpost&#46;com/securityfix/index&#46;xml',
        'http&#58;//feedproxy&#46;google&#46;com/linuxtoday/linux&#46;xml'&#93;

rand = random&#46;randint(0,5)
d = feedparser&#46;parse(feed&#91;rand&#93;)

for i in range(0,10)&#58;
    worthy = 0
    
    title = d&#46;feed&#46;title
    e = d&#46;entries&#91;i&#93;
    entry = d&#46;entries&#91;i&#93;&#46;title
    entry_low = entry&#46;lower()
    entry_split = entry_low&#46;split(' ') 
    string_list=&#91;     'hack',
                      'hacker',
                      'hackers',
                      'hacker\'s',
                      'hacking',
                      'virus',
                      'worm',
                      'malfunction',
                      'linux',
                      'unix',
                      'defcon',
                      'malware',
                      'engineering',
                      'conspiracy',
                      'network',
                      'tweak',
                      'bug',
                      'crack',
                      'lock',
                      'password',
                      'phish',
                      'phishing',
                      'scam',
                      'scams',
                      'internet',
                      'encryption',
                      'encrypt',
                      'spam',
                      'firewall',
                      'spy',
                      'spying',
                      'flaw',
                      'flaws',
                      'security',
                      'developers',
                      'wi-fi',
                      'banned',
                      'dns',
                      'holes',
                      'cybercrime',
                      'attack',
                      'cookie'&#93;
    for j in string_list&#58;
        if j in entry_split&#58;
            worthy = 1
    if worthy &gt; 0&#58;
        login_url = 'http&#58;//phx2600&#46;org/forum2/ucp&#46;php?mode=login'
        params1 = urllib&#46;urlencode({'username'&#58; 'SECRET', 'password'&#58; 'PASSWORD', 'login'&#58; 'Login'})
        s&#46;go(login_url, params1)
        time&#46;sleep(5)

        link = e&#46;link
        subject = entry + '&#91;' + title + '&#93;'
        message = '&#91;url=' + link + '&#93;' + entry + '&#91;/url&#93;'

        post_url = 'http&#58;//www&#46;phx2600&#46;org/forum2/posting&#46;php?mode=post&amp;f=27'
        
        s&#46;go(post_url)
        d = s&#46;doc
        content = d&#46;content

        token_re = re&#46;search ('name=\&quot;form_token\&quot; value=\&quot;\w{40}', content)
        token1 = token_re&#46;group(0)
        token2 = token1&#46;split('\&quot;')
        token = token2&#91;3&#93;&#46;strip('\u2019')
        
        lastclick_re = re&#46;search ('lastclick\&quot; value=\&quot;\w{10}', content)
        lastclick1 = lastclick_re&#46;group(0)
        lastclick = lastclick1&#46;split('\&quot;')

        creation_re = re&#46;search ('creation_time\&quot; value=\&quot;\w{10}', content)
        creation1 = creation_re&#46;group(0)
        creation = creation1&#46;split('\&quot;')

        sid_re = re&#46;search ('sid=\w{32}', content)
        sid1 = sid_re&#46;group(0)
        sid = sid1&#46;split('=')

        create_int = int(creation&#91;2&#93;)
        creation_time = create_int + 1

        print &quot;POSTING&#58; &quot; + subject&#91;&#58;60&#93; + &quot;\nWaiting 30 seconds&#46;&#46;&#46;\n\n*DEBUG*&quot;
        print &quot;token&#58; &quot; + token + &quot;\nmake_time&#58; &quot; + creation&#91;2&#93;
        print &quot;last_click&#58; &quot; + lastclick&#91;2&#93;
        print &quot;sid&#58; &quot; + sid&#91;1&#93;

        time&#46;sleep(5)
        post_url2 = 'http&#58;//www&#46;phx2600&#46;org/forum2/posting&#46;php?mode=post&amp;f=27&amp;sid=' + sid&#91;1&#93;
        params2 = urllib&#46;urlencode({'subject'&#58; subject&#91;&#58;50&#93;,
                                    'message'&#58; message,
                                    'lastclick'&#58; lastclick&#91;2&#93;,
                                    'post'&#58; 'Submit',
                                    'creation_time'&#58; creation&#91;2&#93;,
                                    'form_token'&#58; token})

        s&#46;go(post_url2, params2, redirects=10)

        d = s&#46;doc
        content = d&#46;content
        content2 = content&#46;encode('utf-8')
        htmlfile = open('response&#46;html', 'w')
        htmlfile&#46;write(content2)
        htmlfile&#46;close()
        
        worthy = 0
        time&#46;sleep(30)
        
    else&#58;
        print &quot;\nNOT POSTING&#58; &quot; + entry + &quot;\n\n&quot;
[/code:24p2zv8a]
