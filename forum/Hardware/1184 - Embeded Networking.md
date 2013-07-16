## Embeded Networking
Posted by **Automated Penguin** on Wed December 30th, 2009 11:40:49 AM

Looks like my next project is going to be an embedded networking device which monitors some piece of hardware and sends out emails or other alerts when certain events are detected. 

Another possibility would be an embedded web server which relays the status of the hardware via a web-page.

After a moderate amount of research it seems like microchip's ENC28J60 ethernet controller is a pretty reasonable way to go for putting a micro-controller on Ethernet. 

Data-sheet:
<!-- m --><a class="postlink" href="http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en022889">http://www.microchip.com/wwwproducts/De ... e=en022889</a><!-- m -->

I guess I'm just wondering if anyone here has any experience with this chip or any embedded networking solutions at all.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed December 30th, 2009 06:44:22 PM

just did an arduino(logic is gonna make fun of me) that reads from an rss feed to display information and actually looking into working with PIC on doing something along the lines of what your looking to do but was gonna to use a twitter feed instead of a webpage.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed December 30th, 2009 08:05:22 PM

yeah but how did you do it.

details man, details.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Wed December 30th, 2009 09:48:10 PM

Posting from blackberry atm so details will be coming soon to a forum near you when back to PC proper.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Thu December 31st, 2009 08:33:40 AM

ok here is details
this isn't a stand alone embedded network device it does require a computer to interface between the internetz and the MC its also from when i first started with arduino and pretty much follows the tutorial in the make arduino book 
what it does is serach an rss feed for certain keywords then cause a multi color lamp to light up according to the amount of keywords
here is the code for the computer side
[code:2wmpdydk]// Example 08A&#58; Arduino networked lamp
// parts of the code are inspired
// by a blog post by Tod E&#46; Kurt (todbot&#46;com)
import processing&#46;serial&#46;*;
String feed = &quot;***********&quot;; // enter rss feed address here
int interval = 10; // retrieve feed every 60 seconds;
int lastTime; // the last time we fetched the content
int **** = 0; //keywords go here
int **** = 0; //and here
int **** = 0; // and finally here
int light = 0; // light level measured by the lamp
Serial port;
color c;
String cs;
String buffer = &quot;&quot;; // Accumulates characters coming from Arduino
PFont font;
void setup() {
size(640,480);
frameRate(10); // we don't need fast updates
font = loadFont(&quot;HelveticaNeue-Bold-32&#46;vlw&quot;);
fill(255);
textFont(font, 32);
// IMPORTANT NOTE&#58;
// The first serial port retrieved by Serial&#46;list()
// should be your Arduino&#46; If not, uncomment the next
// line by deleting the // before it, and re-run the
// sketch to see a list of serial ports&#46; Then, change
// the 0 in between &#91; and &#93; to the number of the port
// that your Arduino is connected to&#46;
//println(Serial&#46;list());
String arduinoPort = Serial&#46;list()&#91;0&#93;;
port = new Serial(this, arduinoPort, 9600); // connect to Arduino
lastTime = 0;
fetchData();
}
void draw() {
background( c );
int n = (interval - ((millis()-lastTime)/1000));
// Build a colour based on the 3 values
c = color(******, ******, ******); //enter same keywords here
cs = &quot;#&quot; + hex(c,6); // Prepare a string to be sent to Arduino
text(&quot;Arduino Networked Lamp&quot;, 10,40);
text(&quot;Reading feed&#58;&quot;, 10, 100);
text(feed, 10, 140);
text(&quot;Next update in &quot;+ n + &quot; seconds&quot;,10,450);
text(&quot;*****&quot; ,10,200); //keyword goes here
text(&quot; &quot; + *****, 130, 200); //same one here
rect(200,172, ******, 28); //keyword again
text(&quot;***** &quot;,10,240); //another keyword
text(&quot; &quot; + *****, 130, 240); //another keyword again
rect(200,212, ******, 28); //one more time with the keyword
text(&quot;***** &quot;,10,280); //use keywords here to set light sequence
text(&quot; &quot; + ******, 130, 280);
rect(200,252, *******, 28);
// write the colour string to the screen
text(&quot;sending&quot;, 10, 340);
text(cs, 200,340);
text(&quot;light level&quot;, 10, 380);
rect(200, 352,light/10&#46;23,28); // this turns 1023 into 100
if (n &lt;= 0) {
fetchData();
lastTime = millis();
}
port&#46;write(cs); // send data to Arduino
if (port&#46;available() &gt; 0) { // check if there is data waiting
int inByte = port&#46;read(); // read one byte
if (inByte != 10) { // if byte is not newline
buffer = buffer + char(inByte); // just add it to the buffer
}
else {
// newline reached, let's process the data
if (buffer&#46;length() &gt; 1) { // make sure there is enough data
// chop off the last character, it's a carriage return
// (a carriage return is the character at the end of a
// line of text)
buffer = buffer&#46;substring(0,buffer&#46;length() -1);
// turn the buffer from string into an integer number
light = int(buffer);
// clean the buffer for the next read cycle
buffer = &quot;&quot;;
// We're likely falling behind in taking readings
// from Arduino&#46; So let's clear the backlog of
// incoming sensor readings so the next reading is
// up-to-date&#46;
port&#46;clear();
}
}
}
}
void fetchData() {
// we use these strings to parse the feed
String data;
String chunk;
// zero the counters
***** = 0; //yup keywords
****** = 0;
***** = 0;
try {
URL url = new URL(feed); // An object to represent the URL
// prepare a connection
URLConnection conn = url&#46;openConnection();
conn&#46;connect(); // now connect to the Website
// this is a bit of virtual plumbing as we connect
// the data coming from the connection to a buffered
// reader that reads the data one line at a time&#46;
BufferedReader in = new
BufferedReader(new InputStreamReader(conn&#46;getInputStream()));
// read each line from the feed
while ((data = in&#46;readLine()) != null) {
StringTokenizer st =
new StringTokenizer(data,&quot;\&quot;&lt;&gt;,&#46;()&#91;&#93; &quot;);// break it down
while (st&#46;hasMoreTokens()) {
// each chunk of data is made lowercase
chunk= st&#46;nextToken()&#46;toLowerCase() ;
if (chunk&#46;indexOf(&quot;*****&quot;) &gt;= 0 ) // found &quot;*****&quot;?
love++; // increment ****** by 1
if (chunk&#46;indexOf(&quot;******&quot;) &gt;= 0) // found &quot;*****&quot;?
peace++; // increment ***** by 1
if (chunk&#46;indexOf(&quot;*****&quot;) &gt;= 0) // found &quot;****&quot;?
arduino++; // increment ***** by 1
}
}
// Set 64 to be the maximum number of references we care about&#46;
if (****** &gt; 64) ***** = 64; //you should know by now its keyword time
if (***** &gt; 64) ***** = 64;
if (***** &gt; 64) ***** = 64;
***** = ***** * 4; // multiply by 4 so that the max is 255, isolated * is not part of the keyword
***** = **** * 4; // which comes in handy when building a
***** = ***** * 4; // colour that is made of 4 bytes (ARGB)
}
catch (Exception ex) { // If there was an error, stop the sketch
ex&#46;printStackTrace();
System&#46;out&#46;println(&quot;ERROR&#58; &quot;+ex&#46;getMessage());
}
}
[/code:2wmpdydk]

ok and now for the arduino skecth 
[code:2wmpdydk]// Example 08B&#58; Arduino Networked Lamp
#define SENSOR 0
#define R_LED 9
#define G_LED 10
#define B_LED 11
#define BUTTON 12
int val = 0; // variable to store the value coming from the sensor
int btn = LOW;
int old_btn = LOW;
int state = 0;
char buffer&#91;7&#93; ;
int pointer = 0;
byte inByte = 0;
byte r = 0;
byte g = 0;
byte b = 0;
void setup() {
Serial&#46;begin(9600); // open the serial port
pinMode(BUTTON, INPUT);
}
void loop() {
val = analogRead(SENSOR); // read the value from the sensor
Serial&#46;println(val); // print the value to
// the serial port
if (Serial&#46;available() &gt;0) {
// read the incoming byte&#58;
inByte = Serial&#46;read();
// If the marker's found, next 6 characters are the colour
if (inByte == '#') {
while (pointer &lt; 6) { // accumulate 6 chars
buffer&#91;pointer&#93; = Serial&#46;read(); // store in the buffer
pointer++; // move the pointer forward by 1
}// now we have the 3 numbers stored as hex numbers
// we need to decode them into 3 bytes r, g and b
r = hex2dec(buffer&#91;1&#93;) + hex2dec(buffer&#91;0&#93;) * 16;
g = hex2dec(buffer&#91;3&#93;) + hex2dec(buffer&#91;2&#93;) * 16;
b = hex2dec(buffer&#91;5&#93;) + hex2dec(buffer&#91;4&#93;) * 16;
pointer = 0; // reset the pointer so we can reuse the buffer
}
}
btn = digitalRead(BUTTON); // read input value and store it
// Check if there was a transition
if ((btn == HIGH) &amp;&amp; (old_btn == LOW)){
state = 1 - state;
}
old_btn = btn; // val is now old, let's store it
if (state == 1) { // if the lamp is on
analogWrite(R_LED, r); // turn the leds on
analogWrite(G_LED, g); // at the colour
analogWrite(B_LED, b); // sent by the computer
} else {
analogWrite(R_LED, 0); // otherwise turn off
analogWrite(G_LED, 0);
analogWrite(B_LED, 0);
}
delay(100); // wait 100ms between each send
}
int hex2dec(byte c) { // converts one HEX character into a number
if (c &gt;= '0' &amp;&amp; c &lt;= '9') {
return c - '0';
} else if (c &gt;= 'A' &amp;&amp; c &lt;= 'F') {
return c - 'A' + 10;
}
}[/code:2wmpdydk]
like i said not a standalone but a start 
I am not thinking of do a feed from the micro processor to prolly a twitter account using the ENC28J60 ethernet controller was also thinking of doing something along the lines of being able to send a message thru internet to a MP and having it start my coffee pot or control my house thermostat remotely.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 1st, 2010 11:31:21 AM

yeah I made a USB peripheral once using an ftdi chip and a pic, now I really want to make it all embedded including Ethernet control.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri January 1st, 2010 03:33:32 PM

what exactly do you want it to do i've seen PIC based web servers? I'm guessing you want to just have your board plug into a router and provide some kind of data or service.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Fri January 1st, 2010 04:15:48 PM

the idea is to have a series of small networked monitoring devices to report from around the house, almost like a security system but monitoring more than just entry points and much more customizable.

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Fri January 1st, 2010 07:22:41 PM

sounds very do-able and fun 
I would  try looking at how builds for security systems and tweetawatt work and expanding on those idea

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon January 11th, 2010 09:15:50 PM

Just thought I would post an update on my project.

I ordered a pickit clone for programming 18 and 24 series pics and decided on an archatecture.

Using a pic24 and An ENC 28J60.

I have finished the schematic and the board layout (below) and i should be moving on to etching the board and soldering components within the next day or so.

So far I must say programming the 18 and 24 series chips in C is a real treat compared to the assembly. The C libraries that microchip provides for the hardware peripherals is completely awesome, I mean you still have to do some stuff like brgh and spbrg calculations for baud rate on the usart and timing calculations for calibrating the PWM but you can get simple calculators for that stuff.

The only problem with programming in anything above assembly is you tend to forget whats really going on down there at the machine code level which is kinda sad in a way but totally worth it for the ease of coding in C.

PICS:

Board:
[url:36dk3vub]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/board&#46;png[/url:36dk3vub]
Schematic:
[url:36dk3vub]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/sch&#46;png[/url:36dk3vub]
Shitty Eagle 3d Rendering:
[url:36dk3vub]http&#58;//www&#46;public&#46;asu&#46;edu/~cbock/Pic24%20Demo%20Board&#46;bmp[/url:36dk3vub]

--------------------------------------------------------------------------------

Posted by **TerrorDrone** on Tue January 12th, 2010 06:43:51 AM

Can you post a copy of the code for it if its cool I'd like to take a look at it.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Wed January 13th, 2010 05:39:15 PM

One crisp new Amerikkan dollar to the person who can find the MASSIVE error i made in my board design, which i only noticed AFTER I finished etching the board and soldering on components.

[img:1jxjcqxn]http&#58;//knowyourmeme&#46;com/i/578/original/1234931504682&#46;jpg[/img:1jxjcqxn]

Hint*

I was able to fix the issue with one well placed solder bridge.
