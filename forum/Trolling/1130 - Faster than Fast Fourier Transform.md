## Faster than Fast Fourier Transform
Posted by **jargon** on Tue October 6th, 2009 07:38:56 PM

...

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue October 6th, 2009 10:41:14 PM

...

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue October 6th, 2009 11:15:34 PM

...

--------------------------------------------------------------------------------

Posted by **jargon** on Wed October 7th, 2009 08:06:15 AM

Ok, I originally nuked this thread with the traditional '...' topic and '...' post body because I posted something in haste that made me come off as a moronic douchebag... But now I paraphrased the topic to the original's intent, and now have something tangible to share:

These are Goldwave waveform manipulation tool Expression Evaluation scripts:

[code:252h2109]Freq&#58;
sin(f*2*pi*n/x)*y

Freq2Tri&#58;
asin(wave1(n)/y)/pi*2

Freq2Tri-Tri&#58;
(asin(wave1(n)/y)/pi*2-(abs(((((n)*f/x+3/4)-int((n)*f/x+3/4))*4)/2-1)*2-1))/2

Freq2Tri-Tri2&#58;
(asin(wave1(n)/y)/pi-(abs(((((n)*f/x+3/4)-int((n)*f/x+3/4))*4)/2-1)*2-1)/2)/2

Tri&#58;
abs(((((n)*f/x+3/4)-int((n)*f/x+3/4))*4)/2-1)*2-1

TwoFreq&#58;
(sin(x*2*pi*n/f)*1+sin(y*2*pi*n/f)*1)/2

TwoFreq2Tri-Tri2&#58;
(asin((asin(wave1(n)/1)/pi-(abs(((((n)*x/f+3/4)-int((n)*x/f+3/4))*4)/2-1)*2-1)/2)/2/1)/pi-(abs(((((n)*y/f+3/4)-int((n)*y/f+3/4))*4)/2-1)*2-1)/2)/2
[/code:252h2109]

&quot;TwoFreq&quot; Generates any combo of two frequencies,

&quot;TwoFreq2Tri-Tri2&quot; converts any phase-shift combination of two frequencies into a single unique frequency.

This means you can convert any 2 frequency DTMF tone into a unique single frequency waveform, this means instead of being forced to use FFT or some bullshit, you can apply the filter per sample, and then simply parse which single frequency the result is!!

This means you can use Goertzel to simply check for one frequency instead of the DTMF combination! Halving the algorithmic &quot;big o&quot; notation! 
Reference: [url:252h2109]http&#58;//www&#46;mstarlabs&#46;com/dsp/goertzel/goertzel&#46;html[/url:252h2109]

The resulting tone is a single frequency instead of two, meaning you half the big o algorithmic complexity using Goertzel. This means for two frequencies out of a known set you are in n time instead of n^2 time. (This is faster than the n log n of FFT (Fast Fourier Transform) Less big O notation algorithmic complexity. This means you can solve a DTMF tone in just a couple dozen samples This means instead of 40ms being the lower bound of tone detection, the lower bound is now a few thousandths of a second.

This defeats the Nyquist–Shannon sampling theorem, meaning the theory is goddamn wrong. This means this morning I broke two major fundamentals of DSP's My two-frequency to one-frequency simplifier, is a 1:1 simple sample input to single sample output, which is unheard of! ..and breaks what is known about DSP's
Reference: [url:252h2109]http&#58;//en&#46;wikipedia&#46;org/wiki/Digital_signal_processing[/url:252h2109]

1:1 sample filters that combine two frequencies into one frequency were prior thought to be an impossibility!
Next trick I have to pull out of my ass will be doing faster that Goetzel for testing a single frequency. Btw, the resulting single frequency is a TRIANGLE WAVEFORM, meaning YES it is POSSIBLE TO DO FASTER. ..This means the slope is damn near continuous minus the inversion every half phase

And YES, I plan to improve the Single-Frequency Triangle Waveform so that the resulting phase is consistent regardless the unique phase combination of the original signal!

Floor is open for discussion, and no, I do not have any clue what the hell I am doing, possibly ever. There is good reason that prodigies are eccentric.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 7th, 2009 09:53:09 AM

...

--------------------------------------------------------------------------------

Posted by **jargon** on Wed October 7th, 2009 07:03:02 PM

[quote=&quot;Automated Penguin&quot;:2evgqjn9]...[/quote:2evgqjn9]

Oh, Hai!

Yes the resulting waveform in the destination is a flawless isosceles triangle waveform of the average frequency only if the source signal is the two exact combined -1 to 1 amplitude averaged sine wave frequencies being tested for.
Reference: Ostrogradsky's second algorithm [url:2evgqjn9]http&#58;//en&#46;wikipedia&#46;org/wiki/Mikhail_Vasilievich_Ostrogradsky[/url:2evgqjn9] (Google doesn't really know of next to jack shit regarding Ostrogradsky's 2nd algorithm. Can you say &quot;Arizona State University Digital Archives road trip?&quot;)

This means you plug in x and y as the two frequencies and mutate a single source sample at a to create a single output sample. This defeats the Shannon-Nyquist sampling theory due to being able to average two frequencies knowing only a single sample, but this only works if the source two frequencies are in-fact the two frequency in the signal being tested.
Reference: [url:2evgqjn9]http&#58;//en&#46;wikipedia&#46;org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem[/url:2evgqjn9]

If for example the resulting waveform is not a flawless isosceles triangle wave, and is instead a curved sawtooth, but still is the correct average frequency this means the source signal is not actually the two frequencies being tested, it is actually two other frequencies with the same average frequency.

This means all you need to know is 3 samples within 180s of a full phase change of the average frequency in order to rule out it being the correct result, which means you only need to know less than twice the phase of the larger frequency, defeating the Shannon-Nyquist sampling theory.

Since this is a 1:1 sample filter, this means this even works using a variable sample rate.
Reference: [url:2evgqjn9]http&#58;//en&#46;wikipedia&#46;org/wiki/Digital_signal_processing#Time_and_space_domains[/url:2evgqjn9]

I haven't tested this yet, but &quot;Freq2Tri-Tri2&quot; could potentially simply be applied recursively one iteration per frequency to average as a 1:1 sample filter. &quot;Freq2Tri-Tri2&quot; is a single iteration, while &quot;TwoFreq2Tri-Tri2&quot; is two iterations.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed October 7th, 2009 10:49:06 PM

...

--------------------------------------------------------------------------------

Posted by **jargon** on Thu October 8th, 2009 01:19:26 AM

[quote=&quot;Automated Penguin&quot;:2d34amjc]...[/quote:2d34amjc]

Yeah, apparently I was mistaken, below is the DTMF tone for the &quot;1&quot; key, which shows graphed the two combined frequencies, below that the average frequency graphed, and below that the graph of the  &quot;TwoFreq2Tri-Tri&quot; output from the first graph as input, with the timeline below that in seconds.

[img:2d34amjc]http&#58;//retromachineshop&#46;com/dl/audio/dtmf-1-analysis&#46;png[/img:2d34amjc]

I have no idea how I got it to consistently produce a single isosceles triangle waveform unique two each combination of two frequencies. I am going to have to dig around more in my formulas used here.

This clearly shows it is possible to detect the &quot;1&quot; key from a phone in just four ten-thousandths of a second.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Fri October 9th, 2009 12:58:38 AM

If i'm not mistaken, it's the top frequency in those 3 images that is the average of the bottom 2. combining waves is as simple as averaging their values at any given time.

Say you look at the wave as being above and below the middle line of 0 voltage, and you further look at it as going up to 1 volt and down to -1 volt, and to go even further, you have a range of voltages in between. Say at a given moment of time, one wave is at .3 volts, and another is at .5 volts, the combined wave at that given moment of time would be .4 volts.

To truly show an understanding of this, if you could play a sinewave and cosine wave at the exact same time and frequency, you would hear silence, this is because the sinewave is exactly the same distance above 0 as the cosine would be below it, or vice versa.

If you have any questions, ask. I know this because of the audio driver I have written in assembly. There is no audio hardware support for the system I'm programming, so I literally wrote an engine for Pulse Code Modulation, I will post the source code soon. Relevant to this conversation though, my driver is 4-channel, which means that I had to mix channels into one, the math behind it was just averaging the samples, and it works.

--------------------------------------------------------------------------------

Posted by **jargon** on Tue October 13th, 2009 02:13:07 AM

[quote=&quot;XlogicX&quot;:rmysaiot]If i'm not mistaken, it's the top frequency in those 3 images that is the average of the bottom 2. combining waves is as simple as averaging their values at any given time.

Say you look at the wave as being above and below the middle line of 0 voltage, and you further look at it as going up to 1 volt and down to -1 volt, and to go even further, you have a range of voltages in between. Say at a given moment of time, one wave is at .3 volts, and another is at .5 volts, the combined wave at that given moment of time would be .4 volts.

To truly show an understanding of this, if you could play a sinewave and cosine wave at the exact same time and frequency, you would hear silence, this is because the sinewave is exactly the same distance above 0 as the cosine would be below it, or vice versa.

If you have any questions, ask. I know this because of the audio driver I have written in assembly. There is no audio hardware support for the system I'm programming, so I literally wrote an engine for Pulse Code Modulation, I will post the source code soon. Relevant to this conversation though, my driver is 4-channel, which means that I had to mix channels into one, the math behind it was just averaging the samples, and it works.[/quote:rmysaiot]

Thanks, but 100% of what I posted prior in this thread other than the resource references are most probably bunk due to sycnhronicity. The nearly identical resulting waveforms are generated virtually every time regardless of what the input is due to the nature of arcsin().

In-order to make up for this sheer bullshit thread, here: download this full set of 64bit double precision floating point trigonometric functions as written for GWBASIC.

[code:rmysaiot]10 GOSUB 10000
90 END
10000 REM Trigonometric Functions
10001 DIM PI#
10002 PI#=3&#46;141592653589793#
10010 REM Sine
10011 REM DEF FNSIN#(X#)=SIN#(X#)
10020 REM Cosine
10021 REM DEF FNCOS#(X#)=COS#(X#)
10030 REM Tangent
10031 REM DEF FNTAN#(X#)=TAN#(X#)
10040 REM Secant
10041 DEF FNSEC#(X#)=1/COS#(X#)
10050 REM Cosecant
10051 DEF FNCSC#(X#)=1/SIN#(X#)
10060 REM Cotangent
10061 DEF FNCOT#(X#)=1/TAN#(X#)
10070 REM Inverse Sine
10071 DEF FNARCSIN#(X#)=ATN(X#/SQR(-X#*X#+1))
10080 REM Inverse Cosine
10081 DEF FNARCCOS#(X#)=ATN(X#/SQR(-X#*X#+1))+PI#/2
10090 REM Inverse Tangent
10091 DEF FNARCTAN#(X#)=ATN#(X#)
10100 REM Inverse Secant
10101 DEF FNARCSEC#(X#)=ATN(X#/SQR(X#*X#-1))+SGN(SGN#(X#)-1)*PI#/2
10110 REM Inverse Cosecant
10111 DEF FNARCCSC#(X#)=ATN(X#/SQR(X#*X#-1))+SGN#(X#)-1)*PI#/2
10120 REM Inverse Cotangent
10121 DEF FNARCCOT#(X#)=ATN#(X#)+PI#/2
10130 REM Hyperbolic Sine
10131 DEF FNSINH#(X#)=(EXP#(X#)-EXP(-X#))/2
10140 REM Hyperbolic Cosine
10141 DEF FNCOSH#(X#)=(EXP#(X#)+EXP(-X#))/2
10150 REM Hyperbolic Tangent
10151 DEF FNTANH#(X#)=EXP#(X#)-EXP(-X#))/+(EXP#(X#)+EXP(-X#))
10160 REM Hyperbolic Secant
10161 DEF FNSECH#(X#)=2/(EXP#(X#)+EXP(-X#))
10170 REM Hyperbolic Cosecant
10171 DEF FNCSCH#(X#)=2/(EXP#(X#)-EXP(-X#))
10180 REM Hyperbolic Cotangent
10181 DEF FNCOTH#(X#)=EXP(-X#)/(EXP#(X#)-EXP(-X#))*2+1
10190 REM Inverse Hyperbolic Sine
10191 DEF FNARCSINH#(X#)=LOG(X#/SQR(X#*X#+1))
10200 REM Inverse Hyperbolic Cosine
10201 DEF FNARCCOSH#(X#)=LOG(X#+SQR(X#*X#-1))
10210 REM Inverse Hyperbolic Tangent
10211 DEF FNARCTANH#(X#)=LOG((1+X#)/(1-X#))/2
10220 REM Inverse Hyperbolic Cosecant IHC
10221 DEF FNARCCSCH#(X#)=LOG(SGN#(X#)*SQR(X#*X#+1)+1)/X#
10230 REM Inverse Hyperbolic Secant
10231 DEF FNARCSECH#(X#)=LOG(SQR(-X#*X#+1)+1)/X#
10240 REM Inverse Hyperbolic Cotangent
10241 DEF FNARCCOTH#(X#)=LOG((X#+1)/(X#-1))/2
10299 RETURN
[/code:rmysaiot]

You can download the above code tagged source code of my &quot;GWTRIG.BAS&quot; GWBASIC source code along with GWBASIC 3.20, 3.22 and 3.23 from the following link: [url:rmysaiot]http&#58;//retromachineshop&#46;com/dl/basic/GWBASIC&#46;ZIP[/url:rmysaiot] (Also Included are some *.COM file drivers for GWBASIC: &quot;FISCHER.COM&quot; is a driver for robotics via both the LPT1/LPT2 printer ports; &quot;MOUSE.COM&quot; is a mouse driver.)

[quote=&quot;XlogicX&quot;:rmysaiot]To truly show an understanding of this, if you could play a sinewave and cosine wave at the exact same time and frequency, you would hear silence, this is because the sinewave is exactly the same distance above 0 as the cosine would be below it, or vice versa.[/quote:rmysaiot]

You are mistaken; Sine and Cosine are simply rotated 90 degrees of phase from each other, they'd have to be rotated 180 degrees from each other in-order to cancel each other out.

--------------------------------------------------------------------------------

Posted by **jargon** on Wed October 14th, 2009 12:10:20 AM

Here is an analog signal scrambler that I am working on. (As written in &quot;Goldwave&quot; waveform manipulation utility &quot;Expression Evaluator&quot; notation.)

&quot;Keal Binary Swap&quot;:
[code:1k9jjszj](((((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^7)))/(2^7))%2)*(2^7))/(2^7))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^6)))/(2^6))%2)*(2^6))/(2^5))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^5)))/(2^5))%2)*(2^5))/(2^3))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^4)))/(2^4))%2)*(2^4))/(2^1))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^3)))/(2^3))%2)*(2^3))*(2^1))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^2)))/(2^2))%2)*(2^2))*(2^3))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^1)))/(2^1))%2)*(2^1))*(2^5))+(((((int((wave1(n)+1)*(2^7))-(int((wave1(n)+1)*(2^7))%(2^0)))/(2^0))%2)*(2^0))*(2^7)))/(2^7))-1[/code:1k9jjszj]

I plan to combine this with &quot;Keal Binary Interlace&quot;.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed October 14th, 2009 04:25:17 AM

[quote:24fwywss]ou are mistaken; Sine and Cosine are simply rotated 90 degrees of phase from each other, they'd have to be rotated 180 degrees from each other in-order to cancel each other out.[/quote:24fwywss]

Nice catch, yeah, the sine wave would have to be 180 out of phase to be opposite of itself.

I'm curious, do you know why phlak and penguins postings in this thread have been ...'d out?

--------------------------------------------------------------------------------

Posted by **jargon** on Wed October 14th, 2009 06:09:46 AM

&quot;Keal's Eight Tier Analog Signal Swap&quot;:
[code:2m7o8xfj](((2*(int(((wave1(n)+1)*128)/(2^7))/2-int(int(((wave1(n)+1)*128)/(2^7))/2)))*(2^7)/(2^7)+(2*(int(((wave1(n)+1)*128)/(2^6))/2-int(int(((wave1(n)+1)*128)/(2^6))/2)))*(2^6)/(2^5)+(2*(int(((wave1(n)+1)*128)/(2^5))/2-int(int(((wave1(n)+1)*128)/(2^5))/2)))*(2^5)/(2^3)+(2*(int(((wave1(n)+1)*128)/(2^4))/2-int(int(((wave1(n)+1)*128)/(2^4))/2)))*(2^4)/(2^1)+(2*(int(((wave1(n)+1)*128)/(2^3))/2-int(int(((wave1(n)+1)*128)/(2^3))/2)))*(2^3)*(2^1)+(2*(int(((wave1(n)+1)*128)/(2^2))/2-int(int(((wave1(n)+1)*128)/(2^2))/2)))*(2^2)*(2^3)+(2*(int(((wave1(n)+1)*128)/(2^1))/2-int(int(((wave1(n)+1)*128)/(2^1))/2)))*(2^1)*(2^5)+(2*(int(((wave1(n)+1)*128)/(2^0))/2-int(int(((wave1(n)+1)*128)/(2^0))/2)))*(2^0)*(2^7))/(128))-1[/code:2m7o8xfj]

This is superior to my prior post's &quot;Keal Binary Swap&quot;: (AKA &quot;Keal's ADC/DAC 8bit Binary Swap&quot;)

[quote=&quot;XlogicX&quot;:2m7o8xfj][quote:2m7o8xfj]ou are mistaken; Sine and Cosine are simply rotated 90 degrees of phase from each other, they'd have to be rotated 180 degrees from each other in-order to cancel each other out.[/quote:2m7o8xfj]

Nice catch, yeah, the sine wave would have to be 180 out of phase to be opposite of itself.

I'm curious, do you know why phlak and penguins postings in this thread have been ...'d out?[/quote:2m7o8xfj]

My first post I changed to &quot;...&quot; so they kept replying with &quot;...&quot; to punk the thread as if the first post in this thread was the only one that mattered and solely defined &quot;what goes&quot; in this discussion.

Here is my work thus-far on the unsimplified version of &quot;Keal's Eight Tier Analog Signal Interlace&quot;: (It still doesn't inverse itself. *:(*)
[code:2m7o8xfj](((2*(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)))))))/128-1[/code:2m7o8xfj]

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon April 12th, 2010 10:40:41 AM

[quote=&quot;jargon&quot;:259ebm5u]Here is my work thus-far on the unsimplified version of &quot;Keal's Eight Tier Analog Signal Interlace&quot;: (It still doesn't inverse itself. *:(*)
[code:259ebm5u](((2*(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)))))))/128-1[/code:259ebm5u][/quote:259ebm5u] This equation seems unnecessarily complex. It can be simplified to the following equation:[code:259ebm5u]-1[/code:259ebm5u]

--------------------------------------------------------------------------------

Posted by **jargon** on Sat May 8th, 2010 11:26:18 PM

[quote=&quot;Medicine Storm&quot;:35vosiln][quote=&quot;jargon&quot;:35vosiln]Here is my work thus-far on the unsimplified version of &quot;Keal's Eight Tier Analog Signal Interlace&quot;: (It still doesn't inverse itself. *:(*)
[code:35vosiln](((2*(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)))))))/128-1[/code:35vosiln][/quote:35vosiln] This equation seems unnecessarily complex. It can be simplified to the following equation:[code:35vosiln]-1[/code:35vosiln][/quote:35vosiln]

Just go ahead and admit that you don't know math very well in any way shape or form.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon May 10th, 2010 12:24:01 AM

Indeed. What is this thing you call &quot;number&quot;

--------------------------------------------------------------------------------

Posted by **jargon** on Wed May 12th, 2010 12:05:07 AM

This function is the inverse and/or near-inverse of itself.

The graph/plot of the output does indeed appear to be solid -1, solid 1, or solid both -1 and 1 depending on what plotting method you use, the compactness of the complexity the plot exceeds the display resolution. However, it isn't solid -1.

Are you [b:6zu1airf][i:6zu1airf]*really*[/i:6zu1airf][/b:6zu1airf] confident in your decision to have assigned me that troll status now, mister too-sure-of-himself in his assertions to simply apply the filter and view/listen-to the plot yourself? You sure do look like a blatant dick now, don't you?

Let me assist:

(from) [url:6zu1airf]http&#58;//thekealshow&#46;com/seddd/?i=Keal%27s+8-Tier+Analog+Interlace[/url:6zu1airf]

Keal's 8-Tier Analog Interlace
<!-- m --><a class="postlink" href="http://thekealshow.com/">http://thekealshow.com/</a><!-- m -->

Before Plot, Mp3: [url:6zu1airf]http&#58;//thekealshow&#46;com/seddd/public/Keal's%208-Tier%20Analog%20Interlace/before&#46;mp3[/url:6zu1airf]
[img:6zu1airf]http&#58;//thekealshow&#46;com/seddd/public/Keal's%208-Tier%20Analog%20Interlace/before&#46;png[/img:6zu1airf]

After Plot, Mp3: [url:6zu1airf]http&#58;//thekealshow&#46;com/seddd/public/Keal's%208-Tier%20Analog%20Interlace/after&#46;mp3[/url:6zu1airf]
[img:6zu1airf]http&#58;//thekealshow&#46;com/seddd//public/Keal's%208-Tier%20Analog%20Interlace/after&#46;png[/img:6zu1airf]

Filter:
[code:6zu1airf](((2*(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^0))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(0/(2^7))/2-int(int(0/(2^7))/2)))*(2^7)/(2^7)+(2*(int(0/(2^6))/2-int(int(0/(2^6))/2)))*(2^6)/(2^5)+(2*(int(0/(2^5))/2-int(int(0/(2^5))/2)))*(2^5)/(2^3)+(2*(int(0/(2^4))/2-int(int(0/(2^4))/2)))*(2^4)/(2^1)+(2*(int(0/(2^3))/2-int(int(0/(2^3))/2)))*(2^3)*(2^1)+(2*(int(0/(2^2))/2-int(int(0/(2^2))/2)))*(2^2)*(2^3)+(2*(int(0/(2^1))/2-int(int(0/(2^1))/2)))*(2^1)*(2^5)+(2*(int(0/(2^0))/2-int(int(0/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^1))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(1/(2^7))/2-int(int(1/(2^7))/2)))*(2^7)/(2^7)+(2*(int(1/(2^6))/2-int(int(1/(2^6))/2)))*(2^6)/(2^5)+(2*(int(1/(2^5))/2-int(int(1/(2^5))/2)))*(2^5)/(2^3)+(2*(int(1/(2^4))/2-int(int(1/(2^4))/2)))*(2^4)/(2^1)+(2*(int(1/(2^3))/2-int(int(1/(2^3))/2)))*(2^3)*(2^1)+(2*(int(1/(2^2))/2-int(int(1/(2^2))/2)))*(2^2)*(2^3)+(2*(int(1/(2^1))/2-int(int(1/(2^1))/2)))*(2^1)*(2^5)+(2*(int(1/(2^0))/2-int(int(1/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^2))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(2/(2^7))/2-int(int(2/(2^7))/2)))*(2^7)/(2^7)+(2*(int(2/(2^6))/2-int(int(2/(2^6))/2)))*(2^6)/(2^5)+(2*(int(2/(2^5))/2-int(int(2/(2^5))/2)))*(2^5)/(2^3)+(2*(int(2/(2^4))/2-int(int(2/(2^4))/2)))*(2^4)/(2^1)+(2*(int(2/(2^3))/2-int(int(2/(2^3))/2)))*(2^3)*(2^1)+(2*(int(2/(2^2))/2-int(int(2/(2^2))/2)))*(2^2)*(2^3)+(2*(int(2/(2^1))/2-int(int(2/(2^1))/2)))*(2^1)*(2^5)+(2*(int(2/(2^0))/2-int(int(2/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^3))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(3/(2^7))/2-int(int(3/(2^7))/2)))*(2^7)/(2^7)+(2*(int(3/(2^6))/2-int(int(3/(2^6))/2)))*(2^6)/(2^5)+(2*(int(3/(2^5))/2-int(int(3/(2^5))/2)))*(2^5)/(2^3)+(2*(int(3/(2^4))/2-int(int(3/(2^4))/2)))*(2^4)/(2^1)+(2*(int(3/(2^3))/2-int(int(3/(2^3))/2)))*(2^3)*(2^1)+(2*(int(3/(2^2))/2-int(int(3/(2^2))/2)))*(2^2)*(2^3)+(2*(int(3/(2^1))/2-int(int(3/(2^1))/2)))*(2^1)*(2^5)+(2*(int(3/(2^0))/2-int(int(3/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^4))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(4/(2^7))/2-int(int(4/(2^7))/2)))*(2^7)/(2^7)+(2*(int(4/(2^6))/2-int(int(4/(2^6))/2)))*(2^6)/(2^5)+(2*(int(4/(2^5))/2-int(int(4/(2^5))/2)))*(2^5)/(2^3)+(2*(int(4/(2^4))/2-int(int(4/(2^4))/2)))*(2^4)/(2^1)+(2*(int(4/(2^3))/2-int(int(4/(2^3))/2)))*(2^3)*(2^1)+(2*(int(4/(2^2))/2-int(int(4/(2^2))/2)))*(2^2)*(2^3)+(2*(int(4/(2^1))/2-int(int(4/(2^1))/2)))*(2^1)*(2^5)+(2*(int(4/(2^0))/2-int(int(4/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^5))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(5/(2^7))/2-int(int(5/(2^7))/2)))*(2^7)/(2^7)+(2*(int(5/(2^6))/2-int(int(5/(2^6))/2)))*(2^6)/(2^5)+(2*(int(5/(2^5))/2-int(int(5/(2^5))/2)))*(2^5)/(2^3)+(2*(int(5/(2^4))/2-int(int(5/(2^4))/2)))*(2^4)/(2^1)+(2*(int(5/(2^3))/2-int(int(5/(2^3))/2)))*(2^3)*(2^1)+(2*(int(5/(2^2))/2-int(int(5/(2^2))/2)))*(2^2)*(2^3)+(2*(int(5/(2^1))/2-int(int(5/(2^1))/2)))*(2^1)*(2^5)+(2*(int(5/(2^0))/2-int(int(5/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^6))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(6/(2^7))/2-int(int(6/(2^7))/2)))*(2^7)/(2^7)+(2*(int(6/(2^6))/2-int(int(6/(2^6))/2)))*(2^6)/(2^5)+(2*(int(6/(2^5))/2-int(int(6/(2^5))/2)))*(2^5)/(2^3)+(2*(int(6/(2^4))/2-int(int(6/(2^4))/2)))*(2^4)/(2^1)+(2*(int(6/(2^3))/2-int(int(6/(2^3))/2)))*(2^3)*(2^1)+(2*(int(6/(2^2))/2-int(int(6/(2^2))/2)))*(2^2)*(2^3)+(2*(int(6/(2^1))/2-int(int(6/(2^1))/2)))*(2^1)*(2^5)+(2*(int(6/(2^0))/2-int(int(6/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3))))))+((2*(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2-int(int((((wave1(n)+1)*128)/(2^7))/(2^0))/2)))*2^(7-(((2^3)*(int(((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)-int(int((((2*(int(7/(2^7))/2-int(int(7/(2^7))/2)))*(2^7)/(2^7)+(2*(int(7/(2^6))/2-int(int(7/(2^6))/2)))*(2^6)/(2^5)+(2*(int(7/(2^5))/2-int(int(7/(2^5))/2)))*(2^5)/(2^3)+(2*(int(7/(2^4))/2-int(int(7/(2^4))/2)))*(2^4)/(2^1)+(2*(int(7/(2^3))/2-int(int(7/(2^3))/2)))*(2^3)*(2^1)+(2*(int(7/(2^2))/2-int(int(7/(2^2))/2)))*(2^2)*(2^3)+(2*(int(7/(2^1))/2-int(int(7/(2^1))/2)))*(2^1)*(2^5)+(2*(int(7/(2^0))/2-int(int(7/(2^0))/2)))*(2^0)*(2^7))/(2^6))/((2^3)^0))/(2^3)))))))/128-1[/code:6zu1airf]
