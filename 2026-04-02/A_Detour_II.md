### A Detour Part II

Yesterday I setup freeswitch in a docker container.  It's technically working, but, working from my local machine in docker is proving difficult because of the IP bindings of freeswitch.

I've switched over to using an AWS EC2 instance.

First, I picked a t3.small instance running in us-east-1.  It's priced around $15/month, so it's a good deal with 2vcpu and 2GB RAM.

I picked Debian (Trixie) as the OS and setup the basic security packages and admin tools:

- firewalld
- auditd
- suricata
- aide
- fail2ban

- btop
- lnav
- iftop

- tmux
- git

Then I proceeded to lockdown the SSH daemon by ensuring only public key authentication is enabled, limitting the connection time and number of sessions, and upping the log level from INFO to VERBOSE.

I started this part around 6am and it's now 7am.  I'm going to take a quick break, then come back to setup fail2ban to tighten the banning rules...and maybe also so it uses firewalld and not iptables...although since the fail2ban-firewalld package is not available on Trixie yet it might not be worth the trouble.  Possibly I could use a backport if I setup the backport apt source list, but we'll see what I decide after the break!