# Bulk Rename Files Using VIM

```
\ls | vim -
```

The backslash tells your shell to disregard any aliases for ls; we need plain output with no color.

```
:%s/.*/mv & &/g
```

Now you can change the destination name for each file.
To remove the highlighting, type `:noh`

When finished, execute

```
:w !sh
```

