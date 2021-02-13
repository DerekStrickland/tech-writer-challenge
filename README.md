## What is the difference between push, pull, and fetch?

- `git fetch` - downloads changes from your _remote_ branch, and adds them to your
  _tracking_ branch
- `git pull` - downloads changes from your _remote_ branch, adds them to your
  _tracking_ branch, and then merges them into your _tracking_ branch
- `git push` - uploads changes from your _local_ or _tracking_ branch to your
  _remote_ branch

Often `git push` and `git pull` are described as equivalent. This isn't entirely
correct, since `git pull` does two things.

The `git fetch` command takes your current branch, and checks to see if there is
a _tracking_ branch. If so, it looks for changes in the _remote_ branch. If there
are changes, they are downloaded, but not merged into your _tracking_ branch. You
must manually issue the `git merge origin/main` command (for the "main" branch)
to merge those changes into your branch - probably also called "main".

The `git pull` command performs `git fetch` followed immediately by `git merge`.
This is often what you want to do, but you may prefer to use `git fetch` followed
by `git merge` to make sure you understand the changes before you merge.

The `git push` command takes your current branch, and checks to see whether is a
_tracking_ branch for a _remote_ branch. If so, your changes are pushed from your
_tracking_ branch to your _remote_ branch. This is how code is shared with a
_remote_ branch. You can think of it as "make the _remote_ branch resemble my
_tracking_ branch".

The `git push` command will fail if your _remote_ branch has diverged from your
_tracking_ branch: if not all the commits in the _remote_ branch are in your
_tracking_ branch. When this happens, your _tracking_ branch needs to be synchronized
with the _remote_ branch using either `git pull`, or using `git fetch` with
`git merge`.

