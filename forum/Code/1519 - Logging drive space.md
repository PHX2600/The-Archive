## Logging drive space
Posted by **XlogicX** on Sun December 18th, 2011 04:49:57 AM

I thought it would be cool if I could have a spreadsheet get automatically populated with the free/used space on my drives on a daily basis. That way I could graph it and do other geeky analysis on my habits.

Not really &quot;code&quot; so much as a one-liner:

```date | awk '{print $1&quot;, &quot;$2&quot;, &quot;$3&quot;, &quot;$4&quot;, &quot;$6&quot;, &quot;}'| head -c -1 | cat &gt;&gt; /home/xlogicx/logs/server_usage&#46;csv; df --total | tail -n 1 | awk '{print $2&quot;, &quot;$3&quot;, &quot;$4&quot;, &quot;$5}' | cat &gt;&gt; /home/xlogicx/logs/server_usage&#46;csv```

server_usage.csv just starts off as a file with the following content:
Weekday, Month, Day, Time, Year, Total, Used, Free, Percentage

Those are the columns, the command populates them. You could use df -h, but I prefer how specific the results are without it. --total is great because it sums up all of my cifs mounted drives on my server; it gives me a good idea of my &quot;total&quot; space left (great info when running a 'poor mans RAID').

So I just added this to my crontab so I can start tracking trends!

Oh, and if I was only concerned with my local disk, I would just use:
```date | awk '{print $1&quot;, &quot;$2&quot;, &quot;$3&quot;, &quot;$4&quot;, &quot;$6&quot;, &quot;}'| head -c -1 | cat &gt;&gt; /home/xlogicx/logs/local_usage&#46;csv; df | grep /dev/sdb1 | awk '{print $2&quot;, &quot;$3&quot;, &quot;$4&quot;, &quot;$5}' | cat &gt;&gt; /home/xlogicx/logs/local_usage&#46;csv```

(Where /dev/sdb1 is my linux drive. Likely to be /dev/sda1 in a box with one drive)

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue December 20th, 2011 02:21:28 PM

This is great, but what do you mean by &quot;poor mans RAID&quot;?

--------------------------------------------------------------------------------

Posted by **XlogicX** on Wed December 21st, 2011 02:47:24 AM

Meaning that I don't run RAID at all. I have around 6 or 7 hard drives in my file server, but they are independent. I configured my fstab to mount them all automatically using cifs (the file server itself is still windows 2003, lol). Being that each drive is mounted, doing a df will show the size of each one (a df -h is more readable). But doing a df --total is cool because it actually adds up all of the drives for a grand total (of total, used, free, and the %).
