# Compile programs / files from within vim

## LaTeX

Compile using F2 key:

```
map <F2> :w<CR>:cd %:p:h<CR>:! pdflatex %<CR><CR>
```

The first command saves the file. The second changes into the directory of the file such that the output file is written to the same directory. The third command executes `pdflatex` on the file.

To only use the F2 command for `tex` files, start the line with

```
autocmd FileType tex map <F2> :w<CR>:cd %:p:h<CR>:! pdflatex %<CR><CR>
```

## Markdown with pandoc

```
autocmd FileType md map <F2> :w<CR>:cd %:p:h<CR>:! pandoc -i % -o %:r.pdf<CR><CR>
```
