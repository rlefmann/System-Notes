# Bash prompt

To change the bash prompt, add a line that looks like

```
PS1="$ "
```

to the end of `~/.bashrc`. You have to replace the string with a format string describing how you want your prompt to look like.

This is my standard prompt:

```
PS1="\n\$(if [[ \$? == 0 ]]; then echo \"\[\033[1;34m\]\"; else echo \"\[\033[0;31m\]\"; fi)\342\226\210\342\226\210 [ \u ] [ \W ]\n\[\033[0m\]\342\226\210\342\226\210 "
```

Nice alternative:

```
PS1="\033[01;34m┌──[\D{%d-%m-%Y %H:%M:%S}] \033[01;39m[\u@\h] \w \033[03;34m\n└──[\$] → \[\033[00m\]"
```
