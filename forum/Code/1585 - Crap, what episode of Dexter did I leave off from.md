## Crap, what episode of Dexter did I leave off from?
Posted by **XlogicX** on Sat March 31st, 2012 03:37:39 AM

So these are some odd scripts that are probably only useful to me. The dilemma was that I watch a few TV shows, and I watch them sequentially, and sometimes it's hard to keep track of which episode I left off on for which show. I used to be a heavy user of Fences for windows and just have a copy of the most recent show in a fence, then I could resize the fence to reduce desktop clutter (or the visual side-effect of it).

Linux doesn't have fences, or anything I know of that would be close to it. Then I saw that VLC has a most recent videos menu, showing you the last 10 videos you have watched. That's kind of the idea I was looking for, it would work perfectly if I were only watching a couple different TV shows evenly distributed. But for anything else (namely, my own habits), I would need a much larger history.

So I made two scripts to solve this. One script to make a bigger history, piggybacking of of VLC's .conf file and cron'ing the script to have my own list:

[code:1eeaufmf]#!/usr/bin/perl
# recent_vlc
use warnings;
use strict;

my @videos;
my $last_vid;
my $list;

chdir;
open IN, &quot;&#46;config/vlc/vlc-qt-interface&#46;conf&quot;;
open VLCIN, &quot;logs/vlc&#46;txt&quot;;
open OUT, &quot;&gt;&gt;logs/vlc&#46;txt&quot;;

@videos = &lt;IN&gt;;
$last_vid = $videos&#91;5&#93;;

$/ = undef;
$list = &lt;VLCIN&gt;;
$/ = &quot;\n&quot;;
close VLCIN;

if ($last_vid =~ /(list=)(&#91;^,&#93;+&#91;^,&#93;)(, \/)/) {
        if ($list !~ $2) {
                print OUT &quot;$2\n&quot;;
        }
}
[/code:1eeaufmf]

And then another script that I can run to query whichever TV show I want (including regex queries). It will respond with the full path of the last entry in the list matching the search/regex. If no matches, it does nothing. Nothing fancy, just a quick hack I put together.

[code:1eeaufmf]#!/usr/bin/perl
# recent_vlc
use warnings;
use strict;

my $list;
my $pattern;
my $answer;

chdir;
open IN, &quot;logs/vlc&#46;txt&quot;;

print &quot;What Video do you want to know about?&#58; &quot;;
$pattern = &lt;STDIN&gt;;
chomp($pattern);

$/ = undef;
$list = &lt;IN&gt;;
$/ = &quot;\n&quot;;

while ($list =~ /(\n&#91;^\n&#93;*)($pattern)(&#91;^\n&#93;*&#91;\n&#93;)/isg) {
        $answer = &quot;$1$2$3&quot;;
}
print &quot;$answer\n&quot;;
[/code:1eeaufmf]

--------------------------------------------------------------------------------

Posted by **Anonymous** on Tue July 31st, 2012 08:55:12 AM

To the contrary, fences is based off KDE's desktop after version 4.
[img:11wt96ju]http&#58;//upload&#46;wikimedia&#46;org/wikipedia/commons/thumb/1/1b/KDE_4-1_desktop&#46;png/300px-KDE_4-1_desktop&#46;png[/img:11wt96ju]
