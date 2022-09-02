Groups
======

##  View the Groups a User Account is Assigned To
```
groups
```
## View all groups on the system
```
getent group
```
or look at the file `/etc/group`.

## Add user to existing group
```
sudo usermod -a -G <groupname> <username>
```

## References

https://www.howtogeek.com/50787/add-a-user-to-a-group-or-second-group-on-linux/
