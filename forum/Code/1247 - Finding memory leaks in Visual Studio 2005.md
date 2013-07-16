## Finding memory leaks in Visual Studio 2005
Posted by **Medicine Storm** on Sat May 22nd, 2010 01:29:34 PM

We are using Visual Basic .Net 2005 professional.

From what we understand, we should be disposing of any object that is an unmanaged resource. We understand the best way to tell if a resource is unmanaged is if it has a Dispose method. ie: If we type a dot after my object, intellisense shows .Dispose() as one of the options. If it does, it's an unmanaged resource. Is that correct?

In that case, pretty much every control is an unmanaged resource: buttons, forms, panels, etc.

In the application we are working on we use an MDIparent container form, which contains MDI children forms, which themselves contain Panels, Menus, Groupboxes, etc, which in turn contain Buttons, Textboxes, Labels, Dropdowns, etc.

Do we have to dispose of each button, textbox, label and dropdown within a panel before disposing of the panel?
Do we have to dispose of each panel, menu, and groupbox before disposing of the MDI child form?
...Or can we just call the Dispose() method of the MDIchild form and the GarbageCollector will take care of all the controls and resources within the form?

The reason we ask is because we have been disposing of the child forms whenever they are closed, but we are still seeing signs of memory leaks.

Watching the &quot;mem usage&quot; in Windows Task Manager seems to be an unreliable way to detect if I have a memory leak. The numbers just keep climbing and falling (mostly climbing) erratically and without any activity performed on the application. Is there some (relatively) easy way to detect leaks?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon May 24th, 2010 09:44:25 AM

Perhaps the leak is caused somewhere other than your garbage collection.  Loops are a common place for memory leaks to occur.

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon May 31st, 2010 08:59:53 AM

No, the Dispose() method doesn't mean that the object is unmanaged. The Dispose() method is just a way for you to properly dispose of any unmanaged resources that the object may be carrying. (File I/O or anything marked as &quot;unsafe&quot; for instance&quot;)Or perhaps you can do some other tasks. (sending a goodbye message to the user before the window closes)

In general, you shouldn't try to second guess the garbage collector, though. Do some googling around on how best to use Dispose() and Finalize(). They both have subtle differences. 

Though if you're just doing normal .NET programming (or Java for that matter, since .NET is just a JRE ripoff) don't worry about any of this stuff. The Garbage Collector will take care of it all.


EDIT: Also, standard &quot;memory leaks&quot; don't occur as you know them in managed code. Typically a memory leak happens when an object exists in memory with no references to it. The GC will take care of all of those cases. But &quot;leaks&quot; can still kind of happen. If you're careless about object instantiation, you can wind up creating a whole lot of objects that are still referenced, but no longer in use. So although you don't have to worry about low level memory management, you still have to keep track of what objects you create.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Tue June 1st, 2010 11:45:49 PM

[quote=&quot;PHLAK&quot;:8qznglcr]...Loops are a common place for memory leaks to occur.[/quote:8qznglcr] How and why?

[quote=&quot;AltF4&quot;:8qznglcr]...anything marked as &quot;unsafe&quot; for instance...[/quote:8qznglcr] Where would they be marked as unsafe?

[quote=&quot;AltF4&quot;:8qznglcr]...since .NET is just a JRE ripoff...[/quote:8qznglcr] Lol. [citation needed]

[quote=&quot;AltF4&quot;:8qznglcr]...you can wind up creating a whole lot of objects that are still referenced, but no longer in use.[/quote:8qznglcr] Good to know. In that case we have very little to worry about. Our objects references are obsessively tracked.

--------------------------------------------------------------------------------

Posted by **AltF4** on Wed June 2nd, 2010 08:22:13 AM

Also keep in mind that you might not be getting leaks at all! 

The garbage collector is designed purposefully to not bother freeing memory until it needs to. (Another process requests some) So a normal, non-leaky, program may very well balloon up to &quot;using&quot; your entire system memory after a while of use. Only then to plummet down suddenly when something requests memory. Happened to me all the time when I did .NET development a while ago. 


Also also, come on! C# is practically copy-pasteable into Java. M$ stole the Java bytecode idea and called it &quot;MSIL&quot;. Even the built in library functions are nearly identical. This was on purpose to try and win over as many Java devs to their side as possible. It's no secret.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Thu June 3rd, 2010 11:26:01 AM

[quote=&quot;AltF4&quot;:sjghtei0]...a normal, non-leaky, program may very well balloon up to &quot;using&quot; your entire system memory after a while of use. Only then to plummet down suddenly when something requests memory...[/quote:sjghtei0] Good point. Your advice is looking more and more consistent with what we are seeing. Thanks. We are reassured.

[quote=&quot;AltF4&quot;:sjghtei0]...C# is practically copy-pasteable into Java. M$ stole the Java bytecode idea and called it &quot;MSIL&quot;. Even the built in library functions are nearly identical. This was on purpose to try and win over as many Java devs to their side as possible. It's no secret.[/quote:sjghtei0] blah, blah, blah, and the windows concept was stolen from Xerox, the catholic church stole the holidays from the pagans, and java is a ripoff of C++. Although true, none of them are [i:sjghtei0]actual[/i:sjghtei0] ripoffs... meaning the basic underlying concept might be the same, or perhaps one incorporated some feature that made the former superior, but the off-rippers always made it their own, dare we say, IMPROVED version. There is a fine line between plagiarism and the constantly evolving improvement of technology. Not reinventing the wheel and incorporating others' good ideas is considered good programming practice. Java had a good thing going, so .Net incorporated it. C++ had a good thing going, so Java incorporated it. The thing that makes .Net evil and Java not-evil has little to do with who ripped off whom. &quot;Evil&quot; is determined by the fact that .Net is closed source, whereas Java is open and free, and therefore cannot be blamed for anything. .Net is seen as evil by default. <!-- s:) --><img src="{SMILIES_PATH}/icon_e_smile.gif" alt=":)" title="Smile" /><!-- s:) -->

We aren't saying we support the stealing of ideas. We are saying both Java and .Net are guilty.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Thu July 8th, 2010 12:14:11 PM

P.S. Thanks! That answered our question.
