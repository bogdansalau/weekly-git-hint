*Gint hint of the week:*

Interactive rebasing: change a random commit's message

Commit history example:
```
* 977c8b4 (HEAD -> master) fix typo
* ebcaeb4 update reamde.md
* b638479 update changelog
```
Ugh, there's a typo in the commit `ebcaeb4` message.
`git rebase -i HEAD~3`

Editor pops up with:
```
pick 977c8b4 update changelog
pick ebcaeb4 update reamde.md
pick b638479 fix typo
```
Change `ebcaeb4`'s key from "pick" to "reword" like this:
```
pick 977c8b4 update changelog
reword ebcaeb4 update reamde.md
pick b638479 fix typo
```
Now close the editor. A new editor window pops up with the commit selected for rewording, just like a `git commit --amend`.
Update the commit message and close the editor.
Here's the new commit history:
```
* 977c8b4 (HEAD -> master) fix typo
* a3e95ed update readme.md
* b638479 update changelog
```
Notice the new hash of the commit with the renamed message.

Here's a list with all the `git rebase -i` commands:
```
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
```

