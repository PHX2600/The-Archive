## &quot;2600 Meetings Table&quot; proxy PHP script
Posted by **jargon** on Tue December 29th, 2009 04:29:39 PM

I wrote this last night, and removed dependencies etc along with adding the Gnu Public License 2.0 comments this afternoon.

This PHP script acts as a proxy for viewing the 2600.com meetings list page in a uniform table rather than in its original slightly chaotic plain/text formatting. It simply downloads <http&#58;//2600&#46;com/meetings/mtg&#46;html>, then reformats the downloaded page and dumps it into the browser as a nice clean HTML table.

The 6 columns in the table are:
1. country
2. state
3. city
4. description of meeting
5. time of meeting
6. payphone direct inward dials

Notice the script is smart enough to not put a time for the Arlington meeting due to being a redirect, automatically enters &quot;5 pm&quot; for all undesignated times, and automatically removes extraneous trailing periods from times listed in the table.

Anyone is free to use this script unrestricted; However, I advise websites of meetings to not use this script to dictate solely their own meeting information due to the nature of feedback loops.

[code:wydeps3t]&lt;?php
/*
// &quot;2600 Meetings Table&quot; http&#58;//2600&#46;com/meetings/mtg&#46;html proxy PHP script
// Created by T&#46;R&#46;Keal December 29th 2009
// Released under the Gnu Public License 2&#46;0
//
// http&#58;//thekealshow&#46;com/
//
// Please review the Gnu Public License, Thank you&#46; 
// The GPL can be located online at http&#58;//www&#46;gnu&#46;org/copyleft/gpl&#46;html
*/
$mtg=file_get_contents('http&#58;//www&#46;2600&#46;com/meetings/mtg&#46;html');
$mtg=substr($mtg,strpos($mtg,'&lt;PRE&gt;'));
$mtg=str_replace(&quot;\r\n&quot;,&quot;\n&quot;,$mtg);
$ln=explode(&quot;\n&quot;,$mtg);
$k=null;
$k&#91;'country'&#93;='';
$k&#91;'state'&#93;='';
$k&#91;'city'&#93;='';
$k&#91;'desc'&#93;='';
$k&#91;'time'&#93;='';
$m=null;
$m&#91;'ct'&#93;=0;
foreach($ln as $i =&gt; $v)
{
	if(strlen($ln&#91;$i&#93;)&gt;0)
	{
		if(strtoupper($ln&#91;$i&#93;)===$ln&#91;$i&#93;)
		{
			$k&#91;'country'&#93;=$ln&#91;$i&#93;;
			$k&#91;'state'&#93;='';
			$k&#91;'city'&#93;='';
			$k&#91;'desc'&#93;='';
			$k&#91;'time'&#93;='';
			$k&#91;'payphones'&#93;='';
		}
		else
		{
			if(strpos($ln&#91;$i&#93;,'&#58;')===false)
			{
				$k&#91;'state'&#93;=$ln&#91;$i&#93;;
			}
			else
			{
				$k&#91;'payphones'&#93;='';
				$k&#91;'time'&#93;='5 pm';
				$k&#91;'city'&#93;=substr($ln&#91;$i&#93;,0,strpos($ln&#91;$i&#93;,'&#58;'));
				$k&#91;'desc'&#93;=substr($ln&#91;$i&#93;,strpos($ln&#91;$i&#93;,'&#58;')+2);
				if((substr($k&#91;'desc'&#93;,strlen($k&#91;'desc'&#93;)-3,3)===' pm')||(substr($k&#91;'desc'&#93;,strlen($k&#91;'desc'&#93;)-3,3)===' am'))
				{
					$k&#91;'time'&#93;=substr($ln&#91;$i&#93;,strrpos(substr($ln&#91;$i&#93;,0,strrpos($ln&#91;$i&#93;,' ')),' '));
					$k&#91;'desc'&#93;=substr($k&#91;'desc'&#93;,0,strlen($k&#91;'desc'&#93;)-strlen($k&#91;'time'&#93;));
				}
				else
				{
					if((substr($k&#91;'desc'&#93;,strlen($k&#91;'desc'&#93;)-4,4)===' pm&#46;')||(substr($k&#91;'desc'&#93;,strlen($k&#91;'desc'&#93;)-4,4)===' am&#46;'))
					{
						$k&#91;'time'&#93;=substr($ln&#91;$i&#93;,strrpos(substr($ln&#91;$i&#93;,0,strrpos($ln&#91;$i&#93;,' ')),' '));
						$k&#91;'desc'&#93;=substr($k&#91;'desc'&#93;,0,strlen($k&#91;'desc'&#93;)-strlen($k&#91;'time'&#93;));
					}
				}
				if(strpos($k&#91;'desc'&#93;,'Payphones&#58; ')!==false)
				{
					$k&#91;'payphones'&#93;=substr($k&#91;'desc'&#93;,strpos($k&#91;'desc'&#93;,'Payphones&#58; ')+11);
					$k&#91;'desc'&#93;=substr($k&#91;'desc'&#93;,0,strpos($k&#91;'desc'&#93;,'Payphones&#58; '));
				}
				if(substr($k&#91;'desc'&#93;,0,5)==='(see ')
				{
					$k&#91;'time'&#93;='';
				}
				if(substr($k&#91;'time'&#93;,strlen($k&#91;'time'&#93;)-1,1)==='&#46;')
				{
					$k&#91;'time'&#93;=substr($k&#91;'time'&#93;,0,strlen($k&#91;'time'&#93;)-1);
				}
				$m&#91;$m&#91;'ct'&#93;&#93;=$k;
				$m&#91;'ct'&#93;++;
				}
		}
	}
}
echo '&lt;html&gt;&lt;head&gt;&lt;title&gt;2600 Meetings Table&lt;/title&gt;&lt;/head&gt;&lt;body&gt;';
echo '&lt;h1&gt;2600 Meetings Table&lt;/h1&gt;';
echo '&lt;table border=&quot;1&quot;&gt;&lt;tbody&gt;';
for($i=0;$i&lt;$m&#91;'ct'&#93;;$i++)
{
	echo '&lt;tr&gt;&lt;td&gt;'&#46;$m&#91;$i&#93;&#91;'country'&#93;&#46;'&lt;/td&gt;&lt;td&gt;'&#46;$m&#91;$i&#93;&#91;'state'&#93;&#46;'&lt;/td&gt;&lt;td&gt;'&#46;$m&#91;$i&#93;&#91;'city'&#93;&#46;'&lt;/td&gt;&lt;td&gt;'&#46;$m&#91;$i&#93;&#91;'desc'&#93;&#46;'&lt;/td&gt;&lt;td width=&quot;64&quot;&gt;'&#46;$m&#91;$i&#93;&#91;'time'&#93;&#46;'&lt;/td&gt;&lt;td&gt;'&#46;$m&#91;$i&#93;&#91;'payphones'&#93;&#46;'&lt;/td&gt;&lt;/tr&gt;';
}
echo '&lt;/tbody&gt;&lt;/table&gt;';
echo '&lt;/body&gt;&lt;/html&gt;';
?&gt;[/code:wydeps3t]

Enjoy!
