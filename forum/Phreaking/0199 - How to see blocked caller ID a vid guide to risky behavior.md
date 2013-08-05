## How to see blocked caller ID: a vid guide to risky behavior
Posted by **Ghostshell** on Thu August 7th, 2008 08:39:12 AM

<http://www.engadget.com/2008/07/21/how-to-reveal-blocked-caller-id-info-a-video-guide-to-risky-beh/>

In a demonstration video, a hacker tweaks said asterisk box with some new
configurations to strip out privacy flags, forward the call to another number,
and ultimately reveal caller ID information which, surprisingly, is still
available.

--------------------------------------------------------------------------------

Posted by **Problem Child** on Sun October 12th, 2008 09:28:22 PM

This is a serious flaw in flowroute's platform.  I don't think it has anything
to do with being "Entperprise Class" and it surely isn't intentional that
flowroute is sending P-Asserted Identity information to the SIP endpoint! :lol:
Their platform is functioning more like a SIP proxy and less like a back to back
user agent.

Here is my theory on how this is possible: The originating party calls from the
PSTN towards the SIP network with *67, the media gateway is sending the
P-Asserted info in the SIP Invite towards flowroute's SIP platform, and then
flowroute's SIP registrar/location server sends the SIP Invite to Asterisk with
all the original information and includes the P-Asserted identiy because the
device is provisioned using "SIP Connect" trunking.  This is where flowroute's
platform has it all wrong, because their registrar's SIP invite should be
originated towards the destination SIP endpoint (Asterisk) where the From and
Contact URI would show something like anonmyous@anonymous.invalid and
anononymous@<IP Address>:5060;transport=udp. P-Asserted shouldn't even be there!

In theory, you could use more than just Asterisk for this.  Any SIP endpoint
that supports SIP header manipulation could accomplish this.

--------------------------------------------------------------------------------

Posted by **Ugly** on Tue October 14th, 2008 12:02:37 AM

> Here is my theory on how this is possible: The originating party calls from
> the PSTN towards the SIP network with *67, the media gateway is sending the
> P-Asserted info in the SIP Invite towards flowroute's SIP platform, and then
> flowroute's SIP registrar/location server sends the SIP Invite to Asterisk
> with all the original information and includes the P-Asserted identiy because
> the device is provisioned using "SIP Connect" trunking. This is where
> flowroute's platform has it all wrong, because their registrar's SIP invite
> should be originated towards the destination SIP endpoint (Asterisk) where the
> From and Contact URI would show something like anonmyous@anonymous.invalid and
> anononymous@<IP Address>:5060;transport=udp. P-Asserted shouldn't even be
> there!

...magic, got it.
