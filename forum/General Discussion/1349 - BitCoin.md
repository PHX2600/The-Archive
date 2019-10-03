## BitCoin
Posted by **Automated Penguin** on Mon December 13th, 2010 08:18:12 AM

<!-- m --><a class="postlink" href="http://www.bitcoin.org/">http://www.bitcoin.org/</a><!-- m -->

Awesome idea or lame idea?

I started participating as a node about a year ago so I have 50 bit coins now.

I haven't traded in any US currency towards it though. But maybe I should.

Thoughts?

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon December 13th, 2010 08:29:24 AM

Love the concept, but doubt this will ever become much more than a novelty.  The average user probably wouldn't have a clue how to use this, much less keep their computer running to generate currency.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon December 13th, 2010 08:37:53 AM

It's been getting serious press since the wikileaks shit hit the fan.

check it out.

<!-- m --><a class="postlink" href="http://www.pcworld.com/businesscenter/article/213230/could_the_wikileaks_scandal_lead_to_new_virtual_currency.html">http://www.pcworld.com/businesscenter/a ... rency.html</a><!-- m -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Mon December 13th, 2010 08:56:25 AM

Just downloaded and installed the program on my home PC.  Here's a question, if I spend lots of time generating bitcoins and my HDD crashes, how do I get those coins back?  I don't see any option to create an account or a way to "backup" my coins or anything.  It all seems to be contained within program itself.  This would prevent me from moving coins from one computer to another as well (if, for instance, I bought a new computer).

On another note, have you or anyone else attempted to artificially boost your coins in any way?  If so, what measures do they have in place to prevent this, if any?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon December 13th, 2010 08:59:53 AM

There's a .bitcoin directory in the users home directory that contains your "Wallet" this is a symmetrical key type thing like a private key. As long as you have a copy of it you'll be good. so just back that up to a safe place.

As far as artificially boosting your income idk. Maybe publish your bit coin address everywhere and hope some dude wants to send you some coin? IDK.

--------------------------------------------------------------------------------

Posted by **Rax** on Mon December 13th, 2010 06:58:20 PM

[quote="Automated Penguin":3ik1ctz2]There's a .bitcoin directory in the users home directory that contains your "Wallet" this is a symmetrical key type thing like a private key.[/quote:3ik1ctz2]

I have to check out the BitCoin thing, but I'm confused. If it's a "symmetrical key" both the encryption and decryption is done by the same key.  If it's a public key/private key (PKI), that's a totally different (and much more secure IMHO) solution.

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon December 13th, 2010 07:28:09 PM

[quote="Rax":16wlu8zt][quote="Automated Penguin":16wlu8zt]There's a .bitcoin directory in the users home directory that contains your "Wallet" this is a symmetrical key type thing like a private key.[/quote:16wlu8zt]

I have to check out the BitCoin thing, but I'm confused. If it's a "symmetrical key" both the encryption and decryption is done by the same key.  If it's a public key/private key (PKI), that's a totally different (and much more secure IMHO) solution.[/quote:16wlu8zt]


whoops semetric/asymetric only off by one byte.

Forgive me.

yeah definitely NOT symmetric. it's PKI style asymmetric.

--------------------------------------------------------------------------------

Posted by **AltF4** on Mon December 13th, 2010 07:41:54 PM

BitCoin is pretty cool. It's an unholy mess of asymmetric cryptography and hashes. 

Both the innovation, beauty, and weakness to bitcoin is that it's completely decentralized. The main problem with all forms of digital cash is the double spending problem. With physical cash, when you spend a coin you no longer have it. But with digital cash, that isn't true. The double-spending problem is easy to prevent if you have a central bank.

But in a decentralized system, you have to lay down some serious cryptographic shenanigans. Bitcoin uses a system of proof-of-work, timestamps, and web-of-trust. Fraud isn't cryptographically impossible, but it's difficult. You need a lot of cpu cycles and some concerted effort. The author of the protocol had a long writeup about how the CPU cycles used for fraud are unprofitable. Fuzzy on the details about that, it's been a while since I read it.

The EFF is accepting Bitcoin donations, if memory serves.
