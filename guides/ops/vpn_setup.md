# How to setup the VPN

## Router

* login to the router admin interface on [http://192.168.0.1](http://192.168.0.1)
* Go to _Expert mode_ \(up right\)
* Click on the cog on the left bar menu

### Reserve IP address for server in the DHCP

* Go to _Network &gt; DHCP Server &gt; Client List_

  Reserve the ips address or set them.

  We now have _192.168.0.5_ reserved for `quebec.local`

### Setup Videotron router

* Go to _Network &gt; NAT &gt; Port Forwarding_
* Add Nat Port forwarding rules targetting the VPN server

  ```text
  - UDP 500 to 192.168.0.5
  - UDP 4500 to 192.168.0.5
  - UDP 1701 to 192.168.0.5
  ```

### Setup VPN server via MacOS Server

Setup with a shared secret. That's the password that will be used to connect to the VPN

* Buy and install MacOS Server. Launch it
* Choose "This Mac" to manage its services 
* Go to VPN
* Fill the VPN settings

  ```text
  VPN Host Name: vpn.civilcode.io  
  Shared Secret: password used to connect to the VPN  
  Client address: limit number of connections to the VPN (10)
  ```

  The Status should read "Reachable over the Internet at "

### Add User via MacOS Server

The users of the system are the ones that will be allowed to connect by default. The list of allowed users can be limited. In MacOS Server, go to Account and add new users

### Distribute the VPN config file

In MacOS Server &gt; VPN:

* Save the profile in the Configuration Profile field \(default name: _VPN.config\_mobile_\)
* Share it to your peers

### Setup Client

#### Via the config file

The config file can be found in 1password in the Shared vault under _VPN.config\_mobile_.

* Save and click on the configuration file
* Save the profile
* Enter your credentials set at on the VPN server \(eg _johndoe_\)
* Open Network Preferences, and connect to the VPN profile added

#### Manually

* Open Network Preferences
* create a connection profile for VPN with a IKEv2 or L2TPE protocol

  -- _Server Address_: vpn.civilcode.io

  _\_ Account Name: enter the user account name that has been created on the server \(eg: \_johndoe_\)

## Troubleshoot

* on the server: `tail -f /var/log/ppp/vpnd/log`
* on the client: open the `Console` utility and filter on `vpn` or `vpnkit`
* the VPN connection only works outside of the network, otherwise will drop UDP request \(`Dropping TTL exceeded..`\)

Enjoy Canadian privacy!

