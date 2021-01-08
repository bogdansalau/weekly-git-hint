Based on the diagram from the last week's tip, let's discuss `git diff`

It’s important to note that git diff by itself doesn’t show all changes made since your last commit, but only changes that are still unstaged.
If you’ve staged all of your changes, `git diff` will give you no output.

If you want to see what you’ve staged that will go into your next commit, you can use `git diff --staged` or `git diff --cached` (staged and cached are synonyms).