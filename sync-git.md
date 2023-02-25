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

The push command confirms your local branch is tracked on the change control
server, looks for commits on your local branch that do not exist on the remote
branch, then pushes the missing changes to the server.

Pushing changes to the server is how you share your code with others. You can
think of the push command as "make the remote branch look like my local branch".

> **Warning**
> Your push will fail if the remote branch has changes that you have not applied
> to your local branch. To fix the error, sync your local branch with `git pull`
> or `git fetch` and `git merge` then push your changes again.
