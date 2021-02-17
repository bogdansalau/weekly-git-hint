*Git hint of the week:*

Stashing and cleaning

Often, when you’ve been working on part of your project, things are in a messy state and you want
to switch branches for a bit to work on something else. The problem is, you don’t want to do a
commit of half-done work just so you can get back to this point later. The answer to this issue is the
`git stash` command.

Stashing takes the dirty state of your working directory — that is, your modified tracked files and
staged changes — and saves it on a stack of unfinished changes that you can reapply at any time
(even on a different branch).

For stashing use `git stash` or `git stash push`.
To see all the stashes you've created use `git stash list`:
```
$ git stash list
stash@{0}: WIP on master: 049d078 Create index file
stash@{1}: WIP on master: c264051 Revert "Add file_size"
stash@{2}: WIP on master: 21d80a5 Add number to log
```
You can apply stash 2 with `git stash apply stash@{2}`.

If you want an easy way to test the stashed changes again, you can run `git stash branch <new branchname>`,
which creates a new branch with your selected branch name, checks out the commit you
were on when you stashed your work, reapplies your work there, and then drops the stash if it
applies successfully.

Finally, you may not want to stash some work or files in your working directory, but simply get rid
of them; that’s what the `git clean` command is for.

To remove all the untracked files in your working directory, you can run `git clean -f -d`,
which removes any files and also any subdirectories that become empty as a result. The `-f` means
force or “really do this,” and is required if the Git configuration variable `clean.requireForce` is not
explicitly set to false.

If you ever want to see what it would do, you can run the command with the `--dry-run` (or `-n`)
option, which means "do a dry run and tell me what you would have removed".