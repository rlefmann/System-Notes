# Working with archives

## Display content

```
tar -tf /path/to/archive.tar
```

You can add the `v` flag for an `ls -l` like output.

Unfortunately it is not easily possible to display only the top level
directory of an archive. We instead have to use `grep` and a regular
expression:

```
tar -tf /path/to/archive.tar | grep "^\./[^/]*.$"
```

This looks complicated. The `^` denotes the start of a line and the `$`
denotes the end of a line. The start of the line is a dot (which must be
escaped), followed by a slash. Then arbitrary characters except for another
slash follow. The last character can be anything including a slash because
top level directories are displayed with a slash after the directory name.

If the command returns more than a single folder, you probably want to
extract it into an empty directory.

## Unpack

Basic usage for `tar` and `tgz` files:

```
tar -xf /path/to/archive.tar
```

`x` is for extract and the `f` denotes that a file will follow.

If you want to extract the files into another directory than the current one,
use the `-C` option:

```
tar -xf /path/to/archive.tar -C /extract/here
```

## Create

```
tar -cf /path/to/archive.tar
```

## Compressed Archives (tar.gz)

Compressed archives with the extension `tar.gz` are filtered through `gzip`. To
work with these you have to additionally use the `z` flag.


## Delete everything but the archive

Use `find` for this task:

```
find . ! -name archive.tar -delete
```
