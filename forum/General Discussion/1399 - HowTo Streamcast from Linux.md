## HowTo: Streamcast from Linux
Posted by **AltF4** on Fri May 6th, 2011 08:02:45 PM

Have you ever wanted to do some live streaming to the interwebs? Have you ever wanted to do it using all Free Software? And without any really powerful hardware? I have, and it turned out to be quite an ordeal getting it all to work. But never fear! I will lead you through it. 

Things we want:

1) Video and Audio Streaming to Justin.tv
2) Stream from any source (external device, the entire desktop, etc...)
3) Talk over the video stream from a USB headset
4) Overlay a custom image on top of the video stream (Desktop)
5) All Free Software! (except justin.tv itself, I guess)

This guide was written for Ubuntu 10.04. But I don't see why any other Linux distro wouldn't work. 

1) Turns out there is an excellent tool for streaming from VLC to Justin.tv: jtvlc. <!-- m --><a class="postlink" href="http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API">http://apiwiki.justin.tv/mediawiki/inde ... asting_API</a><!-- m --> Go ahead and download that. 

2) Now make an account on Justin.tv. In particular, you're going to need the &quot;streaming key&quot; that it gives you. We'll use it in just a sec.

3) Get VLC to capture what you want, and stream it out to an SDP file over RTP. In my case, I'm going to stream from a Dazzle video capture device. It's recognized by 4vl as /dev/video1. The command looks like:

[code:11x81kcr]vlc v4l2&#58;///dev/video1 &#58;input-slave=alsa&#58;// -vvv input_stream --sout='#duplicate{dst=&quot;transcode{deinterlace,venc=x264{keyint=60,idrint=2},vcodec=h264,vb=600,acodec=mp4a,ab=48,channels=2,samplerate=22050}&#58;rtp{dst=127&#46;0&#46;0&#46;1,port=1234,sdp=file&#58;///home/altf4/vlc&#46;sdp}&quot;}'[/code:11x81kcr]

Obviously, replace &quot;AltF4&quot; with your username.

You may want to adjust the video and audio bitrates. They are the &quot;vb=&quot; and &quot;ab=&quot; options within. 

If you want to stream the entire desktop, you use ://screen instead of :///dev/video1

4) Redirect audio. This was a tricky one. You see, the above VLC command assumes that all of the audio is coming from the default ALSA input. Which is fine, but that means we have to redirect all the audio we need to that. 

First is the game sounds from my Dazzle:

[code:11x81kcr]pacat -r --latency-msec=1 -d alsa_input&#46;usb-Pinnacle_Systems_GmbH_DVC100-01-DVC100&#46;analog-stereo | pacat -p --latency-msec=1 -d alsa_output&#46;pci-0000_00_1b&#46;0&#46;analog-stereo[/code:11x81kcr]

Next, I redirect the input from my USB headset micorphone:

[code:11x81kcr]pacat -r --latency-msec=1 -d alsa_input&#46;usb-Logitech_Logitech_USB_Headset-00-Headset&#46;analog-mono | pacat -p --latency-msec=1 -d alsa_output&#46;pci-0000_00_1b&#46;0&#46;analog-stereo[/code:11x81kcr]

But! This only redirects these two [b:11x81kcr]inputs[/b:11x81kcr] to the alsa [b:11x81kcr]output[/b:11x81kcr]. How do we then pipe the alsa output to alsa input?

With one of these!
[img:11x81kcr]http&#58;//www&#46;topchinashop&#46;com/images/AUD-014&#46;jpg[/img:11x81kcr]

Plug one end into your PC's speaker out, and the other end into the Microphone-in! 

lawl

5) Stream to Justin.tv using jtvlc. 

[code:11x81kcr]&#46;/jtvlc throw_away $YOUR_STREAM_KEY_HERE /home/altf4/vlc&#46;sdp -d[/code:11x81kcr]

Obviously, replace &quot;AltF4&quot; with your username.

6) Image overlay. (For awesome logos and stuff like that)

I made a custom program in c and gtk. Here's the source:
<!-- m --><a class="postlink" href="http://pastebin.com/tLyV6f9A">http://pastebin.com/tLyV6f9A</a><!-- m -->
Binary attached. Give the program the path of your image as an argument.

Yet to come:
- Scriptify the whole thing for ease of use.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Sun May 8th, 2011 07:47:57 PM

save'd

--------------------------------------------------------------------------------

Posted by **AltF4** on Thu May 12th, 2011 08:10:54 PM

As a live test of the streaming system, some friends and I will be doing a marathon stream on Saturday of Final Fantasy 7! It's a 12 hour real-time run. Also, we're going to be doing all of this for charity. We'll be soliciting donations to Child's Play. It's a good cause.

Come and hang out with us while we BS and play one of our favorite old games.

11AM Saturday May 14th - (hopefully) 11PM 

<!-- m --><a class="postlink" href="http://www.justin.tv/altf4_streaming">http://www.justin.tv/altf4_streaming</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri May 13th, 2011 11:42:56 AM

I'll be watchin.
