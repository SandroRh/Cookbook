https://luisdalmolin.dev/blog/ignoring-files-in-git-without-gitignore/

## .gitignore local (não vai para o repositório)
Adicionar no .git/info/exclude

Ex:

```
# git ls-files --others --exclude-from=.git/info/exclude
# Lines that start with '#' are comments.
# For a project mostly in C, the following would be a good set of
# exclude patterns (uncomment them if you want to use them):
# *.[oa]
# *~

app/etc/config.php
```

`git update-index --assume-unchanged app/etc/config.php`: Executar caso o arquivo ainda esteja sendo monitorado pelo git.