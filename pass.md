# Pass: The Standard Unix Password Manager

## Create a GPG Key

```
gpg2 --full-generate-key
```

Username: username@computer, e.g. lefmann@desktop

Show GPG key:

```
gpg2 --list-secret-keys --keyid-format LONG
```

## Initialize Pass

```
pass init "gpgkey"
```

where gpgkey is your key. This creates a file `~/.password-store`.

## Add a password

```
pass insert <website-url>
```

## Get a password

```
pass <website-url>
```

For practical purposes, install `passmenu` which opens `dmenu`, you select a website and the password is copied to your clipboard.
