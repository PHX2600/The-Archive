## Ghosting across multiple file systems?
Posted by **Automated Penguin** on Mon June 21st, 2010 08:48:00 AM

So I'm in this sort of entry-level Linux Admin position and I have been tasked with putting a dual-boot setup on 100+ machines. 

The problem is Norton ghost doesn't know what ext3 is and so when I ghost a drive which has NTFS and ext3 it will inevitably try to put the files back on an ext2 partition.

I have tried the -IA options in ghost which work by making a bit for bit copy however this means 300gigs+ must be transferred across the network.

I realize this isn't a Linux Users Group but the forums have been so quiet I thought I might as well throw this out there.

Thanks,

-Penguin

Also: Free tours of the ASU Fulton data-center for anyone who wants to stop by my office, GWC 164. Just email me and make sure i know you're coming first.

<!-- e --><a href="mailto:cbock@asu.edu">cbock@asu.edu</a><!-- e -->

--------------------------------------------------------------------------------

Posted by **dxh** on Sat June 26th, 2010 11:22:09 AM

I have no experience with either, but would it be possible to use Clonezilla or Ghost4Linux in lieu of Norton Ghost not working?

--------------------------------------------------------------------------------

Posted by **Automated Penguin** on Mon June 28th, 2010 01:06:01 PM

Those work pretty good and they handle ext3 great but they are both really poor at doing multicast images.

Also ghost for Linux doesn't support some of the more robust networking protocols that I enjoy.

Thanks for the thought though.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Tue June 29th, 2010 10:44:24 AM

Clonezilla was my suggestion as well. :-/
