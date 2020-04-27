# Setup printer connected to speedport

This is a guide on how to setup a printer that is connected via usb to a router. In my case, it is a `HP LaserJet 1220` connected to a `Telekom Speedport` router.

## Install Programs

* cups
* samba
* samba-cups
* cups-filters
* cups-pdf

```
xi cups samba samba-cups cups-filters cups-pdf
```


## Start Service

sudo usermod -a -G lpadmin christine
sudo ln -s /etc/sv/cupsd /var/service

Restart. You can now navigate to `localhost:631` to configure printers. We use the command-line tool `lpadmin`, instead.


## Configure Printer

```
lpadmin -p HP-Laserjet-1220 -E -v smb://speedport.ip/HewLettPackardHPLaserJet122 -m drv:///sample.drv/laserjet.ppd -o auth-info-required=username,password
```

The list of available drivers (ppd files) can be obtained by `lpinfo -m`.

Other things to try:

* Add `-U username` where username is the login of the router
* Try `auth-info-required=negotiate`

You can now see the printer in the web interface or query its status information using

```
lpstat -p HP-Laserjet-1220 -t
```

Change the default settings to A4-paper and 600dpi using the web interface.

Now you should be able to print. When printing, you will be asked for the router's login credentials.


## Other things that might be helpful

Start SAMBA service

Edit /etc/samba/smb.conf

Under section `[printers]`, add:

```
guest ok = yes
print ok = yes
```

sudo ln -s /etc/sv/smbd /var/service

Install cifs-utils
Install smbclient
