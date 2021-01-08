Git has the ability to tag specific points in a repository’s history as being important.
Typically, people use this functionality to mark release points (v1.0, v2.0 and so on).

Git supports two types of tags: lightweight and annotated.

A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific
commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed;
contain the tagger name, email, and date; have a tagging message; and can be signed and verified
with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you
can have all this information; but if you want a temporary tag or for some reason don’t want to
keep the other information, lightweight tags are available too.

To create an annotated tag, type for example `git tag -a v1.4 -m "my version 1.4"`

Sharing tags can be done with `git push origin <tagname>`.

Listing the existing tags in Git is straightforward. Just type `git tag`.

You can also search for tags that match a particular pattern. The Git source repo, for instance,
contains more than 500 tags. If you’re interested only in looking at the 1.8.5 series, you can run this: `git tag -l "v1.8.5*"`