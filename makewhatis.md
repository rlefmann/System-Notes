# Makewhatis

If you execute `makewhatis /usr/share/man` you might get the error message

```
/usr/share/man/mandoc.db: Data changed, but cannot replace database
```

In that case, run the command as root and afterwards change the permissions of the database file `mandoc.db`, such that group and others are allowed to read:

```
sudo chmod go+r /usr/share/man/mandoc.db
```
