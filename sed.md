# sed

## Basic regular expressions

* `^` indicates the beginning of the line
* `$` indicates the end gof the line
* `\s` indicates whitespace (`s/\s*$//` removes trailing space)
* `[0-9]`: all numeric characters
* `[a-z]`: all lowercase characters
* `[a-zA-Z]`: all letters (warning: `[A-z]` is **not** the same)
* `[^0-9]`: every character except numeric characters
* `&`: matched string
* If you want to include a closing square bracket in a list, make it the first character
* `\w` indicates a word character; that is it matches any letter or digit or the underscore character

More information on regular expressions: `man 7 regex`


## Ampersand denotes matched string

Put parentheses around each numeric character:

```
sed 's/[0-9]/(&)/g' file
```

Put parentheses around each number:

```
sed 's/[0-9][0-9]*/(&)/g file
```


## Character classes

Character classes have to be enclosed in double square brackets, e.g.:

* `[[:alnum:]]`
* `[[:space:]]`


## Boundaries

Boundaries ensure a whole word match. Example:
```
sed 's/\bnew\b/old/g
```
* replaces every instance of `new` with `old`
* does not replace instances of `newer` with `older`.


## Replace more than one string

Simply write more than one replace command and separate them by semicolons.


# Run a command for certain lines only

* `sed '3,$ d' file` deletes all lines, starting at line 3.
* `sed '3 q' file` displays the first 3 lines and then quits
* Run a command only for certain lines: `sed '2,${/^#/d} file`
* Remove comments but do not remove shebang line: `sed '/^#!/! {/^#/d}' test`


## Useful flags

* `-n` suppress automatic printing of every line. Only print lines where it is explicitely requested via the `p` command (similar to `grep`). Example: `sed -n '/regexp/p' file`
* `-i` files are edited in-place
* `-E` use extended regular expressions
* `-I` ignore the case of the regex. Example: `sed 's/that/*/Ig' file` replaces `that`, `That`, `ThAt`, etc. with an asterisk.
