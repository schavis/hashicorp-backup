# What is the difference between push, pull, and fetch?

To work with Git, you must keep your local (tracking) branches in sync
with the remote branches on your repository server. You use the push, pull, and
fetch commands to control the communication between your local branch and the
remote branch: 

- `git push` - send your local changes to the remote branch
- `git fetch` - get changes from the remote branch
- `git merge` - apply changes from the remote branch to your local branch
- `git pull` - get changes from the remote branch **and** apply the changes to
  your local branch

> **Note**
> A local branch connected to a remote branch is a **tracking branch**. The
> push, fetch, merge, and pull commands only work with tracking branches. To
> create a tracked local branch, use `git branch --track` or `git checkout -b`. 

## Get information from the server

In most cases, `git pull` is easist way to get changes from the server. However,
if you prefer to review and understand changes before applying them to your
local branch, use `git fetch` and `git merge`.

### Fetch and merge changes

The fetch command confirms you are using a tracked branch, looks for changes in
the remote branch that do not exist on your local branch, and downloads the
related commit details **without** modifying your files.

To apply the changes locally, you must pair `git fetch` with `git merge`:

1. Run `git fetch origin BRANCH_NAME` to look for unapplied changes in the
   remote branch.
1. Review the list of commits to understand what will change.
1. Run `git merge origin BRANCH_NAME` to apply the changes.

### Pull changes

The pull command also confirms you are using a tracked branch and looks for
changes in the remote branch. The difference between `git pull` and `git fetch`
is that `git pull` downloads and applies the related commits in one step.

To apply remote changes with a single command, run `git pull origin BRANCH_NAME`.

## Send information to the server

`git push` takes our
current branch, and checks to see whether or not there is a tracking branch for
a remote repository connected to it. If so, our changes are taken from our
branch and pushed to the remote branch. This is how code is shared with a remote
repository, you can think of it as "make the remote branch resemble my local
branch".

Your push will fail if the remote branch has changes that you have not applied
to your local branch. When a push fails, your local branch needs to be synchronized with the remote
branch with git pull or git fetch and git merge.
