## Peaceful cruise through Xian Jiaotong University
Posted by **XlogicX** on Sat October 8th, 2011 07:19:19 AM

So uh, I got bored and decided to check out my auth.log's for people trying to haxor my ssh and found an interesting one from a Chinese university computer. Guy was trying to brute force the hell out of my ssh with various usernames and such.

IP: 202.117.1.174.

the nmap -sV was cool:
PORT      STATE    SERVICE            VERSION
21/tcp    open     ftp                vsftpd 2.0.1
22/tcp    open     ssh                OpenSSH 3.9p1 (protocol 1.99)
25/tcp    filtered smtp
80/tcp    open     http               Apache httpd 2.2.9 ((Unix) DAV/2)
111/tcp   open     rpcbind
113/tcp   filtered auth
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
593/tcp   filtered http-rpc-epmap
646/tcp   open     rpcbind
1025/tcp  filtered NFS-or-IIS
1111/tcp  open     unknown
1433/tcp  filtered ms-sql-s
1434/tcp  filtered ms-sql-m
1521/tcp  open     oracle-tns         Oracle TNS Listener 10.2.0.1.0 (for Linux)
1935/tcp  open     http               Apache httpd 2.2.9 ((Unix) DAV/2)
4444/tcp  filtered krb524
4662/tcp  filtered edonkey
4899/tcp  filtered radmin
5801/tcp  open     vnc-http           RealVNC 4.0 (Resolution 400x250; VNC TCP port: 5901)
5901/tcp  open     vnc                VNC (protocol 3.8)
6001/tcp  open     X11                (access denied)
6129/tcp  filtered unknown
6667/tcp  filtered irc
6881/tcp  filtered bittorrent-tracker
8008/tcp  filtered http
8009/tcp  open     ajp13              Apache Jserv (Protocol v1.3)
8080/tcp  open     http               Apache Tomcat/Coyote JSP engine 1.1
9898/tcp  filtered unknown
11111/tcp filtered unknown


8080 was accessible, congrats on setting up your Apache Tomcat server. VNC was legit, I didn't have password, but it sure did prompt. Would like to see what they're sharing through edonkey (didn't get around to that). What's on port 80 is weird though, its video footage of a drive through the campus (34.248277,108.982676 I believe). Anyway, this guy is either botted (with all those glorious open ports) or it's a flagrant misuse of university property.

I know there are other great nuggets out there, but thought this one was weird and decided to share.
