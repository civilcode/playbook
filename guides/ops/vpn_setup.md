# How to setup the VPN

Setting up the VPN requires:

1. Configure the DNS
2. Configure the router
3. Setup VPN server via VPN Enabler

## Background

Apple [removed the VPN service](https://support.apple.com/en-ca/HT208312) in macOS Server 5.7.1 (Mojave).
The VPN Server is still available on macOS but requires activation. The
[VPN Enabler](https://cutedgesystems.com/software/VPNEnablerForMojave/) third-party software is the
easiest way to activate it.

## Confiture the DNS

Setup a domain to access the DNS on [DNSimple](https://dnsimple.com/). See 1Password for the
domain to use.

## Configure the Router

The router needs ports forwarded to the machine hosting the VPN server.

1. Login into the router (see 1Password)
2. Go to: _Expert Mode &gt; Configuration (cog icon)_

### Reserve IP address for server in the DHCP

1. Go to _Network &gt; DHCP Server &gt; Client List_
2. Reserve the IP address or set them. We now have _192.168.0.5_ reserved for `quebec.local`

### Setup the router

1. Go to _Network &gt; NAT &gt; Port Forwarding_
2. Add Nat Port forwarding rules targeting the VPN server

  ```text
  - UDP 500 to 192.168.0.5
  - UDP 4500 to 192.168.0.5
  - UDP 1701 to 192.168.0.5
  ```

### Setup VPN server

1. Download [VPN Enabler](https://cutedgesystems.com/software/VPNEnablerForMojave/); the software
   license is in 1Password.
2. Move the file into `Applications` and start the program
3. Follow the instructions for all three steps (Step 4. was completed above, router config)

It is recommended to restart the computer after installation. After the initial installation,
clients had connection problems. After a restart, these were resolved.

### Distribute the VPN config file

1. Use VPN Enabler to "Create Config Profile" for each user. (create a unique password for each user)
2. Forward the config file to each user.

### Setup Client

1. Save and click on the config file sent.
2. Save the profile
3. Open Network Preferences, and connect to the VPN profile added
4. Under `Advanced...` options check "Send all traffic over VPN connection"

## Troubleshoot

* on the server: `tail -f /var/log/ppp/vpnd/log`
* on the client: open the `Console` utility and filter on `vpn` or `vpnkit`
* the VPN connection only works outside of the network, otherwise will drop UDP request \(`Dropping TTL exceeded..`\)

Enjoy Canadian privacy!
