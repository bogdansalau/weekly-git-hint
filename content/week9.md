*Gint hint of the week:*

Commit message formatting is one of the small details that makes Git great.

By using `git commit -m "<comment here>"` we are creating a one-line commit message. This is just the tip of the iceberg. By using `git commit` without the `-m` flag, the editor linked to the `.gitconfig` file will open.

In the editor we will be able to add longer commit messages. Here’s a Git commit message model:

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here
```

By using this feature we can comment in detail why certain changes were made and the comment will stick to the commit. 

When using `git log --pretty=oneline` only the summary of the commits will be shown.
To check the last commit's full comment use `git log -1 --pretty=%B`.
To check a commit's full comment use `git log <commit_hash>`.