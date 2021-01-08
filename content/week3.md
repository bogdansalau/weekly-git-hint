Sometimes you just want to check out a single file of another commit. You can do that like this:
`git checkout master -- path/to/file1.java path/to/file2.java`

Notice the double-dash in there. Also, there is a space before and after the dashes.

This will not actually checkout the master branch - it will only take this specific file from the master branch and apply it to your current work tree.