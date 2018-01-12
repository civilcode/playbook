# Router
- login to the router admin interface on http://192.168.0.1
- Go to _Expert mode_ (up right)
- Click on the cog on the left bar menu

## Reserve IP address for server in the DHCP
- Go to _Network > DHCP Server > Client List_
Reserve the ips address or set them.
We now have _192.168.0.5_ reserved for `quebec.local`

## Setup Videotron router
- Go to _Network > NAT > Port Forwarding_
- Add Nat Port forwarding rules targetting the VPN server
-- UDP 500 to 192.168.0.5
-- UDP 4500 to 192.168.0.5
-- UDP 1701 to 192.168.0.5


## Setup VPN server via MacOS Server
Setup with a shared secret. That's the password that will be used to connect to the VPN
- Buy and install MacOS Server. Launch it
- Choose "This Mac" to manage its services 
- Go to VPN
- Fill the VPN settings
*VPN Host Name*: vpn.civilcode.io
*Shared Secret*: password used to connect to the VPN
*Client address*: limit number of connections to the VPN (10)

The Status should read "Reachable over the Internet at <ip>"

## Add User via MacOS Server
The users of the system are the ones that will be allowed to connect by default. The list of allowed users can be limited.
In MacOS Server, go to Account and add new users


## Distribute the VPN config file
In MacOS Server > VPN:
- Save the profile in the Configuration Profile field (default name: _VPN.config_mobile_)
- Share it to your peers

## Setup Client
### Via the config file
- Save and click on the configuration file
- Save the profile
- Enter your credentials set at on the VPN server (eg _johndoe_)
- Open Network Preferences, and connect to the VPN profile added

### Manually
- Open Network Preferences
- create a connection profile for VPN with a IKEv2 or L2TPE protocol
-- *Server Address*: vpn.civilcode.io
__ *Account Name*: enter the user account name that has been created on the server (eg: _johndoe_)


Enjoy Canadian privacy! 
