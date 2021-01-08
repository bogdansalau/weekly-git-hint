Here is a diagram with all the states in which a file can be found in a git repo.
When we execute `git status`, files that are in the Untracked, Modified and Staged states are shown.
Files included in the `.gitignore` are excluded when Untracked files are displayed.

Using `git add <filepath>` makes any file Staged. Only staged files can be included in a commit.