# Merge pdf files

Merge several pdf files to one pdf result file `output.pdf`.

## Using ghostscript

```
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -dAutoRotatePages=/None -sOutputFile=output.pdf file1.pdf file2.pdf
```

## Using pdfunite

`pdfunite` is part of the `poppler-utils` pdf rendering utilities.

```
pdfunite file1.pdf file2.pdf output.pdf
```
