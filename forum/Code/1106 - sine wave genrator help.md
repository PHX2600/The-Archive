## sine wave genrator help
Posted by **TerrorDrone** on Tue September 15th, 2009 08:46:36 PM

writing up a sine wave generator and this is the error which keeps coming up if anyone could help me fix it i would appreciate it 
error is POLINK: error: Unresolved external symbol '_main'.
POLINK: fatal error: 1 unresolved external(s).
[code:327nq846]/*  File&#58; sinez&#46;h
* Header information for sinez&#46;c
*/

#ifndef sinez_h
#define sinez_h

/* Function Prototypes*/

#ifdef  __cplusplus
extern  &quot;C&quot;  {
#endif

	double sinez ();

#ifdef  __cplusplus
}
#endif

#endif /*_SINEZ_H_*/
[/code:327nq846]
[code:327nq846]/* File&#58;sinez&#46;c
* Sine Wave Generator
*/

#include &quot;sinez&#46;h&quot;
int j;
double wT, k, xn1, xn2 ,xn;

double sinez ()
{
	wT = 0&#46;2;
	k = 1&#46;960133;
	xn1 = 0&#46;1986693;
	xn2 = 0&#46;3894183;
	for (j = 1; j &lt;= 100; ++j)
	{
		xn = - (2 - k) * xn1 + xn1 - xn2 + xn1;
		xn2 = xn1;
		xn1 = xn;
		return xn;
	}
}
[/code:327nq846]

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Tue September 15th, 2009 09:36:02 PM

its probably looking for a main function to start in since its C

rename your function to main and try again, if that doesn't work you can always try assembly.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue September 15th, 2009 10:46:05 PM

hmm had error further up the list i missed 
warning #2027: Missing prototype for 'sine'.

--------------------------------------------------------------------------------

Posted by **RetroTech1541** on Tue September 15th, 2009 11:01:28 PM

Don't rename sinez to main, but if you want to run the program, you do need the entry-point which will call it.

Have something like main.c
[code:2pp2omox]
#include &quot;sinez&#46;h&quot;

int main(int argc, char** argv) {
   double d;
   for(;;)
     d = sinez();
   return 0;
}
[/code:2pp2omox]

That's should take care of that linker error. As for the compiler warning, rename sinez.cpp to sinez.c, that should eliminate it.

Also, compiling would look like this:
cc main.c sinez.c

And that should run the linker automatically.
Sorry I couldn't be specific to your stuff, I don't have it or know it.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Thu September 17th, 2009 12:51:36 AM

Did somebody say Assembly?  <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) --> 

This is an audio driver I wrote in ASM for my propeller controller, this is an old version (i'm working on the new version now). This version only supports one channel, but it can do different wave shapes (based on a sample), frequencies, duration, volume, and even a cool trick that I call pixelizing (being able to go from 16-bit audio to 5-bit, to 9-bit to whatever, on the fly).

I'm working on a 4 channel driver, I have a workable strategy, but the code will be much more complicated, since I will now be dealing with compression, a virtual mixer, mixing different samples at different frequencies, and the fact that I will need to process in parallel (will be using 3 of the 7 cores offered to me), since the more time it takes to get through the loop, the more of the high frequencies you're going to cut out. If this doesn't already sound simple enough, keep in mind it's assembly; you don't even have an opcode for divide.

I am having to re-write my new version from scratch, so it wont look anything like this:
[code:1savspaw]
CON
  _clkmode = xtal1 + pll16x
  _xinfreq = 5_000_000

DAT
sawwave       long      $0200_0400, $0600_0800, $0A00_0C00, $0E00_1000, $1200_1400, $1600_1800, $1A00_1C00, $1E00_2000, $2200_2400
              long      $2600_2800, $2A00_2C00, $2E00_3000, $3200_3400, $3600_3800, $3A00_3C00, $3E00_4000, $4200_4400, $4600_4800
              long      $4A00_4C00, $4E00_5000, $5200_5400, $5600_5800, $5A00_5C00, $5E00_6000, $6200_6400, $6600_6800, $6A00_6C00
              long      $6E00_7000, $7200_7400, $7600_7800, $7A00_7C00, $7E00_8000, $8200_8400, $8600_8800, $8A00_8C00, $8E00_9000
              long      $9200_9400, $9600_9800, $9A00_9C00, $9E00_A000, $A200_A400, $A600_A800, $AA00_AC00, $AE00_B000, $B200_B400
              long      $B600_B800, $BA00_BC00, $BE00_C000, $C200_C400, $C600_C800, $CA00_CC00, $CE00_D000, $D200_D400, $D600_D800
              long      $DA00_DC00, $DE00_E000, $E200_E400, $E600_E800, $EA00_EC00, $EE00_F000, $F200_F400, $F600_F800, $FA00_FC00
              long      $FE00_FFFF

sinewave      long      $8324_896A, $8FAB_95E2, $9C0B_A223, $A826_AE11, $B3DE_B98C, $BF17_C47A, $C9B4_CEBF, $D39B_D842, $DCB4_E0EC
              long      $E4E8_E8A6, $EC24_EF5F, $F255_F504, $F76C_F98A, $FB5D_FCE3, $FE1D_FF09, $FFA7_FFF6, $FFF6_FFA7, $FF09_FE1D
              long      $FCE3_FB5D, $F98A_F76C, $F504_F255, $EF5F_EC24, $E8A6_E4E8, $E0EC_DCB4, $D842_D39B, $CEBF_C9B4, $C47A_BF17
              long      $B98C_B3DE, $AE11_A826, $A223_9C0B, $95E2_8FAB, $896A_8324, $7CDB_7695, $7054_6A1D, $63F4_5DDC, $57D9_51EE
              long      $4C21_4673, $40E8_3B85, $364B_3140, $2C64_27BD, $234B_1F13, $1B17_1759, $13DB_10A0, $0DAA_0AFB, $0893_0675
              long      $04A2_031C, $01E2_00F6, $0058_0009, $0009_0058, $00F6_01E2, $031C_04A2, $0675_0893, $0AFB_0DAA, $10A0_13DB
              long      $1759_1B17, $1F13_234B, $27BD_2C64, $3140_364B, $3B85_40E8, $4673_4C21, $51EE_57D9, $5DDC_63F4, $6A1D_7054
              long      $7695_7CDB

triangle      long      $0200_0600, $0A00_0E00, $1200_1600, $1A00_1E00, $2200_2600, $2A00_2E00, $3200_3600, $3A00_3E00, $4200_4600
              long      $4A00_4E00, $5200_5600, $5A00_5E00, $6200_6600, $6A00_6E00, $7200_7600, $7A00_7E00, $8200_8600, $8A00_8E00
              long      $9200_9600, $9A00_9E00, $A200_A600, $AA00_AE00, $B200_B600, $BA00_BE00, $C200_C600, $CA00_CE00, $D200_D600
              long      $DA00_DE00, $E200_E600, $EA00_EE00, $F200_F600, $FA00_FE00, $FFFF_FC00, $F800_F400, $F000_EC00, $E800_E400
              long      $E000_DC00, $D800_D400, $D000_CC00, $C800_C400, $C000_BC00, $B800_B400, $B000_AC00, $A800_A400, $A000_9C00
              long      $9800_9400, $9000_8C00, $8800_8400, $8000_7C00, $7800_7400, $7000_6C00, $6800_6400, $6000_5C00, $5800_5400
              long      $5000_4C00, $4800_4400, $4000_3C00, $3800_3400, $3000_2C00, $2800_2400, $2000_1C00, $1800_1400, $1000_0C00
              long      $0800_0400

hump          long      $0648_0C8F, $12D5_1917, $1F56_2590, $2BC4_31F1, $3817_3E33, $4447_4A50, $504D_563E, $5C22_61F7, $67BD_6D74
              long      $7319_78AD, $7E2E_839C, $88F5_8E39, $9368_987F, $9D7F_A267, $A736_ABEB, $B085_B504, $B968_BDAE, $C1D8_C5E4
              long      $C9D1_CD9F, $D14D_D4DB, $D848_DB94, $DEBE_E1C5, $E4AA_E76B, $EA09_EC83, $EED8_F109, $F314_F4FA, $F6BA_F853
              long      $F9C7_FB14, $FC3B_FD3A, $FE13_FEC4, $FF4E_FFB1, $FFEC_FFFF, $FFEC_FFB1, $FF4E_FEC4, $FE13_FD3A, $FC3B_FB14
              long      $F9C7_F853, $F6BA_F4FA, $F314_F109, $EED8_EC83, $EA09_E76B, $E4AA_E1C5, $DEBE_DB94, $D848_D4DB, $D14D_CD9F
              long      $C9D1_C5E4, $C1D8_BDAE, $B968_B504, $B085_ABEB, $A736_A267, $9D7F_987F, $9368_8E39, $88F5_839C, $7E2E_78AD
              long      $7319_6D74, $67BD_61F7, $5C22_563E, $504D_4A50, $4447_3E33, $3817_31F1, $2BC4_2590, $1F56_1917, $12D5_0C8F
              long      $0648_0000                     

VAR

long    freq          'variable that controls wave frequency (has limits of how low it can be &#91;8&#93;)
long    volume        'lower value equals larger volume
long    quality       '0 = 16-bit, 1 = 15-bit, 2 = 14-bit&#46;&#46;&#46;&#46;
long    duration      'how long to play the note
long    shape         'what type or shape of wave (sine, saw, etc&#46;&#46;&#46;)

PUB Main

  freq &#58;= $FFF
  volume &#58;= 0
  quality &#58;= 0
  duration &#58;= $FFFF
  shape &#58;= 1
  cognew(@PCM, @freq)


DAT

        '------------------------------------------------&#91;Initialization&#93;----------------------------------------------------------'
        '                                          &#91;41&#46;25 microsecond init time&#93;
              org       0
PCM           mov       dira, pinmask           'turn pins to outputs based on mask
              mov       ctra, CtrCfg            'single ended duty, pin 31

            '&#91;Grabs varibles from spin and loads them into local cog&#93;
              mov       delay, par              'put address of spin freq in delay
              mov       vol, par                'put address of VAR beginning index in vol
              mov       qual, par               'put address of VAR beginning index in qual
              mov       dur, par                'put address of VAR beginning index in dur
              mov       asmshape, par           'put address of VAR beginning index in asmshape
              mov       wavemem, waveadr        'put start address of wave data into wavemem
              add       vol, #4                 'jump to spin volume adress and store it in asm vol
              add       qual, #8                'jump to spin quality adress and store it in asm qual 
              add       dur, #12                'jump to spin duration adress and store it in asm dur 
              add       asmshape, #16           'jump to spin shape adress and store it in asm asmshape 
              rdlong    delay, delay            'Put value of delay address in variable delay
              rdlong    vol, vol                'Put value of vol address in variable vol
              rdlong    qual, qual              'Put value of qual address in variable qual
              rdlong    dur, dur                'Put value of qual address in variable qual
              rdlong    asmshape, asmshape      'Put value of asmshape address in variable asmshape

            '&#91;calculates what wave address to start at and writes value to wavemem in local cog&#93;
              mov       count, asmshape         'Start counter equal to the shape number in spin
&#58;mul          add       asmshape, #256          'this jumps to the next shape in address land
              djnz      count, #&#58;mul            'Will jump down as many shapes&#91;the address of&#93; as the shape number you give
              sub       asmshape, #256          'jump back up a shape (since the loop has to run atleast once)
              add       wavemem, asmshape       'add the new shape jumping index to the starting point of the shape address (if any)
              rdlong    wavemem, wavemem        'write this new value to wavemem

            '&#91;Pixilate audio&#93;
              shl       qualmask, qual          'lower the quality mask by 'qual'             

            '&#91;load local wave table with wave table from main memory&#93;
              movd      &#58;load, #wave            'put local wave in destination field of the command at load (the 0-0)
              mov       count, #64              'It takes 64 reps to load all 64 longs (128 samples in words)
&#58;load         mov       0-0, wavemem            'take main memory wave sample and put it to local wave sample
              mov       wavemem, waveadr        'load wavemem with main memory wave table start adress
              add       wavemem, asmshape       '\Add the shape offset to tell cog how many shapes down to move
              add       wavemem, waveinc        ' \Increment the main memory index by another long
              rdlong    wavemem, wavemem        '  \store the main memory value to local cog wave
              add       waveinc, #4             '   \next time loop will go 1 long farther in index
              add       &#58;load, wavemask         'Increment local cog index by 1 long
              djnz      count, #&#58;load           'loop if you havn't looped 64 times yet&#46;

        '----------------------------------------------------&#91;PCM loop&#93;------------------------------------------------------------'
Start         movs      &#58;pcm_loop, #wave        'put adr of wave in dest of pcm_loop command
              mov       count, #63              'set loop for 63 times (2 samples a loop)
              nop                               '\
              nop                               ' \
              nop                               '  \
              nop                               '    remove these to see if it still works--------------------

            '&#91;These next four instructions take a long value (that actually has two seperate samples as words in it), splits them&#93;
            '&#91;up into 2 seperate samples as longs, it has to mask the first one and shift the second one to make sure they are in&#93;
            '&#91;the correct format&#93;              
&#58;pcm_loop     mov       PCMVal, 0-0             'grabs wave index and puts it in PCMVal
              mov       PCMVal2, PCMVal         'Makes a second copy of PCMVal in PCMVal2
              and       PCMVal, PCMValMask      'grabs most significant word and masks off least significant word
              shl       PCMVal2, #16            'shifts least significat word up to most significant&#46;

            '&#91;Apply the special effects to upper sample&#93; 
              and       PCMVal, qualmask        'mask the qualmask to the sample
              shr       PCMVal, vol             'tells how much quieter to make the sound              
'             36 clock tics plus delay until PCMVal2 is loaded (for balance)
              mov       frqa, PCMVal            'write first wave index value to PWM
              mov       temp, delay             '\
              add       temp, cnt               ' \
              waitcnt   temp, #0                '  Code for in loop delay
              nop                               '\
              nop                               ' |
              nop                               ' |
              nop                               ' |  -possibly squeeze commands here later
              nop                               ' \
              nop                               '  Just for the extra 24 tics for balance
            '&#91;Apply the special effects to lower sample&#93; 
              and       PCMVal2, qualmask       'mask the qualmask to the sample 
              shr       PCMVal2, vol            'tells how much quieter to make the sound
'             36 clock tics plus delay until PCMVal1 is loaded again (for balance)
              mov       frqa, PCMVal2           'write second wave index value to PWM
              mov       temp, delay             '\
              add       temp, cnt               ' \
              waitcnt   temp, #0                '  Code for in loop delay                            
              add       &#58;pcm_loop, #1           'increment source field of pcm_loop command by 1 &#91;go to next value (as long) in wave index&#93;
              djnz      count, #&#58;pcm_loop       'end loop if count is 0, otherwise decrement and loop
              djnz      dur, #Start             'loop again if duration hasn't extinguished itself
              cogid     whoami                  'gets cogid
              cogstop   whoami                  'stops itself
                   

           '****&#91;Variables&#93;****'
CtrCfg        long %0_00110_000_00000000_000000_000_011111  'single ended duty, pin 31 
pinmask       long $80000000                                'make pin 31 an output
PCMVal        long 0                                        'upper sample word
PCMValMask    long $FFFF_0000                               'upper sample mask
PCMVal2       long 0                                        'lower sample word
temp          long 0
qualmask      long $FFFF0000                                'value to truncate quality
whoami        long $0                                       'ccgid

waveadr       long $18                                      'This is the starting address of wave tables (may change, keep an eye on this one)
wavemem       long 0                                        'Used as address variable for wave index in main memory
waveinc       long $4                                       'Variable of how much more to increment the index each pass through the loading loop
wavemask      long $200                                     'this has the value of 1 in the destination field, used to inc by 1

delay         long 0                                        'this value modifies frequency
vol           long 0                                        'this value modifies volume (by shifting right)
qual          long 0                                        'bit quality
dur           long 0                                        'sound duration
asmshape      long 0                                        'shape variable

count         byte 0                                        'loop counter

'*********** allocated local wave form ****************

wave    long 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
        long 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
        long 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
        long 0, 0, 0, 0, 0, 0, 0, 0 
[/code:1savspaw]

--------------------------------------------------------------------------------

Posted by **RetroTech1541** on Thu September 17th, 2009 09:50:35 AM

@xlogicx That was a very readable listing. I guess since you don't have a math co-processor you had to hard-code waveform data. That's cool, but how did you get that data? Did you write a program to generate it? Just curious cuz it's interesting.

@Anybody I found a pretty decent post on how to play frequencies out of the PC speaker with x86 asm. <!-- m --><a class="postlink" href="http://www.programmersheaven.com/mb/x86_asm/116530/116530/pc-speaker/?S=B20000">http://www.programmersheaven.com/mb/x86 ... /?S=B20000</a><!-- m --> .I don't know trig, but maybe combine that with the 387 op FSIN and make sin waves come out the speaker.

@terrordrone
I'm looking at what you're actually doing with sinez.c rather than just compiler output and here's something I noticed. You want to return 100 doubles with a loop. But what's happening is that the first and every time return is called, transfer of the program is returned to the calling function (like main in my prior post, where sinez was to be called for infinity.) The next time sinez is called, j is 1 again, you get the same return value. Since j is a global variable, you may want to initialize it to 1 before sinez is called and take out the initialization in the for loop. Again, because j has global scope, j will retain it's value between calls to sinez. Then, your sinez function will return different values while j is not greater than 100.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Thu September 17th, 2009 05:28:44 PM

wow that's some crazy assembly, that's for the propeller?

seems a lot nicer than stupid PIC ASM.

--------------------------------------------------------------------------------

Posted by **XlogicX** on Thu September 17th, 2009 09:18:23 PM

@Retro:
Actually you can do some decent math if you know the right tricks, and there is even a sine table in the ROM. There is also a log/antilog table as well (of which I will use for some quicker division/multiplication hacks). I actually manually created those hex tables <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->. I just did some math for the triangle wave. I used excel to give me some hex values for a sine wave; just math really. But the hex wasn't generated, that was manually shaped. I prefer this because of the purity,not even because of the sound, but to know I wasn't dependant on any other sound source, these sounds were created from scratch.

As far as computing them, that can be done too, someone wrote an excellent driver for the Hydra system that does this. That was the driver I was using in my bass guitar when I demo'd it at that meeting. I'm deciding to write my own because I outgrew the other one, and I want it to be my own code (even at the driver level).
