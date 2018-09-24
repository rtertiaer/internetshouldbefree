internetshouldbefree
====================

Internet should be free. Pretty simple, no?

# how it works: 
 - clone the ansible codebase to apply to a raspberry pi/similar
 - once deployed, an AP called "Internet should be free" is opened up, serving internet from the Ethernet port
 - offers DHCP lease, DNS and NAT/gateway services
 - blocks ads via `/etc/hosts` thanks to [https://github.com/StevenBlack/hosts/]

# install:
```
# copy 'example_hosts' to  'hosts' and modify it (warning: the default is set to localhost!)
# modify 'vars/default.yml'
sudo apt-get install sshpass libssl-dev libffi-dev python-virtualenv
virtualenv venv
source venv/bin/activate
pip install ansible
ansible-playbook allinone.yml
```

# notes:
 - hosts are expected to be running Debian and to have AP-capable wireless drivers
 - you must supply your own "hosts" file for Ansible in the root of this directory; an example hosts file that configures 127.0.0.1 as an "allinone" host is provided as `example_hosts`. ansible supports provisioning many hosts at once - if you have 5 Pis, put their IP addresses here!
 - if you do not want to use your own username to log into the targets, set the `-u` flag when running `ansible-playbook`
 - the default is to set dynamic WAN addresses with DHCP; however, changing that is simple in the `allinone.yml` file - see the lan side example for a static config.
 - initial implementation doesn't attempt to secure the gateway very much; it also deserves to have firewall rules split out into a less-messy config

# wishlist:
 - organize playbook into actual roles to facilitate reuse
 - before routing traffic publicly, tell the user "internet should be free" and to click "i accept" (propaganda garden)
 - implement QoS to allow userbase to scale well and prioritize non-commercial/latency-sensitive uses
