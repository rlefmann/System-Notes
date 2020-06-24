# Convert between image file formats using Imagemagick

## Basic conversion

```
convert in.png out.tif
```

## Change colorspace

```
convert in.png -colorspace CMYK out.tif
```

Note: png doesnt support cmyk colorspace, therefore we have to convert to tiff (or jpg).

Check colorspace:

```
identify -verbose file | grep Colorspace
```

## Profiles

You can preview different profiles in gimp. See: https://www.saxoprint.de/blog/laden-icc-profil-gimp

Print profiles for PDF output can be downloaded from the Adobe website:

https://www.adobe.com/support/downloads/iccprofiles/iccprofiles_win.html

A good choice is probably `USWebCoatedSWOP.icc`.

`-profile` adds a profile to the image file
`+profile` removes a profile
`-strip` removes any profiles (and comments) from the image

```
convert in.tif -profile ./Adobe-Profiles/CMYK/USWebCoatedSWOP.icc out.pdf
```

Note: the way the result looks in your PDF viewer is not an accurate representation of what it looks like when printed. It depends on the implementation of the viewer and whether it even takes profiles into account.

## Check resolution

```
identify -verbose file | grep Resolution
```

This resolution might not be dpi (dots per inch), but dots per centimeter instead, depending on your locale.
