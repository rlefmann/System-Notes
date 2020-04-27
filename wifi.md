# Setting up Wifi from the command line

## Control the wifi interface

View available network interfaces on your computer:

```
sudo ip link show
```

The wifi interface is typically called `wlp3s0`.

* Enable wifi: `sudo ip link set up wlp3s0`
* Disable wifi: `sudo ip link set down wlp3s0`


## View available networks

```
sudo iw dev wlp3s0 scan | grep "SSID:"
```

## Create a configuration file (wpa network)

```
wpa_passphrase 'ssid' password > path/to/configuration/file.conf
```


## Connect

```
sudo wpa_supplicant -B -i wlp3s0 -c <path/to/configuration/file>
sudo dhcpcd wlp3s0
```

## Disconnect

```
sudo killall wpa_supplicant
```
