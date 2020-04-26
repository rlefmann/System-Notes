# Groff

## Compile

```
groff -ms doc.ms -T pdf > doc.pdf
```

To have support for umlauts etc:

```
groff -ms doc.ms -D utf-8 -T pdf > doc.pdf
```

Or, even more simple:

```
groff -k -ms doc.ms -T pdf > doc.pdf
```

## Images

If you want your document to include images, you have to provide them in `eps` format. You can use `imagemagick` to compile an image:

```
mogrify -format eps image.png
```

This might not be allowed on your system. If you get an error

```
mogrify: attempt to perform an operation not allowed by the security policy `EPS'
```

you have to allow conversion to `eps` in the file `/etc/ImageMagick-7/policy.xml`.

You can insert an image into a groff file like this:

```
.PSPIC image.eps
```

Additionally, you can specify the justification and size of the image:

```
.PSPIC -L image.eps 1.5i
```

Images are only supported if you output your document to `postscript`:

```
groff -k -ms doc.ms -T ps > doc.ps
```

You can then convert the `postscript` file to `pdf`:

```
ps2pdf doc.ps doc.pdf
```

Note: you could also convert the document with

```
groff -k -ms -mpdfmark doc.ms -T ps > doc.pdf
```

but this results in a lower image quality and you wont be able to copy text from the resulting `pdf`.

## Equations

For equation support, use the `eqn` preprocessor. A guide on how to typeset formulas is Ted Harding: "A Guide to Typesetting Mathematics using GNU eqn".
