# Stash

Sometimes you have files you don't want to commit beacuase they are unifinished but you also want don't want to lose them to preserve these files you can stash them so that you can finish in later use.

__To stash files__
## To stash files

```bash
git stash 
```
You can continue woorking on other problem and then later come back to this file or files

`__git stash -u__` or `__git stash --include-untracked__` stash untracked files.
`__git stash -a__` or `__git stash --all__` stash untracked files and ignored files.

see more 
https://opensource.com/article/21/4/git-stash

## Retrieving stashed changes

You can reapply stashed changes with the commands git stash apply and git stash pop. Both commands reapply the changes stashed in the latest stash (that is, stash@{0}). A stash reapplies the changes while pop removes the changes from the stash and reapplies them to the working copy. Popping is preferred if you don't need the stashed changes to be reapplied more than once.

You can choose which stash you want to pop or apply by passing the identifier as the last argument:

```bash
git stash pop stash@{1} 
```
or
```bash
git stash apply stash@{1}
```

## Cleaning up the stash

It is good practice to remove stashes that are no longer needed. You must do this manually with the following commands:

* `git stash clear` empties the stash list by removing all the stashes.
* `git stash drop <stash_id>` deletes a particular stash from the stash list.

## Checking stash diffs
The command git stash show <stash_id> allows you to view the diff of a stash:

```git stash show stash@{1}```
Output
`
console/console-init/ui/.graphqlrc.yml        |   4 +-
console/console-init/ui/generated-frontend.ts | 742 +++++++++---------
console/console-init/ui/package.json          |   2 +-
To get a more detailed diff, pass the --patch or -p flag:`

## Checking out to a new branch

You might come across a situation where the changes in a branch and your stash diverge, causing a conflict when you attempt to reapply the stash. A clean fix for this is to use the command `git stash branch <new_branch_name stash_id>`, which creates a new branch based on the commit the stash was created from and pops the stashed changes to it:

```git stash branch test_2 stash@{0}```