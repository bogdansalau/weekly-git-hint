*Git hint of the week:*

Git Search

Git ships with a command called `grep` that allows you to easily search through any committed tree,
the working directory, or even the index for a string or regular expression. 

By default, git grep will look through the files in your working directory. As a first variation, you
can use either of the -n or --line-number options to print out the line numbers where Git has found
matches

`git grep` can also be used with the `-c` or `--count` flag to show how many matches there were in each file.

Git log search

If, for example, we want to find out when the `MAX_NR_USERS` constant was originally introduced we can use 
the `-S` option (colloquially referred to as the Git "pickaxe" option) to tell Git to show us only
those commits that changed the number of occurrences of that string.

`git log -S MAX_NR_USERS --oneline` can output something like:
```
e01503b add constants
ef49a7a split users constants per module
```
