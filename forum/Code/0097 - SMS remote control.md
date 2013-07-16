## SMS remote control
Posted by **Automated Penguin** on Wed April 16th, 2008 03:33:54 PM

I was looking at NAK's auto SMS sender and thought &quot;hey why not do it in reverse?&quot;  so with this script, a fresh pop email account and an account at <!-- m --><a class="postlink" href="http://www.kwiry.com/">http://www.kwiry.com/</a><!-- m --> you can control your machine via SMS.

heres how it works... you send an SMS message to kwiry (59479) after you have setup an accnt, kwiry sends the SMS to an email account you designate as the subject line in the email  like &quot;Subject: Your Kwiry - [YOUR SMS HERE]&quot;, this script periodically checks the pop email accnt to see if it contains any mail, if it does then it strips out the subject line and parses your SMS using whatever code you put in.

For example if I send the sms &quot;Echo testing!&quot; I get this result:

[code:ubz98l9g]
Recieving 1 message(s)&#46;

Recieved command&#58; Echo

testing!
[/code:ubz98l9g]

anyway heres the script, its not perfect but it has some potential.

[code:ubz98l9g]

import telnetlib, sys, os, time, string

def Get_Mail_Cmd()&#58;
    HOST = &quot;pop&#46;west&#46;cox&#46;net&quot;               #your pop server here
    PORT = &quot;110&quot;
    USER = &quot;username&quot;
    PASS = &quot;password&quot;
    
    telnet = telnetlib&#46;Telnet(HOST, PORT)
    telnet&#46;read_until(&quot;POP3 server ready&quot;)  #may need to change this depending on the server
    time&#46;sleep(&#46;2)
    telnet&#46;write(&quot;user &quot; + USER + &quot;\n&quot;)     # submit user 
    time&#46;sleep(&#46;2)
    telnet&#46;write(&quot;pass &quot; + PASS + &quot;\n&quot;)     # submit pass
    time&#46;sleep(&#46;2)
    telnet&#46;read_very_eager()                #read to empty the buffer
    telnet&#46;write(&quot;list&quot; + &quot;\n&quot;)             #get a list of emails on the server
    time&#46;sleep(&#46;2)
    
    msgs=  telnet&#46;read_very_eager() #read the stuff we want to
    msgs=msgs&#46;split(&quot; &quot;)            #split out the data we need (number of emails waiting to be parsed)

    print &quot;Recieving &quot; + msgs&#91;1&#93; + &quot; message(s)&#46;&quot; + &quot;\n&quot;

    
    if msgs&#91;1&#93; !=&quot;0&quot;&#58;                   #if theres a message do stuff
        telnet&#46;write(&quot;retr 1&quot; + &quot;\n&quot;)
        time&#46;sleep(&#46;4)
        msgs= telnet&#46;read_very_eager()  #parse the email looking for the subject 
        msgs=msgs&#46;split()

        for x in range(1, len(msgs))&#58;
                                        #Index goes like           1    2     3 4       5    6    &#46;&#46;&#46;
                                        #Format goes like Subject&#58; your kwiry - command arg0 arg1 etc&#46;
            
            if  msgs&#91;x&#93; == 'Subject&#58;'&#58;
                if msgs&#91;x+2&#93; == &quot;kwiry&quot;&#58;
                    command= msgs&#91;x+4&#93;  #found a subject
                    arg0= msgs&#91;x+5&#93;     #use arguments?? etc&#46;&#46;
                    print &quot;Recieved command&#58; &quot; + command + &quot;\n&quot;
                    telnet&#46;write(&quot;dele 1&quot; + &quot;\n&quot;)           #got the subject, delete that message
                    time&#46;sleep(&#46;2)
                    telnet&#46;read_very_eager()                #wont delete without this ??
                    Execute_Commands(command, arg0)
                    telnet&#46;write(&quot;quit&quot; + &quot;\n&quot;)             #got what we need, kill our session      
        

    
                
                
def Execute_Commands(command, arg0)&#58; #put whatever commands you want here&#46;&#46;&#46;

    if command== &quot;Shutdown&quot;&#58;
        os&#46;system('shutdown -i -t 30 -c &quot;remote shutdown&quot;')
        
    if command== &quot;Echo&quot;&#58;
        print arg0
        


if __name__ == &quot;__main__&quot;&#58;

    while 1&#58;
        
        Get_Mail_Cmd()
        time&#46;sleep(300) # check for commands every X seconds&#46;



[/code:ubz98l9g]

--------------------------------------------------------------------------------

Posted by **nak** on Fri April 18th, 2008 12:43:08 AM

Cool, so I can start my computer's hard drive erasing as I'm being arrested! Good idea!

--------------------------------------------------------------------------------

Posted by **Valveritas** on Fri April 18th, 2008 06:44:46 AM

Wow, excellent idea.  This is really starting to motivate me to learn Python.  There's all sorts of instances where I could use such scripts to do some automation.

--------------------------------------------------------------------------------

Posted by **phigan** on Sun June 1st, 2008 08:13:24 AM

Good stuff indeed. I'd just bypass the Kwiry deal, because you can send email from phones pretty easily. You can send email via SMS, an actual email client, or using the GMail app. Just set up a contact for it or something.
