## First-Friday.php
Posted by **PHLAK** on Sat December 29th, 2007 11:09:24 PM

A little php I smashed together from misc. code, modified, and threw in some of my own tricks, that will generate the first Friday of next month for you.

[b:3qj4qoow]UPDATE: Latest revision available on Github: [url:3qj4qoow]http&#58;//github&#46;com/PHLAK/first-friday[/url:3qj4qoow][/b:3qj4qoow]

--------------------------------------------------------------------------------

Posted by **Konshu** on Sun December 30th, 2007 09:11:15 PM

Clever little add-in for the front page of the site to keep the information up-to-date automatically.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun December 30th, 2007 11:51:26 PM

I'm an automation addict!  I hate having to update things, even on a monthly basis.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue January 1st, 2008 01:35:36 AM

UH-OH!  The code is flawed... if you take a look, it's showing February 1st as the next meeting even though the next meeting is this Friday (January 4th).  If anyone can, please take a look at the code and let me know if you see the problem.  I'm pretty sure all we need to do is check to see if the first Friday of this month has already occurred, and if not, set that here:

[code:z8bxrx3d]//Next Month//
    if($t&#91;mon&#93;==&quot;12&quot;){
    $nm='1-'&#46;($t&#91;year&#93;+1);
    }
    else {
    $nm=($t&#91;mon&#93;+1)&#46;'-'&#46;$t&#91;year&#93;;
    }[/code:z8bxrx3d]

I'm skiing until Thursday night, but will hopefully have time to check up on it while I'm not skiing.  Thanks guys!

NOTE: I have removed some unneeded code in the original post to simplify.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue January 1st, 2008 01:03:29 PM

I think I found a solution.  This way it checks if the day of the month is &lt;=7, and the weekday is before Friday.  In the event it is, it will find the first friday of the current month, rather than next month.

[code:32tvmd42]
	//Calculate Next Month//
	if($t&#91;mon&#93;=='12'){
	  $nm='1-'&#46;($t&#91;year&#93;+1);
	}
	if($t&#91;mday&#93;&lt;='7' &amp;&amp; $t&#91;wday&#93;&lt;='5') {
		$nm=($t&#91;mon&#93;)&#46;'-'&#46;$t&#91;year&#93;;
	}
	else {
		$nm=($t&#91;mon&#93;+1)&#46;'-'&#46;$t&#91;year&#93;;
	}
[/code:32tvmd42]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun January 6th, 2008 01:39:55 PM

Code revised, it was calculating last Friday's date.

Added the following code:
[code:3rjskadw]
	if ($t&#91;mon&#93; == date('m',$date) &amp;&amp; $t&#91;mday&#93; &gt; date('j',$date) &amp;&amp; $t&#91;mon&#93; == '12') {
		$nm = '1-'&#46;($t&#91;year&#93;+1);
		$ff = get_day(&quot;first&quot;, &quot;friday&quot;, $nm);
	}
	if ($t&#91;mon&#93; == date('m',$date) &amp;&amp; $t&#91;mday&#93; &gt; date('j',$date) &amp;&amp; $t&#91;mon&#93; != '12') {
		$nm = ($t&#91;mon&#93;+1)&#46;'-'&#46;$t&#91;year&#93;;
		$ff = get_day(&quot;first&quot;, &quot;friday&quot;, $nm);
	}
	else {
		$ff = $date;
	}
[/code:3rjskadw]

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sat February 14th, 2009 08:10:19 PM

Just finished a total overhaul of the code.  I learned some new tricks (specifically the mktime function) and was able to significantly reduce the code and simplify it.  Check it out:

[code:2jwiuz7y]&lt;?php // first-friday&#46;php v0&#46;1&#46;3 by, Chris Kankiewicz &lt;http&#58;//www&#46;web-geek&#46;net&gt;

  // Calculate next Friday 
  for ($x = date('d'); $x &lt;= (date('d') + 6); $x++) {
    $timeStamp = mktime(0,0,0,date('m'),$x,date('Y'));
    if (date('w',$timeStamp) == 5) {
      $nextFriday = mktime(0,0,0,date('m'),$x,date('Y'));
    }
  }
  // Check if next Friday is the first friday of the month&#46;
  if (date('d', $nextFriday) &lt;= 7) {
    $firstFriday = $nextFriday;
  } else {
  // Calculate first Friday of next month
    for ($x = 1; $x &lt;= 7; $x++) {
      $timeStamp = mktime(0,0,0,date('m')+1,$x,date('Y'));
      if (date('w',$timeStamp) == 5) {
        $firstFriday = mktime(0,0,0,date('m')+1,$x,date('Y'));
      }
    }
  }

  // Echo next first Friday
  echo date(&quot;F j, Y&quot;, $firstFriday);

?&gt;[/code:2jwiuz7y]

--------------------------------------------------------------------------------

Posted by **jargon** on Sun December 27th, 2009 06:13:00 AM

Pwned by JavaScript.

The following is 100% my own code from scratch that I released under the Gnu Public License 2.0.

Demo at foot of every page: [url:2h6e9n1t]http&#58;//phx2600&#46;retromachineshop&#46;com/[/url:2h6e9n1t]

JavaScript code: (&quot;monthly-ticker.js&quot;)
[code:2h6e9n1t]/*
// The KEAL Show monthly event schedule ticker JavaScript
// Created by T&#46;R&#46;Keal December 27th 2009
// Released under the Gnu Public License 2&#46;0
//
// http&#58;//thekealshow&#46;com/
//
// Please review the Gnu Public License, Thank you&#46; 
// The GPL can be located online at http&#58;//www&#46;gnu&#46;org/copyleft/gpl&#46;html
*/

/* event schedule variables */
var eventAdjustHours=-7;     /* timezone hour offset, valid for -23 through 23 */
var eventAdjustMinutes=0;    /* timezone minute offset, valid for 0 through 59 */
var eventGroupName='monthly Phoenix&amp;#044; Arizona meetup for &amp;quot;2600&#58; The Hacker&amp;#039;s Quarterly Magazine&amp;quot;'; /* must use proper html escapes */
var eventLocationDesc='Gameworks Tempe &amp;#064; Arizona Mills Mall'; /* must use proper html escapes */
var eventStartWeek=1;        /* Is actually Nth ocurrance of eventStartDay in month, valid for 1 through 5&#46; */
var eventStartDay=6;         /* valid for 0 through 6 (0=Sunday, 1=Monday, 2=Tuesday, 3=Wednesday, 4=Thursday, 5=Friday, 6=Saturday) */
var eventStartHours=18;      /* valid for 0 through 23 */
var eventStartMinutes=0;     /* valid for 0 through 59 */
var eventEndDay=7;           /* valid for 0 through 6 (0=Sunday, 1=Monday, 2=Tuesday, 3=Wednesday, 4=Thursday, 5=Friday, 6=Saturday) */
var eventEndHours=0;         /* valid for 0 through 23 */
var eventEndMinutes=0;       /* valid for 0 through 59 */

/* presence calculation variables */
var nowUTC=new Date();
var nowDate=nowUTC&#46;getUTCDate();
var nowWeek=getUTCWeek(nowUTC);
var nowDay=nowUTC&#46;getUTCDay();
var nowHours=nowUTC&#46;getUTCHours();
var nowMinutes=nowUTC&#46;getUTCMinutes();
var nowSeconds=nowUTC&#46;getUTCSeconds();
var nowMilliseconds=nowUTC&#46;getUTCMilliseconds();

/* synchronization calculation variables */
var nowZero=nowUTC-(nowMilliseconds+1000*(nowSeconds+60*(nowMinutes+60*(nowHours+24*nowDay))));
var eventStartUTC=nowZero+60000*(eventStartMinutes-eventAdjustMinutes+60*(eventStartHours-eventAdjustHours+24*eventStartDay));
var eventEndUTC=nowZero+60000*(eventEndMinutes-eventAdjustMinutes+60*(eventEndHours-eventAdjustHours+24*eventEndDay));

/* align week */
if((eventStartDay&gt;eventEndDay)&amp;&amp;((nowDay&gt;=eventStartDay)||(nowDay&lt;=eventEndDay)))
{
	eventStartUTC-=86400000*7;
}
while(eventEndUTC&lt;eventStartUTC)
{
	eventEndUTC+=86400000*7;
}
while((eventStartUTC&lt;nowUTC)&amp;&amp;(eventEndUTC&lt;nowUTC))
{
	eventStartUTC+=86400000*7;
}
while(eventEndUTC&lt;eventStartUTC)
{
	eventEndUTC+=86400000*7;fs
}

/* align month */
while((getUTCWeek(eventStartUTC)!=eventStartWeek)&amp;&amp;(eventStartWeek&gt;=1)&amp;&amp;(eventStartWeek&lt;=5))
{
	eventStartUTC+=86400000*7;
	eventEndUTC+=86400000*7;
}

function getUTCWeek(UTC)
{
	var tmp=new Date(UTC);
	var tmp2=((tmp&#46;getUTCDate()-tmp&#46;getUTCDay()+7)%7)
	return Math&#46;floor((tmp&#46;getUTCDate()+tmp2-1)/7)+1;
}

function spanticker(spanUTC)
{
	var ret='';
	var tmp=0;
	tmp=Math&#46;floor(spanUTC/(7*86400000));
	if(tmp&gt;0)
	{
		ret=ret+tmp+'wk ';
	}
	tmp=Math&#46;floor(spanUTC/86400000)%7;
	if(tmp&gt;0)
	{
		ret=ret+tmp+'d ';
	}
	tmp=Math&#46;floor(spanUTC/Math&#46;floor(86400000/24))%24;
	if(tmp&gt;0)
	{
		ret=ret+tmp+'hr ';
	}
	tmp=Math&#46;floor(spanUTC/Math&#46;floor(86400000/(24*60)))%60;
	if(tmp&gt;0)
	{
		ret=ret+tmp+'min ';
	}
	tmp=Math&#46;floor(spanUTC/Math&#46;floor(86400000/(24*60*60)))%60;
	if(tmp&gt;0)
	{
		ret=ret+tmp+'sec ';
	}
	if(ret&#46;substr(ret&#46;length-1,1)==' ')
	{
		ret=ret&#46;substr(0,ret&#46;length-1);
	}
	if(ret=='')
	{
		ret='0sec';
	}
	return ret;
}

function ticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc)
{
	while((getUTCWeek(eventStartUTC)!=eventStartWeek)&amp;&amp;(eventStartWeek&gt;=1)&amp;&amp;(eventStartWeek&lt;=5))
	{
		eventStartUTC+=86400000*7;
		eventEndUTC+=86400000*7;
	}
	var nowUTC=new Date();
	while((nowUTC&gt;eventStartUTC)&amp;&amp;(nowUTC&gt;eventEndUTC))
	{
		eventStartUTC+=86400000*7;
		eventEndUTC+=86400000*7;
	}
	var spanUTC=Math&#46;abs(eventStartUTC-nowUTC);
	if((nowUTC&gt;=eventStartUTC)&amp;&amp;(nowUTC&lt;=eventEndUTC))
	{
		return 'The current '+eventGroupName+' event at '+eventLocationDesc+' has been in progress '+spanticker(spanUTC)+' of '+spanticker(eventEndUTC-eventStartUTC)+'&#46;';
	}
	else if(nowUTC&lt;eventStartUTC)
	{
		return 'The next '+spanticker(eventEndUTC-eventStartUTC)+' in duration '+eventGroupName+' at '+eventLocationDesc+' will start in '+spanticker(spanUTC)+'&#46;';
	}
	else
	{
		return 'The event progress ticker has failed&#46; (Unknown scripting error)';
	}
}

function dispticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc)
{
	document&#46;getElementById('ticker')&#46;innerHTML=ticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc);
	setTimeout('dispticker('+eventStartWeek+','+eventStartUTC+','+eventEndUTC+',\''+eventGroupName+'\',\''+eventLocationDesc+'\')',990);	
}

/* begin ticker */
dispticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc);
[/code:2h6e9n1t]

HTML code for calling script properly: (notice the JavaScript include comes *after* the &quot;&lt;h3&gt;&quot; with id=&quot;ticker&quot;!)
[code:2h6e9n1t]&lt;h3 id=&quot;ticker&quot;&gt;The monthly event ticker javascript has failed&#46;&lt;/h3&gt;
&lt;script language=&quot;JavaScript&quot; src=&quot;&#46;/js/monthly-ticker&#46;js&quot;&gt;&lt;/script&gt;[/code:2h6e9n1t]

--------------------------------------------------------------------------------

Posted by **jargon** on Thu January 28th, 2010 01:59:04 AM

There was a glitch due to converting from local time to UTC instead of from UTC to &quot;local&quot; UTC. (Same millisecond of day for same day that UTC offset would have.)

Here is the latest version of the script which includes clock render with the 5 weekly The KEAL Show &quot;Supervillain Sunday&quot; airtimes per month, the phx2600 meet-up, and the twice a month HeatSync Labs meet-up already pre-programmed.

[code:21f52tg5]/*
// The KEAL Show monthly event schedule ticker JavaScript
// Created by T&#46;R&#46;Keal January 26th 2010
// Released under the Gnu Public License 2&#46;0
//
// http&#58;//thekealshow&#46;com/
//
// Please review the Gnu Public License, Thank you&#46; 
// The GPL can be located online at http&#58;//www&#46;gnu&#46;org/copyleft/gpl&#46;html
*/

var event_offset=0;
var event_about=1;
var event_recur=2;
var event_start=3;
var event_duration=4;

var event_desc=0;
var event_location=1;
var event_week=0;
var event_day=1;
var event_hour=0;
var event_minute=1;

var event_days=
&#91;
	'Sunday',
	'Monday',
	'Tuesday',
	'Wednesday',
	'Thursday',
	'Friday',
	'Saturday'
&#93;

var event_weeks=
&#91;
	'1st',
	'2nd',
	'3rd',
	'4th',
	'5th'
&#93;

var event=
&#91;
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			4,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			-0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			2,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			4,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			3,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			4,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			4,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			4,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			5,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			4,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//heatsynclabs&#46;org/&quot;&gt;HeatSyncLabs&lt;/a&gt;&quot; Hackerspace Meet-Up',
			'&lt;a href=&quot;http&#58;//gangplankhq&#46;com/&quot;&gt;Gangplank&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			4
		&#93;,
		&#91;
			19,
			0
		&#93;,
		&#91;
			5,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//heatsynclabs&#46;org/&quot;&gt;HeatSyncLabs&lt;/a&gt;&quot; Hackerspace Meet-Up',
			'&lt;a href=&quot;http&#58;//gangplankhq&#46;com/&quot;&gt;Gangplank&lt;/a&gt;'
		&#93;,
		&#91;
			3,
			4
		&#93;,
		&#91;
			19,
			0
		&#93;,
		&#91;
			5,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//phx2600&#46;org/&quot;&gt;Phoenix 2600&lt;/a&gt;&quot; Hacker&amp;#39;s Quarterly Meet-Up',
			'&lt;a href=&quot;http&#58;//www&#46;unlimitedcoffee&#46;com/&quot;&gt;Unlimited Coffee&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			5
		&#93;,
		&#91;
			18,
			0
		&#93;,
		&#91;
			6,
			0
		&#93;
	&#93;
&#93;;
function rendertickerrecur(i)
{
	var week='Nth';
	var day='Caturday';
	var hour=0;
	var minute=0;
	var ampm='';
	if((event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;&gt;=1)&amp;&amp;(event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;&lt;=5))
	{
		week=event_weeks&#91;event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;-1&#93;;
	}
	else
	{
		week='Nth';
	}
	if((event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&gt;=0)&amp;&amp;(event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&lt;=6))
	{
		day=event_days&#91;event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&#93;;
	}
	else
	{
		day='Caturday';
	}
	hour=((event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;+11)%12)+1;
	minute=event&#91;i&#93;&#91;event_start&#93;&#91;event_minute&#93;;
	ampm=(event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;/12)%2;
	switch(ampm)
	{	
		case 0&#58;
		{
			ampm='am';
			break;
		}
		default&#58;
		{
			ampm='pm';
		}
	}
	if(minute===0)
	{
		return 'Every '+week+' '+day+' @ '+hour+ampm;
	}
	else
	{
		return 'Every '+week+' '+day+' @ '+hour+'&#58;'+('00'+minute)&#46;substr(('00'+minute)&#46;length-2,2)+ampm;
	}
}
function getUTCWeek(UTC)
{
	var tmp=new Date(UTC);
	var tmp2=new Date(UTC-((tmp&#46;getUTCDate()-1)*86400000));
	/*if(tmp&#46;getUTCDay()&lt;tmp2&#46;getUTCDay())
	{*/
		return Math&#46;floor((tmp&#46;getUTCDate()-1)/7)+1;
	/*}
	else
	{
		return Math&#46;floor((tmp&#46;getUTCDate()-1)/7);
	}*/
}
function rendertickerbar(spanUTC,skew,unit)
{
	var tmp=Math&#46;floor(spanUTC/skew)%unit;
	switch(tmp)
	{
	case 0&#58;
		return '&lt;tr&gt;&lt;td&gt;&lt;table width=&quot;100%&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td bgcolor=&quot;#000000&quot; height=&quot;4&quot;&gt;&lt;/td&gt;&lt;/body&gt;&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;';
		break;
	default&#58;
		return '&lt;tr&gt;&lt;td&gt;&lt;table width=&quot;100%&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td bgcolor=&quot;#00FF00&quot; width=&quot;'+(100*tmp/unit)+'%&quot; height=&quot;4&quot;&gt;&lt;/td&gt;&lt;td bgcolor=&quot;#000000&quot;&gt;&lt;/td&gt;&lt;/body&gt;&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;';
	}
}
function rendertickerunit(spanUTC,skew,unit,label)
{
	var tmp=Math&#46;floor(spanUTC/skew);
	if(unit&gt;=2)
	{
		tmp=tmp%unit;
	}
	switch(tmp)
	{
	case 0&#58;
		return '';
		break;
	default&#58;
		return '&lt;td align=&quot;right&quot; valign=&quot;top&quot;&gt;&amp;nbsp;'+tmp+label+'&lt;/td&gt;';
	}
}
function spantickerbars(spanUTC)
{
	var ret='';
	ret=ret+rendertickerbar(spanUTC,2419200000,12);
	ret=ret+rendertickerbar(spanUTC,604800000,4);
	ret=ret+rendertickerbar(spanUTC,86400000,7);
	ret=ret+rendertickerbar(spanUTC,3600000,24);
	ret=ret+rendertickerbar(spanUTC,60000,60);
	ret=ret+rendertickerbar(spanUTC,1000,60);
	ret='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot; width=&quot;256&quot;&gt;&lt;tbody&gt;'+ret+'&lt;/tbody&gt;&lt;/table&gt;';
	return ret;
}
function spantickerunits(spanUTC)
{
	var ret='';
	ret=ret+rendertickerunit(spanUTC,604800000,0,'wk');
	ret=ret+rendertickerunit(spanUTC,86400000,7,'d');
	ret=ret+rendertickerunit(spanUTC,3600000,24,'hr');
	ret=ret+rendertickerunit(spanUTC,60000,60,'min');
	ret=ret+rendertickerunit(spanUTC,1000,60,'sec');
	if(ret&#46;length===0)
	{
		return '&lt;td align=&quot;right&quot; valign=&quot;top&quot;&gt;&lt;tt&gt;0sec&lt;/tt&gt;&lt;/td&gt;';
	}
	ret='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tt&gt;'+ret+'&lt;/tt&gt;&lt;/tbody&gt;&lt;/table&gt;';
	return ret;
}
function ticker(i)
{
	var date=new Date();
	var now=date&#46;getTime();
	now+=(60000*(event&#91;i&#93;&#91;event_offset&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_offset&#93;&#91;event_hour&#93;)));
	var start=(now-(now%86400000)-32*86400000)+(60000*(event&#91;i&#93;&#91;event_start&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;)));
	for(var start2=new Date(start);start2&#46;getUTCDay()!=event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;;start2=new Date(start)) start-=86400000;
	var end=start+(60000*(event&#91;i&#93;&#91;event_duration&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_duration&#93;&#91;event_hour&#93;)));
	while((getUTCWeek(start)!=event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;)||((now&gt;end))){start+=7*86400000;end+=7*86400000;}
	var span=Math&#46;abs(start-now);
	if((now&gt;=start)&amp;&amp;(now&lt;=end))
	{
		return '&lt;font color=&quot;#00FF00&quot;&gt;In Progress&#58;&lt;/font&gt;&lt;br&gt;'+rendertickerrecur(i)+'&lt;br&gt;'+event&#91;i&#93;&#91;event_about&#93;&#91;event_desc&#93;+'&lt;br&gt;@ '+event&#91;i&#93;&#91;event_about&#93;&#91;event_location&#93;+'&lt;br&gt;&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerbars(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerunits(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;/tbody&gt;&lt;/table&gt;';
	}
	else if(now&lt;start)
	{
		return '&lt;font color=&quot;#00FF00&quot;&gt;Upcoming&#58;&lt;/font&gt;&lt;br&gt;'+rendertickerrecur(i)+'&lt;br&gt;'+event&#91;i&#93;&#91;event_about&#93;&#91;event_desc&#93;+'&lt;br&gt;@ '+event&#91;i&#93;&#91;event_about&#93;&#91;event_location&#93;+'&lt;br&gt;&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerbars(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerunits(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;/tbody&gt;&lt;/table&gt;';
	}
	else
	{
		return 'This event progress ticker has failed&#46; (Unknown scripting error)';
	}
}
function dispticker()
{
	var ret='';
	for(var i=0;i&lt;event&#46;length;i++)
	{
		ret=ret+'&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;&lt;b&gt;'+ticker(i)+'&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;&amp;nbsp;&lt;/td&gt;&lt;/tr&gt;';
	}
	document&#46;getElementById('ticker')&#46;innerHTML='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;'+ret+'&lt;/tbody&gt;&lt;/table&gt;';
	setTimeout('dispticker()',990);
}
dispticker();[/code:21f52tg5]

The script requires the following to be in the page HTML that uses it:
[code:21f52tg5]&lt;p id=&quot;ticker&quot;&gt;The &quot;TKS&quot; Monthly Ticker JavaScript has failed to load&#46;&lt;/p&gt;&lt;script language=&quot;JavaScript&quot; src=&quot;&#46;/js/tks-monthly-ticker&#46;js&quot;&gt;&lt;/script&gt;[/code:21f52tg5]

1. The &quot;p&quot; and &quot;/p&quot; tag can be any two matching tags that encloses an empty or error-message-containing plain HTML body.
2. The script must be loaded after the tag with id as &quot;ticker&quot; closes.
3. The script replaces all contents between the opening and closing of that tag on-the-fly every 990 milliseconds with clock render updates.
4. I have yet to include an event trigger in the script that pauses rendering refreshes during mouse-over and mouse-highlight events, which would be one of the only ways to be able to allow copying to clipboard otherwise.

Enjoy; I hope you find this script useful.
-- T.R.Keal

--------------------------------------------------------------------------------

Posted by **jargon** on Sat April 3rd, 2010 05:54:09 AM

[code:e5t3jq8m]
/*
// The KEAL Show monthly event schedule ticker JavaScript
// Created by T&#46;R&#46;Keal January 26th 2010
// Released under the Gnu Public License 2&#46;0
//
// http&#58;//thekealshow&#46;com/
//
// Please review the Gnu Public License, Thank you&#46; 
// The GPL can be located online at http&#58;//www&#46;gnu&#46;org/copyleft/gpl&#46;html
*/

var event_offset=0;
var event_about=1;
var event_recur=2;
var event_start=3;
var event_duration=4;

var event_desc=0;
var event_location=1;
var event_week=0;
var event_day=1;
var event_hour=0;
var event_minute=1;

var event_days=
&#91;
	'Sunday',
	'Monday',
	'Tuesday',
	'Wednesday',
	'Thursday',
	'Friday',
	'Saturday'
&#93;

var event_weeks=
&#91;
	'1st',
	'2nd',
	'3rd',
	'4th',
	'5th'
&#93;

var event=
&#91;
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			8,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			-0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			2,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			8,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			3,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			8,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			4,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			8,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;Supervillain Sunday&quot;',
			'&lt;a href=&quot;http&#58;//rev-radio&#46;com/&quot;&gt;Revolutions Radio&lt;/a&gt;'
		&#93;,
		&#91;
			5,
			0
		&#93;,
		&#91;
			22,
			0
		&#93;,
		&#91;
			8,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//heatsynclabs&#46;org/&quot;&gt;HeatSyncLabs&lt;/a&gt;&quot; Hackerspace Meet-Up',
			'&lt;a href=&quot;http&#58;//gangplankhq&#46;com/&quot;&gt;Gangplank&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			4
		&#93;,
		&#91;
			19,
			0
		&#93;,
		&#91;
			5,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//heatsynclabs&#46;org/&quot;&gt;HeatSyncLabs&lt;/a&gt;&quot; Hackerspace Meet-Up',
			'&lt;a href=&quot;http&#58;//gangplankhq&#46;com/&quot;&gt;Gangplank&lt;/a&gt;'
		&#93;,
		&#91;
			3,
			4
		&#93;,
		&#91;
			19,
			0
		&#93;,
		&#91;
			5,
			0
		&#93;
	&#93;,
	&#91;
		&#91;
			-7,
			0
		&#93;,
		&#91;
			'&quot;&lt;a href=&quot;http&#58;//phx2600&#46;org/&quot;&gt;Phoenix 2600&lt;/a&gt;&quot; Hacker&amp;#39;s Quarterly Meet-Up',
			'&lt;a href=&quot;http&#58;//www&#46;unlimitedcoffee&#46;com/&quot;&gt;Unlimited Coffee&lt;/a&gt;'
		&#93;,
		&#91;
			1,
			5
		&#93;,
		&#91;
			18,
			0
		&#93;,
		&#91;
			6,
			0
		&#93;
	&#93;
&#93;;
function rendertickerrecur(i)
{
	var week='Nth';
	var day='Caturday';
	var hour=0;
	var minute=0;
	var ampm='';
	if((event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;&gt;=1)&amp;&amp;(event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;&lt;=5))
	{
		week=event_weeks&#91;event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;-1&#93;;
	}
	else
	{
		week='Nth';
	}
	if((event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&gt;=0)&amp;&amp;(event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&lt;=6))
	{
		day=event_days&#91;event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;&#93;;
	}
	else
	{
		day='Caturday';
	}
	hour=((event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;+11)%12)+1;
	minute=event&#91;i&#93;&#91;event_start&#93;&#91;event_minute&#93;;
	ampm=(event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;/12)%2;
	switch(ampm)
	{	
		case 0&#58;
		{
			ampm='am';
			break;
		}
		default&#58;
		{
			ampm='pm';
		}
	}
	if(minute===0)
	{
		return 'Every '+week+' '+day+' @ '+hour+ampm;
	}
	else
	{
		return 'Every '+week+' '+day+' @ '+hour+'&#58;'+('00'+minute)&#46;substr(('00'+minute)&#46;length-2,2)+ampm;
	}
}
function getUTCWeek(UTC)
{
	var tmp=new Date(UTC);
	var tmp2=new Date(UTC-((tmp&#46;getUTCDate()-1)*86400000));
	return Math&#46;floor((tmp&#46;getUTCDate()-1)/7)+1;
}
function rendertickerbar(spanUTC,skew,unit)
{
	var tmp=Math&#46;floor(spanUTC/skew)%unit;
	switch(tmp)
	{
	case 0&#58;
		return '&lt;tr&gt;&lt;td&gt;&lt;table width=&quot;100%&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td bgcolor=&quot;#000000&quot; height=&quot;4&quot;&gt;&lt;/td&gt;&lt;/body&gt;&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;';
		break;
	default&#58;
		return '&lt;tr&gt;&lt;td&gt;&lt;table width=&quot;100%&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td bgcolor=&quot;#00FF00&quot; width=&quot;'+(100*tmp/unit)+'%&quot; height=&quot;4&quot;&gt;&lt;/td&gt;&lt;td bgcolor=&quot;#000000&quot;&gt;&lt;/td&gt;&lt;/body&gt;&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;';
	}
}
function rendertickerunit(spanUTC,skew,unit,label)
{
	var tmp=Math&#46;floor(spanUTC/skew);
	if(unit&gt;=2)
	{
		tmp=tmp%unit;
	}
	switch(tmp)
	{
	case 0&#58;
		return '';
		break;
	default&#58;
		return '&lt;td align=&quot;right&quot; valign=&quot;top&quot;&gt;&amp;nbsp;'+tmp+label+'&lt;/td&gt;';
	}
}
function spantickerbars(spanUTC)
{
	var ret='';
	ret=ret+rendertickerbar(spanUTC,2419200000,12);
	ret=ret+rendertickerbar(spanUTC,604800000,4);
	ret=ret+rendertickerbar(spanUTC,86400000,7);
	ret=ret+rendertickerbar(spanUTC,3600000,24);
	ret=ret+rendertickerbar(spanUTC,60000,60);
	ret=ret+rendertickerbar(spanUTC,1000,60);
	ret='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot; width=&quot;256&quot;&gt;&lt;tbody&gt;'+ret+'&lt;/tbody&gt;&lt;/table&gt;';
	return ret;
}
function spantickerunits(spanUTC)
{
	var ret='';
	ret=ret+rendertickerunit(spanUTC,604800000,0,'wk');
	ret=ret+rendertickerunit(spanUTC,86400000,7,'d');
	ret=ret+rendertickerunit(spanUTC,3600000,24,'hr');
	ret=ret+rendertickerunit(spanUTC,60000,60,'min');
	ret=ret+rendertickerunit(spanUTC,1000,60,'sec');
	if(ret&#46;length===0)
	{
		return '&lt;td align=&quot;right&quot; valign=&quot;top&quot;&gt;&lt;tt&gt;0sec&lt;/tt&gt;&lt;/td&gt;';
	}
	ret='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tt&gt;'+ret+'&lt;/tt&gt;&lt;/tbody&gt;&lt;/table&gt;';
	return ret;
}
function ticker(i)
{
	var date=new Date();
	var now=date&#46;getTime();
	now+=(60000*(event&#91;i&#93;&#91;event_offset&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_offset&#93;&#91;event_hour&#93;)));
	var start=(now-(now%86400000)-32*86400000)+(60000*(event&#91;i&#93;&#91;event_start&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_start&#93;&#91;event_hour&#93;)));
	for(var start2=new Date(start);start2&#46;getUTCDay()!=event&#91;i&#93;&#91;event_recur&#93;&#91;event_day&#93;;start2=new Date(start)) start-=86400000;
	var end=start+(60000*(event&#91;i&#93;&#91;event_duration&#93;&#91;event_minute&#93;+(60*event&#91;i&#93;&#91;event_duration&#93;&#91;event_hour&#93;)));
	while((getUTCWeek(start)!=event&#91;i&#93;&#91;event_recur&#93;&#91;event_week&#93;)||((now&gt;end))){start+=7*86400000;end+=7*86400000;}
	var span=Math&#46;abs(start-now);
	if((now&gt;=start)&amp;&amp;(now&lt;=end))
	{
		return '&lt;font color=&quot;#00FF00&quot;&gt;In Progress&#58;&lt;/font&gt;&lt;br&gt;'+rendertickerrecur(i)+'&lt;br&gt;'+event&#91;i&#93;&#91;event_about&#93;&#91;event_desc&#93;+'&lt;br&gt;@ '+event&#91;i&#93;&#91;event_about&#93;&#91;event_location&#93;+'&lt;br&gt;&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerbars(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerunits(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;/tbody&gt;&lt;/table&gt;';
	}
	else if(now&lt;start)
	{
		return '&lt;font color=&quot;#00FF00&quot;&gt;Upcoming&#58;&lt;/font&gt;&lt;br&gt;'+rendertickerrecur(i)+'&lt;br&gt;'+event&#91;i&#93;&#91;event_about&#93;&#91;event_desc&#93;+'&lt;br&gt;@ '+event&#91;i&#93;&#91;event_about&#93;&#91;event_location&#93;+'&lt;br&gt;&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerbars(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;'+spantickerunits(span)+'&lt;/td&gt;&lt;/tr&gt;&lt;/tbody&gt;&lt;/table&gt;';
	}
	else
	{
		return 'This event progress ticker has failed&#46; (Unknown scripting error)';
	}
}
function dispticker()
{
	var ret='';
	for(var i=0;i&lt;event&#46;length;i++)
	{
		ret=ret+'&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;&lt;b&gt;'+ticker(i)+'&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=&quot;center&quot; valign=&quot;top&quot;&gt;&amp;nbsp;&lt;/td&gt;&lt;/tr&gt;';
	}
	document&#46;getElementById('ticker')&#46;innerHTML='&lt;table cellspacing=&quot;0&quot; cellpadding=&quot;0&quot; border=&quot;0&quot;&gt;&lt;tbody&gt;'+ret+'&lt;/tbody&gt;&lt;/table&gt;';
	setTimeout('dispticker()',990);
}
dispticker();
[/code:e5t3jq8m]
