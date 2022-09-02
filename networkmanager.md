NetworkManager
==============

## Installation

Install packages `NetworkManager`. If you want to use a status bar applet, also install `network-manager-applet`.

## Setup

Users of `NetworkManager` must belong to the `network` group.
```
groups <username>
# if not in network group:
usermod -a -G network lefmann
```

Before enabling the NetworkManager daemon, disable any other network management services, such as dhcpcd, wpa_supplicant, or wicd. These services all control network interface configuration, and will interfere with NetworkManager. Example:
```
sudo rm /var/service/dhcpcd
```
Also ensure that the dbus service is enabled and running. NetworkManager uses dbus to expose networking information and a control interface to clients, and will fail to start without it.
```
sudo sv status dbus
## if not running:
sudo ln -s /etc/sv/dbus /var/service/
```

Finally, enable the NetworkManager service.
```
sudo ln -s /etc/sv/NetworkManager /var/service/
```


## Not authorized to control networking

Rather than adding polkit, you can enable all users to edit connections without another service running by making a NetworkManager configuration change:

```
mkdir -p /etc/NetworkManager/conf.d
```
create `any-user.conf` within `conf.d` and include within:
```
[main]
auth-polkit=false
```
Restart NM:
```
sv restart NetworkManager
```
After that, any user will be able to add, edit or activate connections.

## References

https://docs.voidlinux.org/config/network/networkmanager.html
https://www.reddit.com/r/voidlinux/comments/ua2hv5/networkmanager_not_authorized_to_control/
