# Configuring a new (network) printer

## Cups

* Install `cups` and `cups-filters`
* Start the cupsd service: `sudo ln -s /etc/sv/cupsd /ver/service`
* Check status of service: `sudo sv status /var/service/cupsd`
* Access web interface: `http://localhost:631/admin`
* Add printer. Most likely `cups` will automatically find the printer.

## Unable to add printer: forbidden

https://ro-che.info/articles/2016-07-08-debugging-cups-forbidden-error

TLDR: add yourself to the `lpadmin` group

```
sudo usermod -a -G lpadmin lefmann
```

## Drivers

1. See what is already available
2. Try a generic driver
3. Gutenprint
4. Foomatic (For non-free drivers, first install `void-repo-nonfree`)
5. Something even more specific

Restart after changing the driver!
