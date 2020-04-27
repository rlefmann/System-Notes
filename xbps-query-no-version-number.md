# List all Packages installed by the User Without Version Number

You can list all of your explicitly installed packages using `xbps-query -m`, but the output contains the version number of each of these packages. We can use `rev` and `cut` to get a list of installed packages without their version number:

```
xbps-query -m | rev | cut -d '-' -f 2- | rev
```

Cut can only use field numbers from the left, so we must reverse each line first, then we output only the second to last field and reverse the lines again.
