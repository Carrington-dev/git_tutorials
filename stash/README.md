# Stash

Sometimes you have files you don't want to commit beacuase they are unifinished but you also want don't want to lose them to preserve these files you can stash them so that you can finish in later use.

## How to use git stash
Here's the sequence to follow when using git stash:

* Save changes to branch A.
* Run git stash.
* Check out branch B.
* Fix the bug in branch B.
* Commit and (optionally) push to remote.
* Check out branch A
* Run git stash pop to get your stashed changes back.
* Git stash stores the changes you made to the working directory locally (inside your project's .git directory; /.git/refs/stash, to be precise) and allows you to retrieve the changes when you need them. It's handy when you need to switch between contexts. It allows you to save changes that you might need at a later stage and is the fastest way to get your working directory clean while keeping changes intact.

__To stash files__
## To stash files

```bash
git stash 
```
You can continue woorking on other problem and then later come back to this file or files

`git stash -u` or `git stash --include-untracked` stash untracked files.
`git stash -a` or `git stash --all` stash untracked files and ignored files.

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
```bash
console/console-init/ui/.graphqlrc.yml        |   4 +-
console/console-init/ui/generated-frontend.ts | 742 +++++++++---------
console/console-init/ui/package.json          |   2 +-
```
To get a more detailed diff, pass the `--patch` or `-p` flag:

## Checking out to a new branch

You might come across a situation where the changes in a branch and your stash diverge, causing a conflict when you attempt to reapply the stash. A clean fix for this is to use the command `git stash branch <new_branch_name stash_id>`, which creates a new branch based on the commit the stash was created from and pops the stashed changes to it:

```git stash branch test_2 stash@{0}```

## Stashing without disturbing the stash reflog
In rare cases, you might need to create a stash while keeping the stash reference log (reflog) intact. These cases might arise when you need a script to stash as an implementation detail. This is achieved by the git stash create command; it creates a stash entry and returns its object name without pushing it to the stash reflog:

```git stash create "sample stash" 63a711cd3c7f8047662007490723e26ae9d4acf9```
Sometimes, you might decide to push the stash entry created via git stash create to the stash reflog:

```git stash store -m "sample stash testing.." "63a711cd3c7f8047662007490723e26ae9d4acf9"```

## List stash
```git stash list```
stash @{0}: sample stash testing..

## Git Stash Extras
Stash with message
* ```git stash save "My Messages"```

Find changes done in specific stash
* ```git stash show stash@{index}```

Apply specific stash
* ```git stash apply stash@{index}```

## Conclusion
I hope you found this article useful and learned something new. If I missed any useful options for using stash, please let me know in the comments.