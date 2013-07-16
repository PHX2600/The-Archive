## Re: Skynet Leak (Don't know how to read simple code do you?)
Posted by **jargon** on Sat May 8th, 2010 11:33:14 PM

[quote=&quot;jargon&quot;:3jyn4c4n][quote=&quot;Medicine Storm&quot;:3jyn4c4n][url=http&#58;//www&#46;phx2600&#46;org/forum/viewtopic&#46;php?p=3919#p3919:3jyn4c4n]Subject: Skynet Leak[/url:3jyn4c4n]

This is a last-ditch attempt to urge you to redeem the aformentioned post. We are hoping you have chosen to recieve emails from phx2600.org when you recieve a private message on the forum since you seem not to have noticed the responses to your topic.

Please perform one of the following before midnight GMT-07:00 May 3, 2010 or risk being returned to Troll status:
[list:3jyn4c4n]
[*:3jyn4c4n]Provide a description of the code as well as instructions and documentation of functionality[/*:m:3jyn4c4n]
[*:3jyn4c4n]Demonstrate credible and verifiable evidence that the subject, code and your claims thereof are legitimate [/*:m:3jyn4c4n]
[*:3jyn4c4n]Remove the post, and do not repost the same or similarly obfuscated and in-credible material[/*:m:3jyn4c4n][/list:u:3jyn4c4n][/quote:3jyn4c4n]

It was an April Fools post. The code is mainly used in chemical analyzers. The code simply uses venn diagram matching. 'Nuff said.[/quote:3jyn4c4n]
btw, that code I posted roughly April 1st was indeed legit, and the code wasn't obsfucated in any way.

Here, I will rewrite from memory from scratch into this pm...

You are familiar with a Venn diagram right?

Well this also happens to be the very basis for digital logic in the Boolean sense.

This means that computers that are digital will pretty much always suck at fuzzy logic or otherwise neural networking, right?

This code I posted allows for a floating point weight to be created as an output from known collected data directly.

This is also done in relatively few steps.

You have say the height of some objects, their weight, how bright they are, how fast they are moving etc.

You pop all these entries into a database:

Tree: ht 15ft, wt 1500lbs, bright 0, speed 0
Ferrari: ht 4.5ft, wt 2000lbs, bright 120 candle power, speed 240mph
Cheetah: ht 3ft, wt 120lbs, bright 0, speed 60mph
etc
etc
etc

Now,

You can plot out Venn diagrams within the data.

Say we have our Tree and Cheetah

We center two &quot;circle&quot;s one on each data location in the 4 dimensional space, we make the radius of this &quot;hyper&quot; (?) sphere the same as distance between the two points.

Then we check how many times all other datapoints in the database are not in either circle per circle.

This then tallys up to a specific score, with zero being 100% (1.0) final correlation score.

if all other points are in both circles then that is two points per all other datapoints meaning 0% (0.0) final correlation score.

All the code does is throw out any of the max tally total that would go towards data elements with no common attributes, by this I mean say we had an item that didn't have either of height, weight, brightness, nor speed, but instead had altitude, since altitude isn't in common with any of the three examples, it would only count toward a tally if it had an attribute in common.

But say it has height, weight but not brightness and speed like Cheetah but additionally had altitude that Cheetah did not.

all three brightness, speed, and altitude would not be factored into the compared distance for calculating within a sphere, but the comparison would still count towards a tally.

This is all the code does, and should be fairly easily figured out since the code isn't obsfucated in any way what-so-ever.

So either nobody on this site knows how to read code at all other than me, or you guys are all elitists that really have nothing to be elitist regarding.

Cheers, Keal

Btw, I have no idea how Evil1 turned you guys all against me at the meet,

..but the simple story is I caught him red-handed breaking into my house when I wasn't home him having used a lockpick set he had.

'Nuff said.

-edit-

Btw, I wasn't able to respond by the time requested due to issues with family emergencies.

The reason I post the code April Fools every year isn't due to it being bogus, I post it because it really is legit and people always assume flat-out that it is bogus.

You should all know by now (It has only been 6 years!) that I love showing off either at a meet or in-person seemingly in-credible ridiculous bogus code that really is well... legitimate state of the art, despite being decades old, code.

You should also realize I routinely post modifications to a specific formula that without deep run through of the break-down of the formula, always at first glance seems to reduce to a simple &quot;-1&quot; despite having unfathomably complex output.

I dislike anyone that feels they are an elitist due to whatever position of employment they may hold.

There is a couple of folks at the meet-up that actually do sit with me after such a proposal of mine, to hear out the explanation, and do indeed respect me for the deep attention I paid to such details.

Just ask Kilo or t0rX, or maybe even Dual regarding such issues; they may not understand, but they do understand I do seem to be able to present a deeply convincing fireside presentation regarding such.

Cheers, Keal

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Mon May 10th, 2010 12:10:11 AM

[quote=&quot;jargon&quot;:2suwr3w7]btw, that code I posted roughly April 1st was indeed legit, and the code wasn't obsfucated in any way.

Here, I will rewrite from memory from scratch into this pm...

You are familiar with a Venn diagram right?

Well this also happens to be the very basis for digital logic in the Boolean sense.

This means that computers that are digital will pretty much always suck at fuzzy logic or otherwise neural networking, right?

This code I posted allows for a floating point weight to be created as an output from known collected data directly.

This is also done in relatively few steps.

You have say the height of some objects, their weight, how bright they are, how fast they are moving etc.

You pop all these entries into a database:

Tree: ht 15ft, wt 1500lbs, bright 0, speed 0
Ferrari: ht 4.5ft, wt 2000lbs, bright 120 candle power, speed 240mph
Cheetah: ht 3ft, wt 120lbs, bright 0, speed 60mph
etc
etc
etc

Now,

You can plot out Venn diagrams within the data.

Say we have our Tree and Cheetah

We center two &quot;circle&quot;s one on each data location in the 4 dimensional space, we make the radius of this &quot;hyper&quot; (?) sphere the same as distance between the two points.

Then we check how many times all other datapoints in the database are not in either circle per circle.

This then tallys up to a specific score, with zero being 100% (1.0) final correlation score.

if all other points are in both circles then that is two points per all other datapoints meaning 0% (0.0) final correlation score.

All the code does is throw out any of the max tally total that would go towards data elements with no common attributes, by this I mean say we had an item that didn't have either of height, weight, brightness, nor speed, but instead had altitude, since altitude isn't in common with any of the three examples, it would only count toward a tally if it had an attribute in common.

But say it has height, weight but not brightness and speed like Cheetah but additionally had altitude that Cheetah did not.

all three brightness, speed, and altitude would not be factored into the compared distance for calculating within a sphere, but the comparison would still count towards a tally.

This is all the code does, and should be fairly easily figured out since the code isn't obsfucated in any way what-so-ever.

So either nobody on this site knows how to read code at all other than me, or you guys are all elitists that really have nothing to be elitist regarding.

Cheers, Keal

Btw, I have no idea how Evil1 turned you guys all against me at the meet,

..but the simple story is I caught him red-handed breaking into my house when I wasn't home him having used a lockpick set he had.

'Nuff said.

-edit-

Btw, I wasn't able to respond by the time requested due to issues with family emergencies.

The reason I post the code April Fools every year isn't due to it being bogus, I post it because it really is legit and people always assume flat-out that it is bogus.

You should all know by now (It has only been 6 years!) that I love showing off either at a meet or in-person seemingly in-credible ridiculous bogus code that really is well... legitimate state of the art, despite being decades old, code.

You should also realize I routinely post modifications to a specific formula that without deep run through of the break-down of the formula, always at first glance seems to reduce to a simple &quot;-1&quot; despite having unfathomably complex output.

I dislike anyone that feels they are an elitist due to whatever position of employment they may hold.

There is a couple of folks at the meet-up that actually do sit with me after such a proposal of mine, to hear out the explanation, and do indeed respect me for the deep attention I paid to such details.

Just ask Kilo or t0rX, or maybe even Dual regarding such issues; they may not understand, but they do understand I do seem to be able to present a deeply convincing fireside presentation regarding such.

Cheers, Keal[/quote:2suwr3w7]

Actually we didn't assume flat out that the code was bogus, (especially considering that no one plays April fools jokes on april 3rd) we just wanted to know what it was and how to make it useful. Obfuscation need not be intentional. By &quot;obfuscated&quot; we mean the code does not use any descriptive or intuitive variable names, function names, or commands nor does it contain any descriptive text or comments that indicate how it might be used. The containing post also lacked instructions or other descriptions of the code's use. 

in-credible ridiculous bogus-seeming code that is actually legit is fine and even welcome, so long as you can demonstrate that it is legit or useful. You have not done either.

We assume your reference to the complex formula that breaks down to &quot;-1&quot; is in regards to an entirely separate post. Our analysis of the formula was not a shallow run-through nor was it a &quot;first glance&quot;. Algebraically (algebraic operations were the only operations in the formula) reducing the formula manually as well as running the entire formula executed in code both resulted in the same constant answer: -1. We even accounted for uncountable and denumerable infinity as well as imaginary numbers. Not an unfathomably complex output. We can totally comprehend negative one. If the formula does indeed perform some function that miraculously does not evaluate to negative one, that is fantastic! We love being wrong for the sake of learning, BUT YOU HAVE TO DEMONSTRATE ITS USE OR PROVE IT IS LEGITIMATE!

To think that everyone but you &quot;[Doesn't] know how to read simple code&quot; is, frankly, arrogant. We could write some very &quot;basic&quot; code who's function is totally obvious to us, but to everyone else, INCLUDING YOU, it would make no sense out of context because you are not the author of the code and do not know it's purpose or intent [i:2suwr3w7]regarldess of your skill as a &quot;L33T programmer&quot;[/i:2suwr3w7] 

The point is, even if the purpose of the code should be obvious to an intermediate programmer, only things that help other hackers learn and grow should appear on these forums. If the purpose of your code doesn't make sense to anyone, you should be more descriptive or answer their questions when they ask about the code. You failed to do either.

You were able to &quot;rewrite from memory from scratch&quot; a description of the code, yet you didn't bother to write it in the post the first time, nor did you post a description in a timely manner after we asked for it. You say you were unable to get back to it in over a month. That is acceptable. That is why we didn't just ban you or set you to Troll status. We just locked the topic until you had a chance to respond to our PM and clear up the issue. We weren't being a bastard, or high-and-mighty. We honestly didn't have any idea what the code was for or how to use it, so we asked. Furthermore, the description and instructions you gave were far from obvious or intuitive when looking at the code by itself. Refusing to do anything constructive to resolve the issue and posting an elitist and flame-riddled post to a locked topic as a response to a private message is, conversely, not acceptable.

The phrase &quot;So either nobody on this site knows how to read code at all other than me, or you guys are all elitists&quot; is quite the hypocritical statement. In the first part you paint yourself an elitist by saying nobody but you can read code and in the second part you accuse everyone but you of being elitist for not knowing what your code does. Keep in mind that we were the only person who claimed the code was unclear. We are sure there is at least one other hacker on this forum who is on par with your uber skilz, so we are the only hacker at which you should be directing your accusations. 

We strive to avoid elitism and certainly don't feel we are elite due to our position of employment. You say there are a couple of folks at the meet-up that sit with you after a proposal you make. We are one of those hackers! We have sat with you and listened to your ideas and propositions and intellectually and philisophically explored all the avenues and ramifications of those proposals. Yes, we do indeed respect you for the deep consideration and thought-out-of-the-box, but we must say, &quot;deeply convicining&quot; is lacking because very few of your presentations can be demonstrated or validated. We are not picking on you about validation. We would be skeptical of someone who claimed the sun gave off light if they could not demonstrate their claim.

Regarding Evil1 turning us guys against you: we are really not very familiar with Evil1 and have not heard any comments whatsoever from him about you, much less anything that would sway our opinion of you.

The fact that you responded to a [i:2suwr3w7]Private[/i:2suwr3w7] Message by posting a new topic regarding a topic that was [b:2suwr3w7]locked for a reason[/b:2suwr3w7] just indicates to us that you have no interest in resolving this issue or providing useful material, but instead you only seem to wish to start some drama. Rest assured this is the last time we will be feeding the Troll.

[Jargon has been returned to Troll status]

&quot;'Nuff said&quot;
