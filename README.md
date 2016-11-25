# Useful commands for Opensource Git workflow 

### Forked Rebases

```sh

# Add the target remote repo as "upstream"

git remote add upstream https://github.com/user/<main-repo>.git

# Updating locally - fetch all branches

git fetch upstream

# Then checkout to master

git checkout master

# rewrite master branch so all your commits are on top of current commits in upstream/master

git rebase upstream/master
```

### Commit Squashes 

Why would you want to squash commits ? 

**Polluted examples:**

```
commit 0e5df0t  - fix Tooltip label
commit 2e7ac0f  - fix things
commit 1e8gc1e  - fix moar things <insert emoji>
```

your commit logs on your master will start get polluted with commits like this. Which is difficult to identify what changes
are occuring at different stages.  

**Polluted examples(squashed):**
```
commit 0e5df0t - Issue/#3618 - Fixed Tooltip label when min is undefined
```

Squashing commits into one clear and concise commit lets other team members know the following:

- what are you changing/fixing ?  
- What is it fixing and if it references a current issue ?  

So, it gives your team member a clear *at-first-glance* look at what happened there. If they wish
to explore further, they can checkout to the branch.


#### How is it Done

```sh
git rebase -i HEAD~<number of lines> # git rebase -i HEAD~3 can be used for the above example
```

Then you enter Interactive mode:   

```
edit 0e5df0t  - Issue/#3618 - Fixed Tooltip label when min is undefined
squash 2e7ac0f  - fix things
squash 1e8gc1e  - fix moar things <insert emoji>
```

you can Make an edit on most recent commit and change the commit message to more clear and concise one to be used
when it gets merged into upstream/master.
