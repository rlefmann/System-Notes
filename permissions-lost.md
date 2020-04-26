# Regain permission for file

Sometimes it can happen that you accidentally lose the permissions to open or edit a file. In particular, this could happen if you do some data rescue work as root user.

You can regain the permissions using

```
sudo chown -R <username> /pfad/zum/ordner
```
