*Git hint of the week:*

Binary search on the commit history

You find a bug in production and you don't know where it came from. You could check each commit from the history starting with the HEAD to find the commit that broke the build but if you have dozens of commits you're constrained to use `git bisect`.
 
First, run `git bisect start` just to get things going, then you use `git bisect bad` to tell the system that the current commit you're on is broken. After that, you must tell bisect when was the last known good state using `git bisect good <good_commit>`. The HEAD will automatically move to the middle commit between the good one and the bad one. Check if it's a good version and mark it accordingly with `git bisect good/bad`.

After doing this a couple of times you will be told by git what commit is the bad one. Use `git bisect reset` to reset your HEAD to where you were before you started.

Bisect is a powerful tool that can help you check hundreds of commits for an introduced bug in minutes. By mentioning the bad and the first good commit in the `git bisect start` we can then apply a script that automates the testing process, just like this:
```
git bisect start HEAD v1.0 //git bisect start <bad_commit> <good_commit>
git bisect run test-error.sh
```