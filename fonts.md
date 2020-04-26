# Fonts

## Installing fonts

Copy the font files into the font directory. For `ttf` fonts this directory is

```
/usr/share/fonts/truetype
```

and for `otf` it is

```
/usr/share/fonts/opentype
```

Afterwards execute

```
sudo fc-cache -f -v
```

## Set default fonts

Create a file `.config/fontconfig/fonts.conf` with the following content:

```xml
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>

	<alias>
		<family>serif</family>
		<prefer><family>Ubuntu</family></prefer>
	</alias>
	<alias>
		<family>sans-serif</family>
		<prefer><family>Ubuntu</family></prefer>
	</alias>
	<alias>
		<family>sans</family>
		<prefer><family>Ubuntu</family></prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer><family>Ubuntu Mono</family></prefer>
	</alias>
</fontconfig>
```
