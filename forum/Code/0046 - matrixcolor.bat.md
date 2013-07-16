## matrixcolor.bat
Posted by **Valveritas** on Sun February 3rd, 2008 11:41:46 PM

Here's something I wrote today that's kind of fun to run for the purpose of having a cheap screen saver (do we even still need those?), or a prank such as: &quot;What the hell is that?!&quot;

What it does is take 3 color values that you provide and runs an infinite loop of random numbers and color.  It looks cool for no particular reason - kind of psychedelic.  It's best to run it in a larger window, or full screen.  Normally when using the COLOR command you only see one color on the screen at a time, but by doing it this way with characters constantly rolling off the screen you see all 3 colors.  

It includes error checking beyond the norm, for no other reason than I've been working on that more and for completion sake. If you use the color value of 2 for each color it'll look most like the &quot;matrix&quot;.  

[code:3dyvrkbb]
@ echo off
&#58;redo
cls
echo Matrixcolor v1&#46;0 written by Gargantuan Orangutan/CultLeadr
echo&#46;
echo        0 = Black       8 = Gray
echo        1 = Blue        9 = Light Blue
echo        2 = Green       A = Light Green
echo        3 = Aqua        B = Light Aqua
echo        4 = Red         C = Light Red
echo        5 = Purple      D = Light Purple
echo        6 = Yellow      E = Light Yellow
echo        7 = White       F = Bright White
echo&#46;
echo Double alphanumeric allowed, but do not use letters after F
&#58;&#58; Example 2, 5, 4
echo&#46;
Set start=0
Set length=2
&#58;&#58;
set /p colorone=&quot;First color? &quot;
if &quot;%colorone%&quot;==&quot;&quot; (
	echo That input cannot be used, you must restart
	pause 
	goto redo
)
CALL SET colorone=%%colorone&#58;~%start%,%length%%%
Echo First color is&#58; %colorone%
color %colorone%
If errorlevel ==1 (
	echo Foreground and background cannot be the same, you must restart
	pause 
	goto redo
)
&#58;&#58;
set /p colortwo=&quot;Second color? &quot;
if &quot;%colortwo%&quot;==&quot;&quot; (
	echo That input cannot be used, you must restart
	pause 
	goto redo
)
CALL SET colortwo=%%colortwo&#58;~%start%,%length%%%
Echo Second color is&#58; %colortwo%
color %colortwo%
If errorlevel ==1 (
	echo Foreground and background cannot be the same, you must restart
	pause 
	goto redo
)
&#58;&#58;
set /p colorthree=&quot;Third color? &quot;
if &quot;%colorthree%&quot;==&quot;&quot; (
	echo That input cannot be used, you must restart
	pause 
	goto redo
)
CALL SET colorthree=%%colorthree&#58;~%start%,%length%%%
Echo Third color is&#58; %colorthree%
color %colorthree%
If errorlevel ==1 (
	echo Foreground and background cannot be the same, you must restart
	pause 
	goto redo
)

set ready=
echo&#46;
set /p ready=&quot;Are you ready to partay &#91;Y/N&#93;? &quot;
if /i '%ready%'=='y' goto start
if /i '%ready%'=='n' goto redo

&#58;start
color %colorone%
echo %random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%
color %colortwo%
echo %random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%
color %colorthree%
echo %random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%%random%
goto start
[/code:3dyvrkbb]
