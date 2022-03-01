## Caesar+Vigenere Python
Posted by **Automated Penguin** on Sun November 8th, 2009 04:37:38 PM

I got pretty interested in some of these ciphers after AltF4's talk so I decided to program a little python which would test out some of the ideas behind breaking these ciphers. 

I have attached a zip file which contains 4 python files, 2 function libraries I created called Caesar.py and Vigenere.py and then 2 others with the word test appended to them which use the above libraries to encrypt attack and then decrypt some text.

Here is some sample IO from the files in case you cant be bothered to download them

Caesartest.py:
[code:3jzsm4u1]
Key&#58; 21
Original&#58;  this is a test of the english language
Encrypted&#58; ocdn dn v ozno ja ocz zibgdnc gvibpvbz
Decrypted&#58; this is a test of the english language

Key&#58; 19
Original&#58;  this is really short
Encrypted&#58; mabl bl kxteer lahkm
Decrypted&#58; this is really short

Key&#58; 3
Original&#58;  too short
Encrypted&#58; wrr vkruw
Decrypted&#58; faa etadf
[/code:3jzsm4u1]

Vigeneretest.py:
[code:3jzsm4u1]
Key Used&#58;  phxhackz

Original&#58;  The Kasiski examination also called the Kasiski
    test takes advantage of the fact that certain common words like
    the will by chance be encrypted using the same key letters leading
    to repeated groups in the ciphertext For example a message encrypted
    with the keyword ABCDEF might encipher crypto the same way each time
    it appears in the plain text

Encrypted&#58; iob kcchhrf ezklxuxaiqx pspv ekkala tjo zhppsms
    tgcs axreu zscxutcqd vc tjo uhza vrzi zlrvkhc zvmoym dlydu kxrb
    iob wkvk iv cjkmrl ie omryvwtgn jzfug dgt phmg jtf sevddgz secnhcn
    sd olpgkstk nrqeoh fu vrd jfwhgbsteq fqb textpno p jlsukft buctioila
    lpqo vrd rbfwqbc hyjdgp bpdot omrpmoet bgfmao dgt phmg vpf laer ipjl
    pq arzdpyp ip swl wlcsm abet

Collisions At&#58; &#91;152, 40, 152, 56, 120&#93;
Probable Key Lengths&#58; &#91;1, 2, 4, 8&#93;
Probable Keys&#58; &#91;'b', 'ph', 'pcxs', 'phxhackz'&#93;
[/code:3jzsm4u1]

The Caesar cipher breaker uses a simple statistical analysis to find the best possible match 

The  Vigenere cipher breaker uses 2 strategies, first it searches the entire cipher text to try and find any collisions longer than 3 letters if it finds any it stores the difference of their positions in a list and then uses them to determine the most likely key length.

For example if &quot;xyzr&quot; is found twice and they happen to be 20 characters from each other in the text then the key length must be either 20,10,5,4,2, or 1

after the most likely key lengths have been determined the cipher text is arranged into x number of columns where x is the key length we are testing for, then a statistical frequency analysis is applied to each column and the resulting best shift value is considered to be the letter of the key for that position. 

Notice also that this second method can be used even without reducing the number of possible key lengths in a sort of &quot;brute force&quot; style attack where we simply test for every possible key length, which is exactly what my program will do if it finds no collisions.

Anyway I have learned a ton from playing with this stuff so thanks again to AltF4 for his sweet presentation

--------------------------------------------------------------------------------

Posted by **AltF4** on Tue November 17th, 2009 08:27:42 AM

Nice! That's awesome you actually did the statistical attack for Caesar. Usually when you see code that &quot;cracks&quot; these ciphers, they make you do the analysis manually. So that's awesome. 

You could probably extend these programs really easily to break any generic monoalphabetic substitution cipher, too. All you do is check the distribution across the letters like you already have. Then begin guessing which ciphertext letter maps to which plaintext letter based on the distribution.

Also, can't you see now why it makes your ciphers stronger if you compress your message before encrypting it? All of these attacks you're doing relies on the fact that the plaintext has low entropy. But if the plaintext were compressed, it would have high entropy.

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Thu December 10th, 2009 09:30:28 AM

Nice. Zaphraud used a similar method to attempt brute-forcing a component of the [http://www.phx2600.org/forum-archive/viewtopic&#46;php?t=1466](obfusconversation (message 9)). Unfortunately we could not give him full points because of the &quot;statistical&quot; portion of these types of cracks means that sometimes the result is slightly inaccurate.

Off topic, but: since the contest was never quite completed and the amount of remaining points available was enough to sway the outcome, we never named a winner. We think it is time to declare a deadline. We'll talk to XlogicX and possibly start a new thread on it.
