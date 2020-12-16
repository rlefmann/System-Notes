Delete file from within zathura
===============================

I often download a pdf file with firefox. I then open it in zathura by pressing the downloads toolbar button and clicking on the file.

I then often notice that it was not the file I was looking for.
You can delete the file from within zathura by pressing colon and entering the command

```
exec rm $FILE
```
