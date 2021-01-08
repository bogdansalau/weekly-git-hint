Rebase vs Merge

There are some fundamental differences between a `git rebase` and `git merge` even if they solve the same problem:

`git merge` creates a new "merge commit" that tie together two branches. Merge commits are the only commits that have two parents: the branch containing the feature and the branch it is merged into. Merging does not change the branches in any way.

`git rebase` moves the whole branch that contains the new feature on the tip of the target branch, incorporating all of the new commits into it. Instead of using a merge commit, rebasing rewrites the project history by creating brand new commits for each commit on the feature branch.

The one and only benefit of using a rebase instead of a merge is that the history of the project will be linear thus easier to follow and debug.

Terms and conditions: Do not rebase commits that exist outside your repository and that people may have based work on.