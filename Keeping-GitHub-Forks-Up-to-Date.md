Lots of times at LambdaSchool and in Real Life, you'll make a fork of a repo. Then the owner of the original repo will make further commits to their repo and your fork will fall out of sync.

This is normal, and can be handled from the command line with a little bit of setup and a couple commands.

Unfortunately, as of now, [you can't do this from the GitHub web UI](https://github.com/isaacs/github/issues/121) and, given how old that feature request is, it might never happen.

## A Bit of Perspective

Before we begin, it's useful to know what repos are at play and how they interact.

There are three, and we're going to give them all names:

* `origin`: this is your fork on GitHub (of the original repo on GitHub, the `upstream`)
* `local`: this is your clone on your local computer (of your fork on GitHub, the `origin`)
* `upstream`: this is the original repo on GitHub that you forked

When we bring our `origin` into sync with the `upstream`, there are two possible approaches:

1. You get the `upstream` owner to issue you a pull request and you accept it in the GitHub UI. **This barely ever happens**, since they'd have to do it for everyone who forked the repo, and that might be hundreds of people.

2. You fetch the commits from `upstream` into your `local` repo, merge them, and then push the result to your `origin`. **This is almost always the way it happens**.

![Syncing the fork repo](https://github.com/LambdaSchool/BeejWiki/blob/master/wiki-images/repo-fork-sync.svg)

## What is `upstream`?

**This is important one-time setup! Once you set the `upstream`, you don't need to do it again for this repo!**

Upstream is what we call a _remote_ in git. It's a nice human-readable name for a repo URL. You could use the full URL every time you wanted to refer to a repo, but that's a pain, so we make these aliases.

`origin` is a remote name you might already have seen. It's "the URL this repo was cloned from". This gets set up for you automatically by git.

For example, if I have a local repo that's a clone of one of my forks, I can see the remotes for the repo with `git remote -v`:

```bash
$ git clone git@github.com:MyName/My-Forked-Repo.git
[...cloning output...] 

$ git remote -v
origin	git@github.com:MyName/My-Forked-Repo.git (fetch)
origin	git@github.com:MyName/My-Forked-Repo.git (push)
```

But you can have as many remotes as you want; they're just names for other repos. So let's add another remote that _refers to the original repo we forked from_, and let's call it `upstream`.

```bash
$ git remote add upstream https://github.com/LambdaSchool/Original-Repo.git

$ git remote -v
origin	git@github.com:MyName/My-Forked-Repo.git (fetch)
origin	git@github.com:MyName/My-Forked-Repo.git (push)
upstream     https://github.com/LambdaSchool/Original-Repo.git (fetch)
upstream     https://github.com/LambdaSchool/Original-Repo.git (push)
```

Now we have two remotes listed.

Note that we used the HTTPS URL for the original repo for `upstream`. This is because we presumably don't have SSH access to that repo, but that's OK--we only need to read from it, not write to it.

## Syncing Your Fork

As shown in the diagram up above, we're going to grab commits from `upstream`, merge them into our `local`, and then push them to our `origin`. After that, all repos should be in sync.

### `git fetch`

`git fetch` is like `git pull`, except it doesn't merge. It goes and grabs all the updates from the named remote and puts them in your local repo, but doesn't update anything in your working directory. The commits are just sitting there in git's database.

> Fun fact: `git pull` is shorthand for `git fetch` followed by `git merge`.

**The following assumes you're merging the `origin`'s `master` branch with your `master` branch. If you're merging other branches, you'll have to adjust the following instructions to suit.**

First, make sure you've fully committed your stuff:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```

If it says you have changes that are staged (or not staged), make a commit before proceeding. (Or learn how to use `[git stash](https://git-scm.com/book/en/v1/Git-Tools-Stashing)`.)

Second, fetch the new commits from the original repo, `upstream`:

```bash
$ get fetch upstream
[...fetch output...]
```

## References

* https://help.github.com/articles/syncing-a-fork/