`git rerere` is a feature that is probably among the less known features of git. What does it do you ask?
It records conflicts you encounter and your solutions to them.
This way you will only need to resolve the conflicts once - your resolution will be stored in an `rr-cache`.
The next time you encounter a conflict, git will look through that `rr-cache` if you resolved that exact conflict some time in the past already and will apply the same resolution to it again.
To enable the feature, simply use the following setting:
`git config --global rerere.autoupdate true`

To find more details on rerere check out this link that I found rather informative: https://levelup.gitconnected.com/the-git-rerere-command-automate-solutions-to-fix-merge-conflicts-d501a9ab9007

PS: rerere stands for "reuse recorded resolution". I find it funny on how its simply the letters "re" repeated 3 times - while repeating work is exactly what rerere should avoid