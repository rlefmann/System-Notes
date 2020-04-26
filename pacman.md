# Pacman Package Manager

## Install Packages

Search for package:

```
pacman -Ss <pkgname>
```

Install package:

```
sudo pacman -S <pkgname>
```

## Installed packages

List installed packages:

```
pacman -Q
```

More details:

```
pacman -Qi
```

Search for specific package. Searches the name and the description:

```
pacman -Qs <query>
```

Show list of files installed by a package:

```
pacman -Ql <pkgname>
```

Create an alphabetic list of the installed packages:

```
pacman -Qqen > pkglist.txt
```

List recently installed packages (newest at the bottom):

```
cat /var/log/pacman.log | grep "installed"
```

List all installed packages by size:

```
expac "%n %m" -l'\n' -Q $(pacman -Qq) | sort -rhk 2 | less
```

## Remove Packages

```
pacman -Rs <pkgname>
```

This also removes all dependencies that were not explicitely installed. If you want to uninstall all dependencies, you can instead use the `-Rss` option.
