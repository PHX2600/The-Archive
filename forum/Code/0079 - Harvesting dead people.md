## Harvesting dead people
Posted by **dual** on Tue March 18th, 2008 12:43:02 AM

This grabs names from legacy.com's obituaries. I don't know why I did it. It eventually stopped writing to the log, though I think assigning the backreference to a temp would fix it. Probably should have included the ID in the log. I'm so going to hell.

[code:1ripjscm]#!/usr/bin/perl -w

use strict;
use LWP&#58;&#58;UserAgent;


my $beg = 100000000;
my $end = 999999999;


open LOG, &quot;&gt;&gt;obit&#46;log&quot; or die &quot;Can't open log&#58; $!&quot;;


my $browser = LWP&#58;&#58;UserAgent-&gt;new;
$browser-&gt;agent(&quot;Mozilla/4&#46;0 (compatible; MSIE 7&#46;0; Windows NT 5&#46;1)&quot;);


my $url = 'http://www.legacy.com/AZCENTRAL/GB/GuestbookView&#46;aspx?PersonId=';


for (my $i = $beg; $i &lt;= $end; $i++) {
        print &quot;$i\n&quot;;

        my $response = $browser-&gt;get($url&#46;$i);
        #die &quot;Can't get $url -- &quot;, $response-&gt;status_line
        #       unless $response-&gt;is_success;


        if ($response-&gt;content =~ /&lt;title&gt;Guest Book - (&#46;+)&lt;\/title&gt;/) {
                my $tmp = $1;
                print &quot;$tmp\n&quot;;
                print LOG &quot;$tmp\n&quot;;
        }

        sleep 1;
}


close LOG;
[/code:1ripjscm]

[code:1ripjscm]Jerry Reece Sr&#46;
Cleo Fletcher
Lenora Conley
Thomas Bezan
David Holt
Marlys Lehr
Haywood Whaley
Walter Butler
Emily Mathes
David Haas
Raleigh Doss
Jeri Lyn Bruner (Wilcox)
Arlene Strow Chichester
Kiong Peng
Merle E&#46; Bailey
Kyle Creighton Barker
Gasberdena C&#46; Hein (Dena)
Blanche E&#46; &quot;Granny&quot; Pierson
Betty Parrack
Lucille Dosser
Lawrence M&#46; Engelbrecht (Larry)
Jesse Lee Moore
William H&#46; Davis Jr&#46;
Hollis M&#46; Overton
Donald L&#46; Paul
Richard George &quot;Dick&quot; Hansen
Robert G&#46; Noyes
Alberto M&#46; Elle
Lillian C&#46; Canete
Dorothea M&#46; Sanger (Gamble)
Eleanor Andrews
Andrew &quot;Sonny&quot; Sena Jr&#46;
Lily M&#46; Lamb
John L&#46; Sharrer
Alida R&#46; Bradish
Elizabeth Naylor
Michael Lewis Wright
Elda Martha Mathey
Conan Andrew McLaren
Raymond G&#46; Magnuson
Gayle M&#46; Docherty
Claudine Mae Champlain
Henry Weldon Riddick
Ross Killian Smith
Leonard R&#46; Christlieb
Evelyn Maul Anderson
Gayle Ballew
Louise Burns
George C&#46; Crews
Heide Marie Cummings
Malcolm L&#46; &quot;Mel&quot; Dearman
Doris D&#46; Doak
Wynelle Brown Eubank
Wallace Fincher
Betty LuOma Duke Giaimo
Marge M&#46; Henning
Warren John Herrig
William Boyd Hunt Sr&#46;
Annie Nell Hyles
Judy Faye King
Johnnie Margaret Lyon
Pamela Kay Martin
Anita Jean Miano
Charles Weldon &quot;Charlie&quot; Milam
Michael Feeney Petterson
Elaine Bramlett Pruett
Donna Jean Ridell
Miki Rios
Dallas Andrew Teeters
Pastor J&#46;D&#46; Wade
Jesse Ward
Anthony Casarella
Michael Scott Gee
Marshall &quot;Marcelino&quot; Archuleta
Lowell Willis &quot;Abe&quot; Abramson
Marjorie Grace McRae Collord
Marjorie B&#46; Spellman
Earl Patrick Hughes Sr&#46;
Michael R&#46; Goss
James A&#46; Goller
Ronald Edwin Herr
Joseph E&#46; &quot;Tim&quot; Thompson II
Nedra L&#46; Meyer
Ralph Monsieur Farmer
Helen S&#46; Bickett
Laura Marie Chichester
Sarah Belk Ferry
Mark S&#46; Funderburk Jr&#46;
Izola Johnson Hamilton
G&#46; Bruce Park
Larry Daniel Parkerson
Harry McFall Pickett Jr&#46;
Helen Lovette Weatherly
Ralph Gilbert Shinn
Jo Ann Mason Wheat
James Ralph Todd (Jim) Jr&#46;
Samuel Patrick &quot;Pat&quot; Carter
George Thomas Gaines
Samuel Gaston Garrison
Modistine Nichols Alexander
Phillip James Ankney
Christopher Earl Ankney
Martha Noles Black
Brittany Boone
Brittany Boone
Brittany Kiara Boone
Brittany Kiara Boone
Brittany Boone
Brittany Boone
Brittany Boone
Brittney Boone
Brittany Kiara Boone
Brittany Boone
Thomas Reginald Byrd
Ruth Ganey
Angelo Giancanelli
Renita Hill-Kee
Mary H&#46; Wilson
John Larango
Dale H&#46; &quot;Bud&quot; Hocken
Jeppe H&#46; Sorensen
Brysza Maria Hugs
Thomas Watson Hanks
William D&#46; Sheehan
Beatrice Grace Meleton Haglund
Paul Russell Brown
Mabel Ellen Loveridge (Miller)
Willis B&#46; Jones
Savannah &quot;Sue&quot; Moses-Berg-Haswell-Becker
Clara Meyers
Helen K&#46; Miller
Leo Francis Kimmet
Wayne A&#46; Boyd
Norma Marlene Trapp Gantz
Robert J&#46; Dietz
Donald Glen Brogan
Pamela Dare &quot;Pam&quot; Watson-Rogers
William &quot;Bill&quot; Carman
Donald A&#46; Adams
Donald L&#46; Baas
Kyle Creighton Barker
Dorothy Anna Beck
Jim Bishop
Jeanne Bogdan
William &quot;Bill&quot; Canon Sr&#46;
Cecil C&#46; Curp
Annette Danell Chandler
Rosemary P&#46; Fisher
Carl Glauser
Lawrence Howard Goldberg
John V&#46; Goodbar Jr&#46;
La Vierge M&#46; Kaiser
Frank LeRoy Kellgren
Catherine Ann &quot;Cathy&quot; Kinnard
Gwen C&#46; Kraushaar
Shirley Languein
Mildred L&#46; McQueeney
Pauline M&#46; Myers (Ruckh)
Hollis M&#46; Overton
Sarah Elise Ramey
Theresa L&#46; Ridout
Pamela A&#46; Romine
Edna &quot;Joyce&quot; Salter
James G&#46; Schultz Jr&#46;
David Gene Shaw
Marty Stearns (Myrtle)
Fred H&#46; Theden
James C&#46; Vleisides Jr&#46;
Arthur F&#46; Wiswell
Jennifer and Graham Bankston
Beverly Ann Thomas Bouillion
Howard L&#46; Chaney Jr&#46;
Don Keith Rooker
Rebekah Fuller &quot;Becky&quot; Peeler
Robert Eugene &quot;Hutch&quot; Hutchinson
Edgar W&#46; Beeson
Paul H&#46; Dunham
Reynold W&#46; Schendel (Ray)
Madeline Dominski (Geiger)
Pastor Jocelyn Kelker
Daniel L&#46; Wirebaugh
Richard &quot;Hawk&quot; Mehok
Jack Hart
Richard Scuba
Gladys Mary Vuin
Marilyn J&#46; Wagner Stevenson
Nicholas Lee Bennett
Glenn E&#46; Grubb
Ann T&#46; O'Breza
Robert O&#46; Webster
Charles Richard Grabel (Dick)
June Byer
Ronnie E&#46; Ballard
Gerald E&#46; Smith
Zelma Williams
Mario V&#46; Gasbarro
Lillian L&#46; &quot;Lil&quot; Butzer
Sandy L&#46; Riley
Joseph James Mills
Willie F&#46; Wright
Clarence Beasley
Marian I&#46; Donohoe
Mary Ann Underation Lipovsky
James C&#46; Gish
Robert Earl Helmling Sr&#46;
Dragan &quot;Doug&quot; Doroslovac
David Weston Burt
David P&#46; Cartwright
Mary D&#46; Donohue (Cartier)
E&#46; Pauline Elmquist
Eleanor Salisbury Fenton
James Rogers Fox
Lyle B&#46; Garvey
Jennie Hathaway
Pearl E&#46; Hillman
Elizabeth J&#46; Hobza
Mary L&#46; Huberty
Robert P&#46; Indihar
Norma M&#46; Johnson
Elaine Novak Keller
Doug Kline
Kristine C&#46; Larson
Alverna M&#46; Loehlein
John A&#46; Lyons
Joseph R&#46; Magnuson
A&#46; Donald McCormack
Ruth V&#46; McKee
D&#46; Meryl McKinney
Rudy O&#46; Melquist
Celia B&#46; Meyers
Agnes J&#46; Mills
Elaine Anna Misita
Grant Seth Mooney
Eleanore K&#46; Nelson
Fern J&#46; O'Day
Charles A&#46; Reidell Sr&#46;
Ethel Roberts
Ruth H&#46; Sandberg
Julia Sandoval
Mary Louise Singher
Judi P&#46; Smith
Betty A&#46; Swanson
Michael F&#46; Terrell
William W&#46; Wadena
Reverend John J&#46; Wirth
Manuela Subia (Tijerina)
Daniela Marie Capano
Leroy F&#46; Spinks
John B&#46; Loiodice
Karen Aldrich
Leigh Ann Koenig
Cleta Lawson Stover
Charles Bolchoz
Esther V&#46; Gonzales
Jennie G&#46; Lopez
Lupe Maria Hernandez-Carrasco
Robert J&#46; Giove
Kenneth Mitsuru Saika
William C&#46; &quot;Bill&quot; Haskins Jr&#46;
Reverend Virgil F&#46; Bjerke
Robert D&#46; &quot;Bob&quot; Henderson
William &quot;Bill&quot; Masters
Jerry Cook
Mary C&#46; Kuker
Trevor Phillps
Faye E&#46; Willis
James A&#46; Pruitt
Lucy Reyes Lujan
Matthew Lawrence Emershy
Jean Rose Bonsangue
Edwin &quot;Eddie&quot; Cohn
Charles Putt
May MacClaire Arlt
William Wayne Kimbrel Jr&#46;
Michael Kesend
Ida Iseson
Berenice Rosenberg
Beatrice Brown Rogers Guthrie (Bee)
Jean Borteck
Fred Gross
Arnold Weisenfeld
Cynthia Calabrese
Jerome Gewirtz
Maggie Masler
Daniel A&#46; Okun
Miriam Borko
Peggy Kornicker
Marilyn Padow (Rubin)
Mildred Maranghi &quot;Billie&quot; DeGraff
Margaret Heimann (Fechheimer)
Patricia B&#46; Wellington
Esther Pickholz
Erica Whitehead
Roland Algrant
Robert B&#46; Durkin
Timmi Goldstein
Robert Stang
Frederick V&#46; Krais Jr&#46;
Harold &quot;Harry&quot; Cohn
Roger Sichel
Alfred L&#46; Mendelsohn
Celia Samose
Walter Frieling
Stan Boras
Ted Steinberg
John Lind
John Richard Ayres
Glen Edwin Barbour
Wilma T&#46; Bottorff
Thelma Daggett
Alice L&#46; Daniels
Mary L&#46; Elliott
George William Flynn
Wing Suey Fong
Dorothy Virginia Freitas
Roberta Olsen Lehigh
Charles Mathews (Bob)
Paul M&#46; Maynard
J&#46; Richard McProuty (Mac)
Vu D&#46; Nguyen
James K&#46; &quot;Jim&quot; Olmo
Doris Sophia Pearson
Elisabeth Roubos (Beppie)
George E&#46; Saber
Robert E&#46; Simmons
Crustalo Anish
Wilhelmina Arnold
Joyce Barbito
Daisy Victoria Edwards
Lilla M&#46; Hallenbeck
Edward P&#46; Moran
Bob Stone
W&#46;A&#46; &quot;Al&quot; Young
Tinky Grisham
Sharon June Borg
Ernest Ouellette
Sharon A&#46; Wilson Stein
JoAnn Barbara &quot;Joey&quot; Stopnik
Rallin W&#46; Sundbom
Hazel E&#46; Sward
Iris J&#46; Anderson
Mary Jane Erikson (Richardson)
Helen V&#46; Frank
Isabell Grover (Steve)
Ralph E&#46; Harvey
Richard Bagley Heimbach
Ila &quot;Sis&quot; Meismer
Emma A&#46; Jacobson
Elia Mary Pederzolli (Sterle)
Gerald J&#46; &quot;Porky&quot; Seitz
Mary Margaret Welsand
Bill F&#46; Jones
Vionia Holloway Adrian
James Marion Berry
Leon Ponder Bloodworth
Dea&#46; John O&#46; Green Jr&#46;
Shirley Patricia Caldwell Hansbrough
Anne Windley Buchanan Hazen
Nancy Lea Kratina
Michael Feeney Petterson
Mildred B&#46; Ricardo
Jewell Lee Sheppard
Kelly F&#46; Weinberg
Arthur B&#46; White
Glenna Teressa Hines
Marty J&#46; Tyson
Donald J&#46; McGraw
Rev&#46; Kenneth E&#46; Williams
Wallis I&#46; Hoyle
Mary Lanzalotti (Fusco)
Richard H&#46; Casey
William F&#46; Dannehower III
Jeannete McBreen (Miller)
Lynda Elliott Elliott (Barton)
Arsenia C&#46; Ortiz (Cala)
Katherine H&#46; Knox (Huber)
Michael Patrick Nolan
Anastasia M&#46; &quot;Stacey&quot; Wilson (Edelmann)
Doris Edwards (Campbell)
Judy E&#46; Lafferty
Mae Wentzel (DiGiacomo)
Raymond August Reher
Christopher T&#46; Angelos
Arlene Stratton
Mary Ford (Martin)
Nickolette Castrovillo (Macredes)
Elizabeth Bergus
Joseph Michael Scioli
Loretta B&#46; Blanchfield (Toland)
Stanley K&#46; Domian
Mary J&#46; Bender (Tracey)
Yolanda Banfi
Stanford P&#46; Sheptak
Irwin C&#46; Furman
James E&#46; Werner
Eleanor M&#46; Kane (Ryan)
Joseph G&#46; Roming
Gloria R&#46; Steacker (Barrulli)
Josephine M&#46; Lattanzio (Malandra)
Lee H&#46; Vogeding
Clarice Valerie Black
Leontios Katourtsidis
Marjorie J&#46; DiMeo (Zielke)
Ruth &quot;Lucky&quot; Malin (Shapiro)
Marguerite &quot;Madge&quot; McGinniss
Martin Gross
Patricia M&#46; Ward (Keenan)
Francis Costello
Aristide &quot;Art&quot; Casciato
Henry S&#46; Levy
Charles F&#46; Kotarski
Harry Williams Homeier
John M&#46; Gribbin Sr&#46;
John J&#46; Byrne
William Leehive
Nicola Louis Comito
Ruth B&#46; Wiley
Martin J&#46; Pottichen
[/code:1ripjscm]

--------------------------------------------------------------------------------

Posted by **nak** on Tue March 18th, 2008 12:43:00 PM

Very cool, my new coworker has a mom that works in the police department and has been showing me some stuff you can look up via public records.

Like:
<!-- m --><a class="postlink" href="http://www.maricopa.gov/Assessor/ParcelApplication/Default.aspx">http://www.maricopa.gov/Assessor/Parcel ... fault.aspx</a><!-- m -->

and

<!-- m --><a class="postlink" href="http://genealogy.az.gov/">http://genealogy.az.gov/</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **dual** on Wed March 19th, 2008 10:26:22 PM

I've used the County Assessor's tool before and it's quite handy. The genealogy tool is new to me. Thanks, nak.

Dork for lots of dead people:
inurl:GB/GuestbookView.aspx?PersonId=

--------------------------------------------------------------------------------

Posted by **Philyteach** on Sun December 28th, 2008 07:39:03 AM

So now that you have harvested my grandmom's information (Yolanda Banfi), what exactly are you planning to do with it?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Sun December 28th, 2008 11:00:03 AM

Yup... you're definitely going to Hell... if there is such a place.

But that's definitely interesting.

--------------------------------------------------------------------------------

Posted by **nak** on Mon December 29th, 2008 01:41:18 PM

Its not &quot;her information&quot; it just parses names of dead people <!-- s:o --><img src="{SMILIES_PATH}/icon_e_surprised.gif" alt=":o" title="Surprised" /><!-- s:o --> 

People share names &lt;3 it's beautiful.
