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
2. `git rebase <branch>` Make your feature branch look like as if they're developed upon the latest master branch.
   1. `git rebase i <branch>` Interactive.
3. `git reflog` Show the whole change history.

# Syncing

1. `git remote` Show remote names.
   1. `add <name> <url>` Add a new remote.
   2. `remove <name>`
   3. `rename <old> <new>`
2. `git fetch <remote> [<branch>]`
3. `git push <remote> <branch>` Push branch to remote.
   1. `[--force]` Use when re-pushing an amended commit.
4. `git pull <remote>` Pull into current branch.
   1. `--rebase` Instead of merge, do a rebase.
   2. `git config --global branch.autosetuprebase always`
   3. 

# Branching

1. `git branch` List branches.
   1. `[<branch_name>]` Create branch with specified name, no switching.
   2. `[-d <branch>]` Delete the branch, or do nothing if the branch has unmerged changes.
   3. `[-D <branch>]` Force delete the branch regardless of unmerged changes.
   4. `-r` Act (or list) remote branches.
   5. `-a` List all branches, both local and remote.
2. `gti checkout <branch>` Switch to branch.
3. yes
