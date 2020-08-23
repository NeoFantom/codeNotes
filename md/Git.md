# Git Handbook <!-- omit in toc -->

## Table of Contents <!-- omit in toc -->

- [Setting up](#setting-up)
- [Inspecting a repository](#inspecting-a-repository)
- [Saving & undoing changes](#saving--undoing-changes)
- [Rewriting history](#rewriting-history)
- [Syncing](#syncing)
- [Branching](#branching)
- [Merging](#merging)

## Setting up

1. `git init` Initialize *current* directory.
   - `git init <directory>` Initialize *given* directory.
1. `git clone <url>` Clone a repo from *url* to `./<repo-name>`. Effectively equivalent to:
   1. Creates a new empty repository.  
      `mkdir <repo-name>`  
      `cd <repo-name>`  
      `git init`
   1. Creates a remote called "origin" and sets it to the given url.  
      `git remote add origin <url>`
   1. Fetches all commits and remote branches from the remote called "origin".  
      `git fetch --all`
   1. Let "master" track the remote branch "origin/master".  
      `git checkout --track origin/master`

## Inspecting a repository

1. `git status`
1. `git log` See commit history.
   1. `[--oneline]` Print each commit in one line.
1. `git blame <file>` Print the file with author attached to each line.
1. `git diff [<file>]` Compare changes since last commit.
   - `git diff <commit1> <commit2>` Compare two commits.
   - `git diff --cached` Compare changes between *staging area* and *HEAD*.

## Saving & undoing changes

1. `git add` Stage file with changes.
   - `git add .` Most commonly used. Stage *current directory*'s changes.
   - `git add [<file>|<directory]` Stage specified *file* or *directory*.
   - `git add (-A | --all)` Stage *all* changes of both tracked and untracked files.
1. `git rm` Reverse of *add*.
   - `git rm <file1> <file2> ...` Remove multiple files.
   - `git rm <glob1> <glob2> ...` Remove multiple items by globs.
1. `git commit [-m "message"]`
   - `git commit --amend` Withdraw the last commit and commit again with the latest changes.
1. `git stash` Stash uncommitted changes of *tracked files* temporarily away.
   - `git stash apply` Apply stashed changes.
   - `git stash pop` Apply, then remove.
   - `git stash (-u | --include-untracked)` Stash *untracked* files.
   - `git stash (-a | --all)` Stash all, including *untracked, ignored*.
1. `git revert` Do a new commit that reverts the last commit. *Requires working tree to be clean.* *Best for public changes.*
   - `git revert HEAD` Revert last commit.
1. `git reset [options=--mixed] <commit id>` Roll back to the previous commit and withdraw the commits after it. *Best for local changes.*
   - `--soft` Reset only HEAD.
   - `--mixed` Reset HEAD and index, move staged changes into working tree.
   - `--hard` Reset HEAD, index and working tree. All uncommitted changes are lost.
1. `git clean` Clean untracked files. *Must be used with parameter*.
   - `git clean -i` Interactive.
   - `git clean -f` Forced clean.

## Rewriting history

1. `git commit --amend` *Best for local changes.*
   - `[-m "message"]` With message given in "".
   - `[--no-edit]` Without editing message, update the s.
1. `git rebase <branch>` Make your feature branch look like as if they're developed upon the latest master branch.
   - `git rebase -i <branch>` Interactive.
1. `git reflog` Show the whole change history, including orphaned commits.

## Syncing

1. `git remote` Show remote names.
   - `add <name> <url>` Add a new remote.
   - `remove <remote>`
   - `rename <old> <new>`
1. `git fetch <remote> [<branch>]`
1. `git push <remote> <branch>` Push branch to remote if all merges are fast-forward.
   - `[--force]` *Use when re-pushing an amended commit.*
1. `git pull <remote>` Pull into current branch. Effectively equivalent to `git fetch` followed by `git merge`.
   - `--rebase` Instead of merge, do a rebase.
   - `git config --global branch.autosetuprebase always`

## Branching

1. `git branch` List branches.
   - `[<branch_name>]` Create branch with specified name, no switching.
   - `[-d <branch>]` Delete the branch, or do nothing if the branch has unmerged changes.
   - `[-D <branch>]` Force delete the branch regardless of unmerged changes.
   - `-r` Act (or list) remote branches.
   - `-a` List all branches, both local and remote.
1. `git checkout`
   - `git checkout <commit id>` Detach HEAD temporarily.
   - `git checkout -b <commit id>` Checkout to a previous commit and create a *new* branch.
   - `git checkout <branch>` Checkout to the latest commit of the branch.
   - `git checkout master` An example. Checkout to the latest commit in master branch.

## Merging

1. `git merge <branch>` Merge branch into current branch.
   - If it is a fast-forward merge, then simply merge it.
   - Else, if the two branches made changes somewhere in the *same place of the same file,* then conflicts are printed in the conflicted file, and the user has to manually resolve it.