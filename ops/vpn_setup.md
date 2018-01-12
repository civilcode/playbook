## Reserve IP address for server
192.168.0.5 for "quebec**
## Setup Videotron router
Add Nat Port forwarding rules
- UDP 500 to 192.168.0.5
- UDP 4500 to 192.168.0.5
- UDP 1701 to 192.168.0.5
## Setup VPN server via MacOS Server
VPN > ?
Setup with a shared secret. That's the password that will be used to connect to the VPN
## Add User via MacOS Server
Users > +
## Distribute the VPN config file
VPN > Configuration Profile > Save
The VPN file is hosted on 1password
## Setup Client
### Manually
### Via the config file
