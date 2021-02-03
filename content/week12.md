*Git hint of the week:*

Merge request references

Dealing with a Merge Request (MR) implies pulling code from the server, running and testing it.
When there are many MRs this leads to repeated `git switch <to-be-merged-branch>` which implies that you have to know the to-be-merged-branch name.

Each repository has a MR counter so wouldn't it be great to just be able to write `git switch mr/<mr-number>`?

By using `git ls-remote origin` we can see all the references from the remote named `origin`. A reference (or "ref") is anything pointing to a commit, for example, branches (heads), tags, and remote branches. Command `git ls-remote origin` would have an output similar to:
```
10d539600d86723087810ec636870a504f4fee4d HEAD
10d539600d86723087810ec636870a504f4fee4d refs/heads/master
6a83107c62950be9453aac297bb0193fd743cd6e refs/merge-requests/1/head
3c8d735ee16296c242be7a9742ebfbc2665adec1 refs/merge-requests/2/head
a5a7751a33b7e86c5e9bb07b26001bb17d775d1a refs/merge-requests/4/head
```

Refs under `refs/heads` are usual branches. Refs under `refs/merge-requests` are basically branches too, but since they’re not under `refs/heads/` you don’t normally get them when you clone or fetch from the server — the process of fetching ignores them. Refs from `refs/merge-requests` point to the last commit from a MR so by fetching them we'll be able to address the MR changes locally.

We can manually fetch a MR ref using `git fetch origin refs/merge-requests/4/head` but there's a way to fetch *all* the MR refs from the server.

Open up `.git/config` in your favorite editor and look for `origin` remote. It should look like this:
```
[remote "origin"]
	url = https://<hostname>.com/<username>/<project-name>.git
	fetch = +refs/heads/*:refs/remotes/origin/*
```

That line that begins with fetch = is a "refspec." It's a way of mapping names on the remote with names in your local `.git` directory. This particular one tells Git, "the things on the remote that are under `refs/heads` should go in my local repository under refs/remotes/origin." You can modify this section to add another refspec:

```
[remote "origin"]
	url = https://<hostname>.com/<username>/<project-name>.git
	fetch = +refs/heads/*:refs/remotes/origin/*
	fetch = +refs/merge-requests/*/head:refs/remotes/origin/mr/*
```

That last line tells Git, "All the refs that look like refs/merge-requests/123/head should be stored locally like
refs/remotes/origin/mr/123."

Save, restart the git bash and `git fetch`. Now you can checkout MRs with `git switch mr/<mr-number>`.

