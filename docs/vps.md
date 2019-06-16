VPS
As it was pointed out already, storing your emails (actually, storing anything) with a third-party is always risky. The question here is the degree of risk (threat model) and convenience.
The major problem of home hosting is blocked 25 port and stability - if your Internet is down, you will not receive anything. Same with electrical supply.
It is much more convenient (and cheap) these days to purchase a VPS (Virtual Private Server) and host all your emails there. There are a couple of caveats though:
- It is recommended to purchase a KVM VPS
- You can encrypt the hard drive but bear in mind that:
  + you will have to enter the password every time your VPS will be rebooted via SSH/VNC console
  + VPS provider will still be able to access your data
- VPS can also go down. Make sure you pick up a reliable provider with SLA not less than 99% or even more. Check https://uptime.is/

If you are still happy to go with VPS - carry on reading. 
