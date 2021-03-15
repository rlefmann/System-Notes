Creating an EPUB file
=====================

## Setting up the folder structure

* Create a new directory `sample`
* In that directory create a file `mimetype` with the content `application/epub+zip`
* Create directories `META-INF` and `OEBPS`


## Compress

Use the program `zip`. Navigate into the directory where your files reside.

```
zip -rX0 ../test.epub *
```

The flag `-0` disables compression, while the `-X` flag prevents `zip` from storing additional mimetype information that confuses EPUB readers.

Unfortunately this still does not work because the mimetype file has to be the first file inside the archive. You have to add the mimetypes file explicitely as the first file to the archive:

```
zip -X0 ../test.epub mimetype
zip -r0 ../test.epub META-INF OEBPS
```

Now, we are done and you can try to open your EPUB file.
