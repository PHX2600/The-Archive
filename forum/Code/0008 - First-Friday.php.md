## First-Friday.php
Posted by **PHLAK** on Sat December 29th, 2007 11:09:24 PM

A little php I smashed together from misc. code, modified, and threw in some of
my own tricks, that will generate the first Friday of next month for you.

**UPDATE: Latest revision available on Github: <https://github.com/PHX2600/FirstFriday>**

--------------------------------------------------------------------------------

Posted by **Konshu** on Sun December 30th, 2007 09:11:15 PM

Clever little add-in for the front page of the site to keep the information up-
to-date automatically.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun December 30th, 2007 11:51:26 PM

I'm an automation addict!  I hate having to update things, even on a monthly
basis.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue January 1st, 2008 01:35:36 AM

UH-OH!  The code is flawed... if you take a look, it's showing February 1st as
the next meeting even though the next meeting is this Friday (January 4th).  If
anyone can, please take a look at the code and let me know if you see the
problem.  I'm pretty sure all we need to do is check to see if the first Friday
of this month has already occurred, and if not, set that here:

	//Next Month//
    if($t[mon]=="12"){
    	$nm='1-'.($t[year]+1);
    }
    else {
    	$nm=($t[mon]+1).'-'.$t[year];
    }

I'm skiing until Thursday night, but will hopefully have time to check up on it
while I'm not skiing.  Thanks guys!

NOTE: I have removed some unneeded code in the original post to simplify.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue January 1st, 2008 01:03:29 PM

I think I found a solution.  This way it checks if the day of the month is <=7,
and the weekday is before Friday.  In the event it is, it will find the first
friday of the current month, rather than next month.


	//Calculate Next Month//
	if($t[mon]=='12'){
	  $nm='1-'.($t[year]+1);
	}
	if($t[mday]<='7' && $t[wday]<='5') {
		$nm=($t[mon]).'-'.$t[year];
	}
	else {
		$nm=($t[mon]+1).'-'.$t[year];
	}


--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun January 6th, 2008 01:39:55 PM

Code revised, it was calculating last Friday's date.

Added the following code:

	if ($t[mon] == date('m',$date) && $t[mday] > date('j',$date) && $t[mon] == '12') {
		$nm = '1-'.($t[year]+1);
		$ff = get_day("first", "friday", $nm);
	}
	if ($t[mon] == date('m',$date) && $t[mday] > date('j',$date) && $t[mon] != '12') {
		$nm = ($t[mon]+1).'-'.$t[year];
		$ff = get_day("first", "friday", $nm);
	}
	else {
		$ff = $date;
	}


--------------------------------------------------------------------------------

Posted by **PHLAK** on Sat February 14th, 2009 08:10:19 PM

Just finished a total overhaul of the code.  I learned some new tricks
(specifically the mktime function) and was able to significantly reduce the code
and simplify it.  Check it out:

	<?php // first-friday.php v0.1.3 by, Chris Kankiewicz <http://www.web-geek.net>

	  // Calculate next Friday
	  for ($x = date('d'); $x <= (date('d') + 6); $x++) {
	    $timeStamp = mktime(0,0,0,date('m'),$x,date('Y'));
	    if (date('w',$timeStamp) == 5) {
	      $nextFriday = mktime(0,0,0,date('m'),$x,date('Y'));
	    }
	  }
	  // Check if next Friday is the first friday of the month.
	  if (date('d', $nextFriday) <= 7) {
	    $firstFriday = $nextFriday;
	  } else {
	  // Calculate first Friday of next month
	    for ($x = 1; $x <= 7; $x++) {
	      $timeStamp = mktime(0,0,0,date('m')+1,$x,date('Y'));
	      if (date('w',$timeStamp) == 5) {
	        $firstFriday = mktime(0,0,0,date('m')+1,$x,date('Y'));
	      }
	    }
	  }

	  // Echo next first Friday
	  echo date("F j, Y", $firstFriday);

	?>

--------------------------------------------------------------------------------

Posted by **jargon** on Sun December 27th, 2009 06:13:00 AM

Pwned by JavaScript.

The following is 100% my own code from scratch that I released under the Gnu
Public License 2.0.

Demo at foot of every page: <http://phx2600.retromachineshop.com/>

JavaScript code: ("monthly-ticker.js")

	// The KEAL Show monthly event schedule ticker JavaScript
	// Created by T.R.Keal December 27th 2009
	// Released under the Gnu Public License 2.0
	//
	// http://thekealshow.com/
	//
	// Please review the Gnu Public License, Thank you.
	// The GPL can be located online at http://www.gnu.org/copyleft/gpl.html
	*/

	/* event schedule variables */
	var eventAdjustHours=-7;     /* timezone hour offset, valid for -23 through 23 */
	var eventAdjustMinutes=0;    /* timezone minute offset, valid for 0 through 59 */
	var eventGroupName='monthly Phoenix&#044; Arizona meetup for &quot;2600: The Hacker&#039;s Quarterly Magazine&quot;'; /* must use proper html escapes */
	var eventLocationDesc='Gameworks Tempe &#064; Arizona Mills Mall'; /* must use proper html escapes */
	var eventStartWeek=1;        /* Is actually Nth ocurrance of eventStartDay in month, valid for 1 through 5. */
	var eventStartDay=6;         /* valid for 0 through 6 (0=Sunday, 1=Monday, 2=Tuesday, 3=Wednesday, 4=Thursday, 5=Friday, 6=Saturday) */
	var eventStartHours=18;      /* valid for 0 through 23 */
	var eventStartMinutes=0;     /* valid for 0 through 59 */
	var eventEndDay=7;           /* valid for 0 through 6 (0=Sunday, 1=Monday, 2=Tuesday, 3=Wednesday, 4=Thursday, 5=Friday, 6=Saturday) */
	var eventEndHours=0;         /* valid for 0 through 23 */
	var eventEndMinutes=0;       /* valid for 0 through 59 */

	/* presence calculation variables */
	var nowUTC=new Date();
	var nowDate=nowUTC.getUTCDate();
	var nowWeek=getUTCWeek(nowUTC);
	var nowDay=nowUTC.getUTCDay();
	var nowHours=nowUTC.getUTCHours();
	var nowMinutes=nowUTC.getUTCMinutes();
	var nowSeconds=nowUTC.getUTCSeconds();
	var nowMilliseconds=nowUTC.getUTCMilliseconds();

	/* synchronization calculation variables */
	var nowZero=nowUTC-(nowMilliseconds+1000*(nowSeconds+60*(nowMinutes+60*(nowHours+24*nowDay))));
	var eventStartUTC=nowZero+60000*(eventStartMinutes-eventAdjustMinutes+60*(eventStartHours-eventAdjustHours+24*eventStartDay));
	var eventEndUTC=nowZero+60000*(eventEndMinutes-eventAdjustMinutes+60*(eventEndHours-eventAdjustHours+24*eventEndDay));

	/* align week */
	if((eventStartDay>eventEndDay)&&((nowDay>=eventStartDay)||(nowDay<=eventEndDay)))
	{
		eventStartUTC-=86400000*7;
	}
	while(eventEndUTC<eventStartUTC)
	{
		eventEndUTC+=86400000*7;
	}
	while((eventStartUTC<nowUTC)&&(eventEndUTC<nowUTC))
	{
		eventStartUTC+=86400000*7;
	}
	while(eventEndUTC<eventStartUTC)
	{
		eventEndUTC+=86400000*7;fs
	}

	/* align month */
	while((getUTCWeek(eventStartUTC)!=eventStartWeek)&&(eventStartWeek>=1)&&(eventStartWeek<=5))
	{
		eventStartUTC+=86400000*7;
		eventEndUTC+=86400000*7;
	}

	function getUTCWeek(UTC)
	{
		var tmp=new Date(UTC);
		var tmp2=((tmp.getUTCDate()-tmp.getUTCDay()+7)%7)
		return Math.floor((tmp.getUTCDate()+tmp2-1)/7)+1;
	}

	function spanticker(spanUTC)
	{
		var ret='';
		var tmp=0;
		tmp=Math.floor(spanUTC/(7*86400000));
		if(tmp>0)
		{
			ret=ret+tmp+'wk ';
		}
		tmp=Math.floor(spanUTC/86400000)%7;
		if(tmp>0)
		{
			ret=ret+tmp+'d ';
		}
		tmp=Math.floor(spanUTC/Math.floor(86400000/24))%24;
		if(tmp>0)
		{
			ret=ret+tmp+'hr ';
		}
		tmp=Math.floor(spanUTC/Math.floor(86400000/(24*60)))%60;
		if(tmp>0)
		{
			ret=ret+tmp+'min ';
		}
		tmp=Math.floor(spanUTC/Math.floor(86400000/(24*60*60)))%60;
		if(tmp>0)
		{
			ret=ret+tmp+'sec ';
		}
		if(ret.substr(ret.length-1,1)==' ')
		{
			ret=ret.substr(0,ret.length-1);
		}
		if(ret=='')
		{
			ret='0sec';
		}
		return ret;
	}

	function ticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc)
	{
		while((getUTCWeek(eventStartUTC)!=eventStartWeek)&&(eventStartWeek>=1)&&(eventStartWeek<=5))
		{
			eventStartUTC+=86400000*7;
			eventEndUTC+=86400000*7;
		}
		var nowUTC=new Date();
		while((nowUTC>eventStartUTC)&&(nowUTC>eventEndUTC))
		{
			eventStartUTC+=86400000*7;
			eventEndUTC+=86400000*7;
		}
		var spanUTC=Math.abs(eventStartUTC-nowUTC);
		if((nowUTC>=eventStartUTC)&&(nowUTC<=eventEndUTC))
		{
			return 'The current '+eventGroupName+' event at '+eventLocationDesc+' has been in progress '+spanticker(spanUTC)+' of '+spanticker(eventEndUTC-eventStartUTC)+'.';
		}
		else if(nowUTC<eventStartUTC)
		{
			return 'The next '+spanticker(eventEndUTC-eventStartUTC)+' in duration '+eventGroupName+' at '+eventLocationDesc+' will start in '+spanticker(spanUTC)+'.';
		}
		else
		{
			return 'The event progress ticker has failed. (Unknown scripting error)';
		}
	}

	function dispticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc)
	{
		document.getElementById('ticker').innerHTML=ticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc);
		setTimeout('dispticker('+eventStartWeek+','+eventStartUTC+','+eventEndUTC+',\''+eventGroupName+'\',\''+eventLocationDesc+'\')',990);
	}

	/* begin ticker */
	dispticker(eventStartWeek,eventStartUTC,eventEndUTC,eventGroupName,eventLocationDesc);

HTML code for calling script properly: (notice the JavaScript include comes
*after* the "<h3>" with id="ticker"!)

	<h3 id="ticker">The monthly event ticker javascript has failed.</h3>
	<script language="JavaScript" src="./js/monthly-ticker.js"></script>

--------------------------------------------------------------------------------

Posted by **jargon** on Thu January 28th, 2010 01:59:04 AM

There was a glitch due to converting from local time to UTC instead of from UTC
to "local" UTC. (Same millisecond of day for same day that UTC offset would
have.)

Here is the latest version of the script which includes clock render with the 5
weekly The KEAL Show "Supervillain Sunday" airtimes per month, the phx2600 meet-
up, and the twice a month HeatSync Labs meet-up already pre-programmed.

	/*
	// The KEAL Show monthly event schedule ticker JavaScript
	// Created by T.R.Keal January 26th 2010
	// Released under the Gnu Public License 2.0
	//
	// http://thekealshow.com/
	//
	// Please review the Gnu Public License, Thank you.
	// The GPL can be located online at http://www.gnu.org/copyleft/gpl.html
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
	[
		'Sunday',
		'Monday',
		'Tuesday',
		'Wednesday',
		'Thursday',
		'Friday',
		'Saturday'
	]

	var event_weeks=
	[
		'1st',
		'2nd',
		'3rd',
		'4th',
		'5th'
	]

	var event=
	[
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				1,
				0
			],
			[
				22,
				0
			],
			[
				4,
				0
			]
		],
		[
			[
				-7,
				-0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				2,
				0
			],
			[
				22,
				0
			],
			[
				4,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				3,
				0
			],
			[
				22,
				0
			],
			[
				4,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				4,
				0
			],
			[
				22,
				0
			],
			[
				4,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				5,
				0
			],
			[
				22,
				0
			],
			[
				4,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://heatsynclabs.org/">HeatSyncLabs</a>" Hackerspace Meet-Up',
				'<a href="http://gangplankhq.com/">Gangplank</a>'
			],
			[
				1,
				4
			],
			[
				19,
				0
			],
			[
				5,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://heatsynclabs.org/">HeatSyncLabs</a>" Hackerspace Meet-Up',
				'<a href="http://gangplankhq.com/">Gangplank</a>'
			],
			[
				3,
				4
			],
			[
				19,
				0
			],
			[
				5,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://phx2600.org/">Phoenix 2600</a>" Hacker&#39;s Quarterly Meet-Up',
				'<a href="http://www.unlimitedcoffee.com/">Unlimited Coffee</a>'
			],
			[
				1,
				5
			],
			[
				18,
				0
			],
			[
				6,
				0
			]
		]
	];
	function rendertickerrecur(i)
	{
		var week='Nth';
		var day='Caturday';
		var hour=0;
		var minute=0;
		var ampm='';
		if((event[i][event_recur][event_week]>=1)&&(event[i][event_recur][event_week]<=5))
		{
			week=event_weeks[event[i][event_recur][event_week]-1];
		}
		else
		{
			week='Nth';
		}
		if((event[i][event_recur][event_day]>=0)&&(event[i][event_recur][event_day]<=6))
		{
			day=event_days[event[i][event_recur][event_day]];
		}
		else
		{
			day='Caturday';
		}
		hour=((event[i][event_start][event_hour]+11)%12)+1;
		minute=event[i][event_start][event_minute];
		ampm=(event[i][event_start][event_hour]/12)%2;
		switch(ampm)
		{
			case 0:
			{
				ampm='am';
				break;
			}
			default:
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
			return 'Every '+week+' '+day+' @ '+hour+':'+('00'+minute).substr(('00'+minute).length-2,2)+ampm;
		}
	}
	function getUTCWeek(UTC)
	{
		var tmp=new Date(UTC);
		var tmp2=new Date(UTC-((tmp.getUTCDate()-1)*86400000));
		/*if(tmp.getUTCDay()<tmp2.getUTCDay())
		{*/
			return Math.floor((tmp.getUTCDate()-1)/7)+1;
		/*}
		else
		{
			return Math.floor((tmp.getUTCDate()-1)/7);
		}*/
	}
	function rendertickerbar(spanUTC,skew,unit)
	{
		var tmp=Math.floor(spanUTC/skew)%unit;
		switch(tmp)
		{
		case 0:
			return '<tr><td><table width="100%"><tbody><tr><td bgcolor="#000000" height="4"></td></body></table></td></tr>';
			break;
		default:
			return '<tr><td><table width="100%"><tbody><tr><td bgcolor="#00FF00" width="'+(100*tmp/unit)+'%" height="4"></td><td bgcolor="#000000"></td></body></table></td></tr>';
		}
	}
	function rendertickerunit(spanUTC,skew,unit,label)
	{
		var tmp=Math.floor(spanUTC/skew);
		if(unit>=2)
		{
			tmp=tmp%unit;
		}
		switch(tmp)
		{
		case 0:
			return '';
			break;
		default:
			return '<td align="right" valign="top">&nbsp;'+tmp+label+'</td>';
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
		ret='<table cellspacing="0" cellpadding="0" border="0" width="256"><tbody>'+ret+'</tbody></table>';
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
		if(ret.length===0)
		{
			return '<td align="right" valign="top"><tt>0sec</tt></td>';
		}
		ret='<table cellspacing="0" cellpadding="0" border="0"><tbody><tt>'+ret+'</tt></tbody></table>';
		return ret;
	}
	function ticker(i)
	{
		var date=new Date();
		var now=date.getTime();
		now+=(60000*(event[i][event_offset][event_minute]+(60*event[i][event_offset][event_hour])));
		var start=(now-(now%86400000)-32*86400000)+(60000*(event[i][event_start][event_minute]+(60*event[i][event_start][event_hour])));
		for(var start2=new Date(start);start2.getUTCDay()!=event[i][event_recur][event_day];start2=new Date(start)) start-=86400000;
		var end=start+(60000*(event[i][event_duration][event_minute]+(60*event[i][event_duration][event_hour])));
		while((getUTCWeek(start)!=event[i][event_recur][event_week])||((now>end))){start+=7*86400000;end+=7*86400000;}
		var span=Math.abs(start-now);
		if((now>=start)&&(now<=end))
		{
			return '<font color="#00FF00">In Progress:</font><br>'+rendertickerrecur(i)+'<br>'+event[i][event_about][event_desc]+'<br>@ '+event[i][event_about][event_location]+'<br><table cellspacing="0" cellpadding="0" border="0"><tbody><tr><td align="center" valign="top">'+spantickerbars(span)+'</td></tr><tr><td align="center" valign="top">'+spantickerunits(span)+'</td></tr></tbody></table>';
		}
		else if(now<start)
		{
			return '<font color="#00FF00">Upcoming:</font><br>'+rendertickerrecur(i)+'<br>'+event[i][event_about][event_desc]+'<br>@ '+event[i][event_about][event_location]+'<br><table cellspacing="0" cellpadding="0" border="0"><tbody><tr><td align="center" valign="top">'+spantickerbars(span)+'</td></tr><tr><td align="center" valign="top">'+spantickerunits(span)+'</td></tr></tbody></table>';
		}
		else
		{
			return 'This event progress ticker has failed. (Unknown scripting error)';
		}
	}
	function dispticker()
	{
		var ret='';
		for(var i=0;i<event.length;i++)
		{
			ret=ret+'<tr><td align="center" valign="top"><b>'+ticker(i)+'</b></td></tr><tr><td align="center" valign="top">&nbsp;</td></tr>';
		}
		document.getElementById('ticker').innerHTML='<table cellspacing="0" cellpadding="0" border="0"><tbody>'+ret+'</tbody></table>';
		setTimeout('dispticker()',990);
	}
	dispticker();

The script requires the following to be in the page HTML that uses it:

	<p id="ticker">The "TKS" Monthly Ticker JavaScript has failed to load.</p><script language="JavaScript" src="./js/tks-monthly-ticker.js"></script>

  1. The "p" and "/p" tag can be any two matching tags that encloses an empty or error-message-containing plain HTML body.
  2. The script must be loaded after the tag with id as "ticker" closes.
  3. The script replaces all contents between the opening and closing of that tag on-the-fly every 990 milliseconds with clock render updates.
  4. I have yet to include an event trigger in the script that pauses rendering refreshes during mouse-over and mouse-highlight events, which would be one of the only ways to be able to allow copying to clipboard otherwise.

Enjoy; I hope you find this script useful.
-- T.R.Keal

--------------------------------------------------------------------------------

Posted by **jargon** on Sat April 3rd, 2010 05:54:09 AM

	/*
	// The KEAL Show monthly event schedule ticker JavaScript
	// Created by T.R.Keal January 26th 2010
	// Released under the Gnu Public License 2.0
	//
	// http://thekealshow.com/
	//
	// Please review the Gnu Public License, Thank you.
	// The GPL can be located online at http://www.gnu.org/copyleft/gpl.html
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
	[
		'Sunday',
		'Monday',
		'Tuesday',
		'Wednesday',
		'Thursday',
		'Friday',
		'Saturday'
	]

	var event_weeks=
	[
		'1st',
		'2nd',
		'3rd',
		'4th',
		'5th'
	]

	var event=
	[
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				1,
				0
			],
			[
				22,
				0
			],
			[
				8,
				0
			]
		],
		[
			[
				-7,
				-0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				2,
				0
			],
			[
				22,
				0
			],
			[
				8,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				3,
				0
			],
			[
				22,
				0
			],
			[
				8,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				4,
				0
			],
			[
				22,
				0
			],
			[
				8,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"Supervillain Sunday"',
				'<a href="http://rev-radio.com/">Revolutions Radio</a>'
			],
			[
				5,
				0
			],
			[
				22,
				0
			],
			[
				8,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://heatsynclabs.org/">HeatSyncLabs</a>" Hackerspace Meet-Up',
				'<a href="http://gangplankhq.com/">Gangplank</a>'
			],
			[
				1,
				4
			],
			[
				19,
				0
			],
			[
				5,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://heatsynclabs.org/">HeatSyncLabs</a>" Hackerspace Meet-Up',
				'<a href="http://gangplankhq.com/">Gangplank</a>'
			],
			[
				3,
				4
			],
			[
				19,
				0
			],
			[
				5,
				0
			]
		],
		[
			[
				-7,
				0
			],
			[
				'"<a href="http://phx2600.org/">Phoenix 2600</a>" Hacker&#39;s Quarterly Meet-Up',
				'<a href="http://www.unlimitedcoffee.com/">Unlimited Coffee</a>'
			],
			[
				1,
				5
			],
			[
				18,
				0
			],
			[
				6,
				0
			]
		]
	];
	function rendertickerrecur(i)
	{
		var week='Nth';
		var day='Caturday';
		var hour=0;
		var minute=0;
		var ampm='';
		if((event[i][event_recur][event_week]>=1)&&(event[i][event_recur][event_week]<=5))
		{
			week=event_weeks[event[i][event_recur][event_week]-1];
		}
		else
		{
			week='Nth';
		}
		if((event[i][event_recur][event_day]>=0)&&(event[i][event_recur][event_day]<=6))
		{
			day=event_days[event[i][event_recur][event_day]];
		}
		else
		{
			day='Caturday';
		}
		hour=((event[i][event_start][event_hour]+11)%12)+1;
		minute=event[i][event_start][event_minute];
		ampm=(event[i][event_start][event_hour]/12)%2;
		switch(ampm)
		{
			case 0:
			{
				ampm='am';
				break;
			}
			default:
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
			return 'Every '+week+' '+day+' @ '+hour+':'+('00'+minute).substr(('00'+minute).length-2,2)+ampm;
		}
	}
	function getUTCWeek(UTC)
	{
		var tmp=new Date(UTC);
		var tmp2=new Date(UTC-((tmp.getUTCDate()-1)*86400000));
		return Math.floor((tmp.getUTCDate()-1)/7)+1;
	}
	function rendertickerbar(spanUTC,skew,unit)
	{
		var tmp=Math.floor(spanUTC/skew)%unit;
		switch(tmp)
		{
		case 0:
			return '<tr><td><table width="100%"><tbody><tr><td bgcolor="#000000" height="4"></td></body></table></td></tr>';
			break;
		default:
			return '<tr><td><table width="100%"><tbody><tr><td bgcolor="#00FF00" width="'+(100*tmp/unit)+'%" height="4"></td><td bgcolor="#000000"></td></body></table></td></tr>';
		}
	}
	function rendertickerunit(spanUTC,skew,unit,label)
	{
		var tmp=Math.floor(spanUTC/skew);
		if(unit>=2)
		{
			tmp=tmp%unit;
		}
		switch(tmp)
		{
		case 0:
			return '';
			break;
		default:
			return '<td align="right" valign="top">&nbsp;'+tmp+label+'</td>';
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
		ret='<table cellspacing="0" cellpadding="0" border="0" width="256"><tbody>'+ret+'</tbody></table>';
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
		if(ret.length===0)
		{
			return '<td align="right" valign="top"><tt>0sec</tt></td>';
		}
		ret='<table cellspacing="0" cellpadding="0" border="0"><tbody><tt>'+ret+'</tt></tbody></table>';
		return ret;
	}
	function ticker(i)
	{
		var date=new Date();
		var now=date.getTime();
		now+=(60000*(event[i][event_offset][event_minute]+(60*event[i][event_offset][event_hour])));
		var start=(now-(now%86400000)-32*86400000)+(60000*(event[i][event_start][event_minute]+(60*event[i][event_start][event_hour])));
		for(var start2=new Date(start);start2.getUTCDay()!=event[i][event_recur][event_day];start2=new Date(start)) start-=86400000;
		var end=start+(60000*(event[i][event_duration][event_minute]+(60*event[i][event_duration][event_hour])));
		while((getUTCWeek(start)!=event[i][event_recur][event_week])||((now>end))){start+=7*86400000;end+=7*86400000;}
		var span=Math.abs(start-now);
		if((now>=start)&&(now<=end))
		{
			return '<font color="#00FF00">In Progress:</font><br>'+rendertickerrecur(i)+'<br>'+event[i][event_about][event_desc]+'<br>@ '+event[i][event_about][event_location]+'<br><table cellspacing="0" cellpadding="0" border="0"><tbody><tr><td align="center" valign="top">'+spantickerbars(span)+'</td></tr><tr><td align="center" valign="top">'+spantickerunits(span)+'</td></tr></tbody></table>';
		}
		else if(now<start)
		{
			return '<font color="#00FF00">Upcoming:</font><br>'+rendertickerrecur(i)+'<br>'+event[i][event_about][event_desc]+'<br>@ '+event[i][event_about][event_location]+'<br><table cellspacing="0" cellpadding="0" border="0"><tbody><tr><td align="center" valign="top">'+spantickerbars(span)+'</td></tr><tr><td align="center" valign="top">'+spantickerunits(span)+'</td></tr></tbody></table>';
		}
		else
		{
			return 'This event progress ticker has failed. (Unknown scripting error)';
		}
	}
	function dispticker()
	{
		var ret='';
		for(var i=0;i<event.length;i++)
		{
			ret=ret+'<tr><td align="center" valign="top"><b>'+ticker(i)+'</b></td></tr><tr><td align="center" valign="top">&nbsp;</td></tr>';
		}
		document.getElementById('ticker').innerHTML='<table cellspacing="0" cellpadding="0" border="0"><tbody>'+ret+'</tbody></table>';
		setTimeout('dispticker()',990);
	}
	dispticker();
