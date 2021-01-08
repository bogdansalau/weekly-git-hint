It’s typical to create a new branch and want to switch to that new branch at the same time — this can be done in one operation with `git checkout -b <newbranchname>`.
This is a shorthand for
```
git branch <newbranchname>
git checkout <newbranchname>
```

From Git version 2.23 onwards you can use git switch instead of git checkout to:
• Switch to an existing branch: `git switch <branch_name>`.
• Create a new branch and switch to it: `git switch -c <new_branch_name>`. The -c flag stands for create, you can also use the full flag: `--create`.
• Return to your previously checked out branch: `git switch -`