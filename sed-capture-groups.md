## sed capture groups

Here is a simple example:

```
$ echo 'abcabcabc' | sed 's/\(ab\)c/\1/'
ababcabc
$ echo 'abcabcabc' | sed 's/\(ab\)c/\1/g'
ababab
$ echo 'abcabcabc' | sed 's/\(ab\)\(c\)/\1d\2/g'
abdcabdcabdc
```

In the first command, only the first match is affected. In the second command, every match is affected. In both cases, the `\1` refers to the characters captured by the escaped parentheses.

In the third command, two capture groups are specified. They are referred to by using `\1` and `\2`. Up to nine capture groups can be used.

In addition to the `g` (global) operator (or without it, the first match), you can specify a particular match:

```
$ echo 'aaaaaa' | sed 's/a/A/4'
aaaAaa
```
