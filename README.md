internetshouldbefree
====================

Internet should be free. Pretty simple, no?

# vision: 
 - an ansible-deployable codebase to flash onto a raspberry pi/similar
 - AP called "Internet should be free"
 - when connected, offers dhcp lease, pointing to gateway and dns server (TODO: that returns No Such Record for advertising domains)
 - TODO: before routing traffic publicly, tell the user "internet should be free" and to click "i accept" (propaganda garden)
 - TODO: implement QoS to allow userbase to scale well and prioritize non-commercial uses

# install:
```
apt-get install sshpass libssl-dev libffi-dev
virtualenv venv
source venv/bin/activate
pip install ansible

```

# notes:
 - you must supply your own "hosts" file in the root of this directory; an example hosts file that configures 127.0.0.1 as an "allinone" host is provided as `example_hosts`
 - you must create a user named "deploy" that can sudo, or change the username value in the `allinone.yml` file
 - initial implementation doesn't attempt to secure the gateway very much; it also deserves to have firewall rules split out into a less-messy config
