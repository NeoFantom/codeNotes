# Undoing Changes

1. `git checkout`
   1. `git checkout <commit id>` Detach HEAD temporarily.
   2. `git checkout -b <commit id>` Checkout to a previous commit and create a new branch.
   3. `git checkout <branch>` Checkout to the latest commit of the branch.
   4. `git checkout master` An example. Checkout to the latest commit in master branch.
2. `git clean` Clean uncommitted changes.
3. `git revert` Do a new commit that reverts the last commit. *Best for public changes.*
4. `git reset --hard <commit id>` Roll back to the previous commit and withdraw the commits after it. *Best for local changes.*
5. `git commit --amend` Withdraw the last commit and commit again with the latest changes.

# Rewriting History

1. `git commit --amend` (*Best for local changes.*)
   1. `[-m "message"]` With message given in "".
   2. `[--no-edit]` Without editing message, update the s.
2. `git rebase`
3. `git rebase i`
4. `git reflog`