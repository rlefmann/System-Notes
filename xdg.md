xdg-utils
=========

Check filetype for a file:

```
xdg-mime query filetype wallpaper.png
```

Check default for a filetype:

```
xdg-mime query default image/png
```

This is a `desktop` file.


## Desktop files

Desktop files are located in one of the following directories:

* `/usr/share/applications`
* `~/.local/share/applications`

You can add your own desktop files to the latter directory, e.g. `img.desktop`:

```
[Desktop Entry]
Type=Application
Name=Image Viewer
Exec=sxiv %f
```

Another example for text files:

```
[Desktop Entry]
Type=Application
Name=Text Editor
Exec=alacritty -e kak %u
```


## Changing the default application

There are two methods:

* `xdg-mime default img.desktop image/png`
* Edit the default applications section of `~/.config/mimeapps.lst`
