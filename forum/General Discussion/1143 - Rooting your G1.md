## Rooting your G1
Posted by **HalfSight** on Fri October 30th, 2009 01:00:04 PM

Updated to number the steps.

<!-- m --><a class="postlink" href="http://nerdanalysis.blogspot.com/">http://nerdanalysis.blogspot.com/</a><!-- m -->

So I have been all over the internet gathering info on rooting my G1. Androidspin.com, Androidandme.com and mostly XDA Forums. I have found several guides and now I use a mix of those guides to root peoples phones. This is the least complicated method I can bring to the table. So I hope this helps a lot of people.

So there is a hole in the bluetooth programming in Android 1.5, I guess, that lets you take root control. That is what they are exploiting. That is beyond my knowledge. So most phones you come across are going to be on stock Android 1.6. This is where you run into a problem. Someone came out with a 1 click root app, but it does not work on Android 1.6. so you must downgrade.

Downgrading for the G1:

Downgrading for the G1 is simple. Just get the DREAIMG.NBH file. You can get this here: &quot;http://code.google.com/p/android-roms/downloads/list&quot;. It will download a file called DREAIMG-RC29.zip. Unzip this with Winrar or 7zip or winzip or whatever fits your fancy. You will have a file called DREAIMG.NBH. 

Now that we have that down. You want put the DREAIMG.IMG file on the root of your SD.
Backup any info on your SD card that you want to save.

1. Press Menu&gt;Settings.Select SD card and phone storage
2. Select SD card &amp; phone storage
3. Unmount SD card
4. Format SD Card (YOU MUST FORMAT THIS FROM YOUR PHONE).
5. Connect the phone to your computer. 
6. Pull down Notifications ans choose &quot;Select to copy files to/from your computer&quot;
7. Select Mount.
8. Now copy the DREAIMG.NBH file to the ROOT of your SD card! Do not put it in a folder!
9. Now power off your phone.
10. Now power your phone on by holding the Camera and Power buttons down as it powers on.
(Assuming the previous steps were done correctly you will see a rainbow screen and then it will cut to a blue screen.) 
11. Press the power button to start the update. Which is actually a downgrade to Android v1.5 RC29.
12. This will take a moment. when it is finished it will ask you to press the action button to finish. 
13. The TrackBall is the action button. This may take you back to the Rainbow screen. If this happens, press the Call+Menu+Power to force a reboot.
14. Assuming you did this correctly you will boot into an earlier version of android.

Ok so that we have downgraded the G1, we get to the easy part.
Files/Apps you will need for the G1:

Linda File Manager (On the market)
&quot;http://zenthought.org/system/files/asset/2/flashrec-1.1.2-20090909.apk&quot; -- Recovery Flasher
&quot;http://developer.htc.com/adp.html#s3&quot; -- HTC Android Image (signed-dream_devphone_userdebug-ota-14721.zip)
&quot;http://n0rp.chemlab.org/android/experimental/update-cm-4.1.9999-signed.zip&quot; -- CyanogenMOD 4.1.9999

1. Go to the market and make sure you have the Linda File Manager installed on your phone.
2. Now you want to get the FLASHREC app &quot;http://zenthought.org/system/files/asset/2/flashrec-1.1.2-20090909.apk&quot;. You can navigate to this from you linda file manager and install it.
3. So now you want to make sure you are hooked to wifi to avoid corrupting the recovery image. 
4. Open the Recovery Flasher. Select &quot;Backup to flash Cyanogens Recovery 1.4&quot;
5. Now select Flash Cyanogen Recovery.
6. Now feel free to verify that this flashed correctly. Power off your phone and boot into the recovery screen by holding down &quot;home button&quot; during power up. This should take you to a screen with a black background and green letters. Now go a head an choose the top selection and reboot the phone.
7. Copy the HTC Android Image and the CyanogenMOD rom to the root of your SD card. (DO NOT PUT THESE IN A FOLDER)
8. Now reboot your phone into the recovery screen by holding down &quot;home button&quot; during power up.
9. OK, now that we are in the recovery menu you want to choose &quot;apply any zip from sd&quot;.
Now pick the signed-dream_devphone_userdebug-ota-14721.zip. Press the home button to apply.
10. This will finish and when you reboot it will take you into a stock &quot;Open Box&quot; screen. 
Don't Panic! Watch it till it reboots again and hold down the &quot;home button&quot; to get back into the recovery menu. Seeing a trend with the &quot;home button&quot; yet?
11. Choose the &quot;apply any zip from sd&quot; option again and choose the cyanogenmod rom. Press the &quot;home button&quot; to continue.
12. Once this has finished reboot your phone, if all went well you will be booting into Cyanogens Custom Android OS. 
13. But wait!! There's more!!! Make sure to reboot twice more. This is to make the HTC rom and the Cyanogen rom mix together, like soup.

Ok, now we are done, you have root access to your phone. YEA!!!

Special thanks to Cyanogen, XDA Forums and their developers, Androidspin.com, Androidandme.com, theunlockr.com.

--------------------------------------------------------------------------------

Posted by **Rax** on Wed November 4th, 2009 11:18:49 AM

Cool. Thanks for the post! <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

There's some great info at [url=http&#58;//theunlockr&#46;com/2009/08/22/how-to-root-the-mytouch-3g-or-g1-in-one-click/:1p92u1bg]TheUnlockr.com[/url:1p92u1bg].  The recovery image they suggest (Amon Ra's Recovery Image) rocks!  You can even mount the SD card on your computer when in Recovery mode, so you can copy files to the phone, and then unmount it an continue the install.  <!-- s:mrgreen: --><img src="{SMILIES_PATH}/icon_mrgreen.gif" alt=":mrgreen:" title="Mr. Green" /><!-- s:mrgreen: -->

--------------------------------------------------------------------------------

Posted by **HalfSight** on Fri November 6th, 2009 09:04:07 AM

[quote=&quot;Rax&quot;:lc5wg5ek]Cool. Thanks for the post! <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

There's some great info at [url=http&#58;//theunlockr&#46;com/2009/08/22/how-to-root-the-mytouch-3g-or-g1-in-one-click/:lc5wg5ek]TheUnlockr.com[/url:lc5wg5ek].  The recovery image they suggest (Amon Ra's Recovery Image) rocks!  You can even mount the SD card on your computer when in Recovery mode, so you can copy files to the phone, and then unmount it an continue the install.  <!-- s:mrgreen: --><img src="{SMILIES_PATH}/icon_mrgreen.gif" alt=":mrgreen:" title="Mr. Green" /><!-- s:mrgreen: -->[/quote:lc5wg5ek]

I know, after I noticed all that, I switched my recovery image to Aman-Ra. You can even partition FAT32+ext2+swap straight from Aman-Ra with the touch of a button. the unlockr is in my special thanks list, their the ones I found out about Aman-Ra from. They have great guides. My guide is just a mix of a few different guides.
