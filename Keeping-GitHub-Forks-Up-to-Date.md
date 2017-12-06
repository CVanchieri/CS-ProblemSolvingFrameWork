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

## References

* https://help.github.com/articles/syncing-a-fork/