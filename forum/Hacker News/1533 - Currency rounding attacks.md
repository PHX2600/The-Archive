## Currency rounding attacks
Posted by **XlogicX** on Thu January 12th, 2012 03:02:30 AM

I know this is an old exploit, but this article sums up how it all works (and is
mostly legal) really well. Banks have lost a lot of money to this:

<http://blog.acrossecurity.com/2012/01/is-your-online-bank-vulnerable-to.html>

--------------------------------------------------------------------------------

Posted by **ArchAngel** on Thu January 12th, 2012 09:00:41 AM

That's actually very interesting -- reminds me of the old no-tech exploit for
online shopping cart software (that still exists in a lot of places) wherein you
order 1.7 items. When the order went in, shipping software would often round up
to the next whole number -- so you'd get 2 xboxen or whatever -- but wind up
getting one item for 30% off, since the payment system did not round. Obviously
this is pretty trivial to patch, but when coding a system it's important to
think of how to handle unexpected data types -- and as a hacker, it's important
to check to make sure that didn't happen. ;)

--------------------------------------------------------------------------------

Posted by **XlogicX** on Thu January 12th, 2012 10:31:15 PM

Yeah, I see a common mistake where business-types assume that the physical-to-
software conversion works 1:1. The two biggest glaring differences (that I see)
that software brings is automation and no-questions-asked. As far as the later,
software doesn't care about your intentions, if it is programmed to accept 1.7
as a valid value, whatever. Whereas humans may ask of your intentions...or just
tell you it's impossible...software wasn't told it was impossible, lol.
Automation can be even scarier. In the currency example, sure, no questions
asked on trading a silly penny for another "penny" in another currency. Even if
the physical bank didn't care about this, it wouldn't do much good in the
physical world. However, with automation and the speed of computing, this benign
activity adds up quick.

I think the same goes with exploits to a vulnerability. It takes a little more
effort in the real physical world. But in computing, all it takes is one person
to write a sciddy tool and now those vulnerabilities are looking a little bit
more vulnerable. Sure somebody could create the super-lockpick in a physical
world, but manufacturing and distribution can still be much more of a bottleneck
than the 0-cost to copy software and the ease of distribution.

my 2 cents.
