*Gint hint of the week:*

Interactive rebasing: squash commits (squash = combine)

In order to keep a clean history, squashing commits is recommended before each MR.
This can be achieved with `git rebase -i <chronological first commit>` which can squash every commit between the current location of the HEAD and the `<first commit>`.

Commit history example:
```
* 977c8b4 (HEAD -> master) fix typo
* ebcaeb4 update readme.md
* b638479 update changelog
```

We want our history to look professional so we would like to combine the "fix typo" commit with the others. Actually, let's squash all of them into one.
`git rebase -i HEAD~3` 

After executing the command this would appear in the editor:
```
pick b638479 update changelog
pick ebcaeb4 update readme.md
pick 977c8b4 fix typo
```
which we will change to:
```
pick b638479 update changelog
squash ebcaeb4 update readme.md
squash 977c8b4 fix typo
```
There must be at least one "pick" commit to squash into.
Git will combine the commits and display a new editor file for a new commit.
In here we can rename the commit message from:
```
# This is a combination of 3 commits.
# This is the 1st commit message:

update changelog

# This is the commit message #2:

update readme.md

# This is the commit message #3:

fix typo
```
to:
```
# This is a combination of 3 commits.
# This is the 1st commit message:

update changelog, readme

# This is the commit message #2:

update readme.md

# This is the commit message #3:

fix typo
```
After saving and closing the editor here's the new commit history:
`* 3b0c43f (HEAD -> master) update changelog`
Notice that the new commit hash is different from the initial "update changelog" commit.
