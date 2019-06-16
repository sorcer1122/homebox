VPS
As it was pointed out already, storing your emails (actually, storing anything) with a third-party is always risky. The question here is the degree of risk (threat model) and convenience.
The major problem of home hosting is blocked 25 port and stability - if your Internet is down, you will not receive anything. Same with electrical supply.
It is much more convenient (and cheap) these days to purchase a VPS (Virtual Private Server) and host all your emails there. There are a couple of caveats though:
- It is recommended to purchase a KVM VPS
- You can encrypt the hard drive but bear in mind that:
  + you will have to enter the password every time your VPS will be rebooted via SSH/VNC console
  + VPS provider will still be able to access your data
- VPS can also go down. Make sure you pick up a reliable provider with SLA not less than 99% or even more. Check https://uptime.is/

If you are still happy to go with VPS - carry on reading. First, prepare your A records, it will save you a lot of time. It will depend on the services you want to use, so if you change the default config, you may need more/less A records. I have ended up with the following A records:
- backup
- caldav
- carddav
- imap
- pop3
- ldap
- rspamd
- webmail
- smtp
- www
- main
- sogo
- zabbix

For XMPP you will need -xmpp and -conference A records. Also, remove all the redirection in your DNS panel, it may interfere with ansible (things like http://mydomain.com -> http://www.mydomain.com).

If you have encrypted hard drive: there are various ways to do it, the easiest one is to boot netboot via VNC (not all VPS providers will have this, so check before you buy) and install OS via graphic install. Bear in mind that you will need to unlock your hard drive after you run ansible script (in around 1-2 mins after the script starts). Simply keep VNC open and enter your password thus ansible will not be interrupted.

Also, make sure all A records point to a correct IP address.

After you install OS, boot it and add SSH key: in /root create sub-folder .ssh and inside create a file 'authorized_keys'. Copy your copy of public SSH key from your LOCAL machine into this file and adjust settings in /etc/ssh/sshd_config to enable public key auth. Don't forget to restart ssh service.
