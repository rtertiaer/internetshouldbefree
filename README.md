internetshouldbefree
====================

Internet should be free. Pretty simple, no?

# how it works: 
 - clone the ansible codebase to apply to a raspberry pi/similar
 - once deployed, an AP called "Internet should be free" is opened up, serving internet from the Ethernet port
 - offers DHCP lease, DNS and NAT/gateway services

# install:
```
# modify 'hosts' file
apt-get install sshpass libssl-dev libffi-dev
virtualenv venv
source venv/bin/activate
pip install ansible
ansible-playbook allinone.yml
```

# notes:
 - hosts are expected to be running Debian and to have Broadcom wireless drivers
 - you must supply your own "hosts" file in the root of this directory; an example hosts file that configures 127.0.0.1 as an "allinone" host is provided as `example_hosts`. ansible supports provisioning many hosts at once - if you have 5 Pis, put their IP addresses here!
 - you must create a user named "deploy" that can sudo, or change the username value in the `allinone.yml` file
 - initial implementation doesn't attempt to secure the gateway very much; it also deserves to have firewall rules split out into a less-messy config

# wishlist:
 - implement ad-blocking at the DNS server a-la PiHole
 - before routing traffic publicly, tell the user "internet should be free" and to click "i accept" (propaganda garden)
 - implement QoS to allow userbase to scale well and prioritize non-commercial/latency-sensitive uses
