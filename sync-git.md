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

`git fetch` again takes our
current branch, and checks to see if there is a tracking branch. If so, it looks
for changes in the remote branch, and pulls them into the tracking branch. It
does not change your local branch. To do that, you'll need to do
`git merge origin/master` (for the "master" branch) to merge those changes into
your branch - probably also called "master".`git pull` simply does a `git fetch`
followed immediately by `git merge`.

## Send information to the server

`git push` takes our
current branch, and checks to see whether or not there is a tracking branch for
a remote repository connected to it. If so, our changes are taken from our
branch and pushed to the remote branch. This is how code is shared with a remote
repository, you can think of it as "make the remote branch resemble my local
branch". This will fail if the remote branch has diverged from your local
branch: if not all the commits in the remote branch are in your local branch.
When this happens, your local branch needs to be synchronized with the remote
branch with git pull or git fetch and git merge.
