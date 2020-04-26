# Working with vim

* `;` repeats the previous command

## Enter Insert Mode

* `i`: Enter insert mode at current position
* `I`: Enter insert mode at the start of the line
* `a`: Enter insert mode at the end of the line
* `o`: Enter insert mode at a new line below the current line

## Navigation

* Move around using the `hjkl` keys (or the arrow keys)
* `^` or `0`: go to beginning of current line
* `$`: go to end of current line
* Move to part of the screen with capital `H` (high), capital `M` (middle), or capital `L` (low)
* `Ctrl+D` moves the current line to the top of the screen
* `Ctrl+U` moves the current line to the bottom of the screen
* `{` moves up a paragraph, `}` moves down a paragraph
* `f+Char` moves to the next character Char, e.g. `fn` moves to the next n in the line
* `*` jumps to the next occurence of the current word, `#` jumps to the previous occurence of the current word
* Go to a specific line: `Num+G`, e.g `320G`

## Searching

* `/word` searches forward
* `?word` searches backward
* You can use the search feature to navigate the document

## Search and replace

In the complete document:

```
:%s/foo/bar/gc
```

From the current position until the end of the document:

```
:.,$s/foo/bar/gc
```

Remove the `c` if you don't want to confirm every replacement.

## Selecting Stuff

The same commands work for copying, e.g. `y$` instead of `v$`

* typing lowercase `v` enters visual mode
* typing uppercase `V` enters line visual mode
* `viw` selects the current word
* `vap` or `vip` selects the whole paragraph
* `vi(` selects everything within parentheses
* `va(` selects everything within the parentheses, including the parentheses themselves
* `v$` selects everything until the end of the line


## Various useful commands

* `:e` reloads the current file


## Line Numbers

```
:set number
```

## Tab width

The default tab width is 8 spaces. To reduce that to 4:

```
:set tabstop=4
```


## Resources

A good resource for questions on vim can be found in the [vim faqs](http://vimdoc.sourceforge.net/cgi-bin/vimfaq2html3.pl).
