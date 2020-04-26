# Crack PDF Password

If you forgot the password of a PDF document, but still know parts of it, you can generate a list of potential passwords using regular expression expansion and then use pdfcrack to find the correct password. Example:

```
echo {j,J}ulian{o,}{ws,WS,ss,SS}{0,1}{0..9}{0,1}{0..9} | tr " " "\n" > passwordlist.txt
pdfcrack -f unfallversicherung.pdf -w passwordlist.txt
```

The `tr` command replaces spaces with newlines because `pdfcrack` requires a passwordlist with one password per line.
