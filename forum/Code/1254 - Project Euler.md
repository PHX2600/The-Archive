## Project Euler
Posted by **maxwell** on Thu June 17th, 2010 01:48:49 AM

Post your project Euler solutions! if you dont know what project euler is, it's basically homework for amateur programmers (found here <!-- m --><a class="postlink" href="http://projecteuler.net/">http://projecteuler.net/</a><!-- m -->).

The first problem is:
Add all the natural numbers below one thousand that are multiples of 3 or 5.
here is my solution in Python:
[code:22sq7juk]
sum = 0
for i in range(1000)&#58;
    if i%3 == 0 or i%5 == 0&#58;
        sum += i
print sum
raw_input('\npress any key to close')
[/code:22sq7juk]
The second problem is:
Find the sum of all the even-valued terms in the Fibonacci sequence which do not exceed four million.
here is my solution in Python:
[code:22sq7juk]
a,b = 0,1
c = a + b
sum = 0
while (a and b) &lt; 4000000&#58;
    a = b + c
    if a%2 == 0&#58;
        sum += a
    b = a + c
    if b%2 == 0&#58;
        sum += b
    c = a + b
    if c%2 == 0&#58;
        sum += c
print sum
raw_input('\npress any key to exit')
[/code:22sq7juk]

--------------------------------------------------------------------------------

Posted by **Medicine Storm** on Tue June 22nd, 2010 11:20:03 AM

This is pretty cool. We are not very familiar with python. Does [b:ygvfmscl]i[/b:ygvfmscl] start with zero when it's in &quot;range(1000)&quot;?

PS: Please put code in [Code] blocks to preserve spacing and make it easier to read.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri June 25th, 2010 10:53:33 AM

That first problem reminds me of the &quot;FizzBuzz&quot; test ([url:2mmerbva]http&#58;//www&#46;codinghorror&#46;com/blog/2007/02/why-cant-programmers-program&#46;html[/url:2mmerbva]) which I solved with the following code:

[code:2mmerbva]
&lt;?php

    for ($x = 1; $x &lt;= 100; $x++) {

        if ($x % 3 === 0 &amp;&amp; $x % 5 === 0) {
            echo 'FizzBuzz';
        } elseif ($x % 3 === 0) {
            echo 'Fizz';
        } elseif ($x % 5 === 0) {
            echo 'Buzz';
        } else {
            echo $x;
        }

        echo &quot;&lt;br&gt;&quot;;

    }

?&gt;
[/code:2mmerbva]
