# git_cheats
Solutions to common git scenarios

## git clone with non-default ssh-key

```console
git -c core.sshCommand="ssh -i <path-to-private-key>" clone <path-to-git-repo>
```

E.g.:
```console
git -c core.sshCommand="ssh -i C:/Users/ewald/.ssh/id_rsa_nexte" clone git@github.com:EwaldRode/cheats.git
```

## reconfigure git to use non-default ssh key


```console
git config core.sshCommand 'ssh -i <path-to-private-key>'
```

E.g.:
```console
git config core.sshCommand 'ssh -i C:/Users/ewald/.ssh/id_rsa_nexte'
```



## rebasing branch onto master
When not to use: If other people are also working on your branch. 
### short
Scenario: You are on your local branch and you are the *ONLY* person working on it.
Solution: If you know what you are doing, use this for rebase. 
```bash
git fetch && git rebase origin/master
```

### long
Scenario: You have a local branch and already commited changes.
Solution:
Step 1: Pull all commits made by other developers working on your branch and rebases your changes on top of it.
```bash
git checkout LocalBranch
git pull --rebase
```

Step 2: Resolve conflicts.

Step 3: Pull all commits from remote master (and rebases local master on remote master(--rebase is only necessary if you committed onto local master)).
```bash
git checkout master
git pull --rebase
```

Step 4: Resolve conflicts.

Step 5: Rebase LocalBranch onto master.
```bash
git checkout LocalBranch
git rebase master
```

Step 6: Resolve conflicts. 

Step 7: Pushing changes to remote LocalBranch. --force-with-lease will only overwrite the branch in case there were no other commits published for LocalBranch from other developers while you were rebasing. Do not use --force as this will overwrite changes made by oter developers. In case other developers made changes to LocalBranch. Start again from Step 1.
```bash
git push --force-with-lease 
```

## resolve rebase/merge conflicts
Add resolved conflicts.
```bash
git add path/to/filename
```
### rebase
Continue rebase with:
```bash
git rebase --continue
```
Abort rebase with:
```bash
git rebase --abort
```

### merge 
Continue merge with:
```bash
git merge --continue
```
Abort merge with:
```bash
git merge --abort
```

## merge branch into master
```bash
git checkout master
git merge LocalBranch
```
When and Why? Merge your branch into master if done with changes by you and other co-developers. Which makes YourBranch up-to-date with master when you wanted to work on same branch later.

## pull changes from master into your current local branch
```bash
git pull origin master
```

## delete a git commit while keeping the changes made to the code
```bash
git reset HEAD^
```
git reset without a --hard or --soft moves your HEAD to point to the specified commit, without changing any files. HEAD^ refers to the (first) parent commit of your current commit, which in your case is the commit before the temporary one.

## amend a commit
```bash
git commit --amend [-m … etc]
```
This will edit the most recent commit.

Note: This can cause problems if you've already pushed the commit to a place where someone else may have pulled it from.

## overwrite changes made to local branch
Setting your branch to exactly match the remote branch:
```bash
git fetch origin
git reset --hard origin/master
```

## Rename a local branch
If you are on the branch you want to rename:
```bash
git branch -m new-name
```

## Create a patch for the last commit 
```bash
git format-patch -1 HEAD
```
