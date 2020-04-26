# Minimize PDF size

You can use `Ghostscript` to reduce the file size of a pdf document (while reducing its quality).

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=out.pdf in.pdf
```
