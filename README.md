# <h1 id="summary">Summary</h1>

* [VSCode Shortcuts](#shortcuts)
* [Commands](#commands)
* [Branch](#branch)
* [Unstage](#unstage)
* [Change Commit Msg](#change-commit-msg)
* [Track/Untrack Files](#track-untrack-files)
* [Revert Commited Files](#revert-commited-files)
* [GitHub Gist](#github-gist)
* [VSCode Default Editor](#vscode-default-editor)

# <h1 id="shortcuts">VSCode Shortcuts</h1>
[Go Back To Summary](#summary)

### Mac
* `CMD+Shift+V`: open README Preview in VSCode

### Windows
* `Ctrl+Alt+V`: open READMEA Preview in VSCode

# <h1 id="commands">COMMANDS</h1>
[Go Back To Summary](#summary)

#### [Commands] List of Log (commits)

* List all your commits

```
      git log --oneline
```
#### [Commands] View Commit Message

```
   git log -n <number of past commit(s)>--pretty=format:%s $hash
```

There is two ways to view your past commits

1) If you want to view the last message, you can just add the `<number of past commit(s)>`, in this case `1` whitout `$hash`

```
      git log -n <number of past commit(s)>--pretty=format:%s
```

2) IF you want to view a specific commit, you use `<number of past commit(s)>` as `1` and add `$hash`

```
      git log -n 1--pretty=format:%s a63ef55
```

#### [Commands] Stash Changes (branch)

* To stash all the changes whitout the need to commit/push 

```
      git stash
```

* Get back the changes from stash (branch)

```
      git stash apply   
```

#### [Commands] [Set New Remote Origin](https://help.github.com/en/articles/changing-a-remotes-url)

```
   git remote set-url origin <url>
```

# <h1 id="branch">BRANCH</h1>
[Go Back To Summary](#summary)

**[Branch] 1. Create a Branch**

```
   git branch <branch name>
```

**[Branch] 2. List All my Local Branches**

```
   git branch
```

**[Branch] 3. To Work on a Branch**

```
   git checkout <branch name>
```

**[Branch] 4. After You've Made the Changes on the Branch**

```
   git add -A
   git commit -m ""
```

**[Branch] 5. After Commit, Push Branch to Remote (Origin)**

```
   git push -u origin <branch name>
   git branch -a             (Check all branch local and remote)
```

**[Branch] 6. Merge a Branch to Local HEAD (Master) and Push to Master to Remote (Origin)**

```
   git checkout master       (to change to master branch)
   git pull origin master    (just to be sure that local master is up to date)
   git branch --merged       (to check if the branch was merged, right now is just "master")
   git merge <branch name>   (to merge the changes to local master)
   git push origin master    (to push this changes to remote master)
   git branch --merged       (to check if the branch was merged)
```

**[Branch] 7. Delete Branch After You Finish Using this Feature**

```
   git branch -d <branch name>              (to delete local branch)
   git branch -a
   git push origin --delete <branch name>   (to delete remote branch)
```

# <h1 id="unstage">UNSTAGE</h1>
[Go Back To Summary](#summary)

#### [Unstage] Remove From Stage - KEEP the Modifications

* Remove from stage (after `git add -A` or `git add <file>`)
* To remove files from stage use `reset HEAD` where `HEAD` is the last commit of the current branch. This will unstage the file but maintain the modifications.

```
      git reset HEAD <filename>
```

#### [Unstage] Remove From Stage - DISCARD the Modifications

* Remove from stage (after `git add -A` or `git add <filename>`)

```
      git reset            (remove all files from staged)
      git reset <filename> (remove specific file from staged)
```

#### [[Unstage] Git Reset `[<mode>] [<commit>]`](https://gist.github.com/CrookedNumber/8964442)


This form resets the current branch head to `<commit>` and possibly updates the index (resetting it to the tree of `<commit>`) and the working tree depending on `<mode>`. If `<mode>` is omitted, defaults to `--mixed`. The `<mode>` must be one of the following:

**`--soft`**

* Does not touch the index file or the working tree at all (but resets the head to `<commit>`, just like all modes do). This leaves all your changed files "Changes to be committed", as git status would put it.

**`--mixed`**

* Resets the index but not the working tree (i.e., the changed files are preserved but not marked for commit) and reports what has not been updated. This is the default action.
* If `-N` is specified, removed paths are marked as intent-to-add (see git-add[1]).

**`--hard`**
* Resets the index and working tree. Any changes to tracked files in the working tree since `<commit>` are discarded.

```
      git reset --hard HEAD~1 (reset last commit)
```

**`--merge`**

* Resets the index and updates the files in the working tree that are different between `<commit>` and HEAD, but keeps those which are different between the index and working tree (i.e. which have changes which have not been added). If a file that is different between `<commit>` and the index has unstaged changes, reset is aborted.
* In other words, `--merge` does something like a git read-tree `-u -m <commit>`, but carries forward unmerged index entries.

**`--keep`**

* Resets index entries and updates files in the working tree that are different between `<commit>` and HEAD. If a file that is different between `<commit>` and HEAD has local changes, reset is aborted.

# <h1 id="change-commit-msg">CHANGE COMMIT MESSAGE</h1>
[Go Back To Summary](#summary)

At some point you’ll find yourself in a situation where you need edit a commit message. That commit might already be pushed or not, be the most recent or burried below 10 other commits

#### [Change Commit Message] Not Pushed + Most Recent Commit:

* This will open your $EDITOR and let you change the message. Continue with your usual git push origin master.

```
      git commit --amend
```

#### [Change Commit Message] Already Pushed + Most Recent Commit:

* We edit the message like just above. But need to `--force` the push to update the remote history.

* ⚠️ But! Force pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

```
      git commit --amend
      git push origin master --force
```

#### [Change Commit Message] Not Pushed + Old Commit:

* Rebase opened your history and let you pick what to change. With edit you tell you want to change the message. Git moves you to a new branch to let you `--amend` the message. git rebase `--continue` puts you back in your previous branch with the message changed.

```
      git rebase -i HEAD~X
      # X is the number of commits to go back
      # Move to the line of your commit, change pick into edit,
      # then change your commit message:
      git commit --amend
      # Finish the rebase with:
      git rebase --continue
```

#### [Change Commit Message] Already Pushed + Old Commit:

* Edit your message with the same 3 steps process as above (`rebase -i, commit --amend, rebase --continue`). Then force push the commit:

```
      git push origin master --force
```

⚠️ But! Remember re-pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

# <h1 id="track-untrack-files">TRACK/UNTRACK FILES</h1>
[Go Back To Summary](#summary)

* There are often times when you want to modify a file but not commit the changes, for example changing the database configuration to run on your local machine.

* Adding the file to .gitignore doesn’t work, because the file is already tracked. Luckily, Git will allow you to manually “ignore” changes to a file or directory.

#### [Track/Untrack] Untrack File Permanently

```
   git update-index --assume-unchanged <filename>
```

#### [Track/Untrack] Track Brack Ignored Files

```
   git update-index --no-assume-unchanged <filename>
```

#### [Track/Untrack] List of Ignored Files

* If you  forgot what file did you `--assume-unchanged`, you can call the list using the following command:

* Windows command

```bash
      git ls-files -v | findstr /B h
```

* Mac/Unix Command

```bash
      git ls-files -v | grep '^h'
```


# <h1 id="discard-not-commited-changes">DISCARD NOT COMMITED CHANGES</h1>
[Go Back To Summary](#summary)

#### [Discard] Discard Local Changes

* To revert the file back to the state it was in before the changes. This will put your local git (HEAD) on your last commit and will erase all your modifications.

```
      git checkout -- <filename>
```

# <h1 id="revert-commited-files">REVERT COMMITED FILES</h1>
[Go Back To Summary](#summary)

[Original External Link](https://gist.github.com/gunjanpatel/18f9e4d1eb609597c50c2118e416e6a6)

Revert local git (HEAD) to '~X'commit(s), This will revert your local git (HEAD) to this "last" commit and it'll DISCARD all your modifications. 
X is the number of step back that you want to do. 

#### [Revert] Revert Local Git and DISCARD All the Changes

* Revert local git (HEAD) to '~X'commit(s), This will revert your local git (HEAD) to this "last" commit and it'll DISCARD all your modifications. 
X is the number of step back that you want to do. 

```
      git reset --hard HEAD~1 (revert commit, but discard the changes)
```

#### [Revert] Revert Local Git and KEEP All the Changes

* Revert local git (HEAD) to '~X'commit(s), This will revert your local git (HEAD) to this "last" commit and it'll KEEP all your modifications.

```
      git reset --soft HEAD~1             (revert commit, but keept the changes)
      git reset HEAD <filename>           (Unstage the file to keep editing)   
```

#### [Revert] Revert the Full Commit

* Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.

```
      git revert {commit_id}
```

#### [Revert] Delete the Last Commit

* Deleting the last commit is the easiest case. Let's say we have a remote origin with branch master that currently points to commit dd61ab32. We want to remove the top commit. Translated to git terminology, we want to force the master branch of the origin remote repository to the parent of dd61ab32:

```
      git push origin +dd61ab32^:master
```

* Where git interprets x^ as the parent of x and + as a forced non-fastforward push. If you have the master branch checked out locally, you can also do it in two simpler steps: First reset the branch to the parent of the current commit, then force-push it to the remote.

```
      git reset HEAD^ --hard
      git push origin -f
```

# <h1 id="delete-remove">DELETE/REMOVE</h1>
[Go Back To Summary](#summary)

#### [Delete/Remove] Remove a File from Local and Remote Repo

* To remove a file from disk and repo use ‘`git rm`’ and to rm a dir use the ‘`-r`’ flag:

```
      git rm '*.txt'
      git rm -r <dirname>
```

#### [Delete/Remove] Remove File (Similiar to .gitignore)

* If we want to remove a file from the repository but keep it on disk, say we forgot to add it to our **.gitignore** file then use `--cache`:

```
      git rm --cache <filename>
```

# <h1 id="github-gist">GitHub GIST</h1>
[Go Back To Summary](#summary)

https://gist.github.com/Roger-Takeshita

**Gist description**: A brief description about your gist

**File**: Create any file just to GitHub let you create your gist

# <h1 id="vscode-default-editor">Set VSCode as Default Editor</h1>
[Go Back To Summary](#summary)

### [Set VSCode as Default Editor] MAC
* If you manually install Visual Studio Code, rather than using Homebrew, you will need to add the code executable to your PATH.

```
      brew cask install visual-studio-code
```

* **In terminal**
   1) Type: `open ~/.bash_profile`
   2) Delete everything and insert: `export EDITOR="code -w"`

* **In visual studio code**

   1) Press: `CMD + SHIFT + P`
   2) Insert: install code and select from autocomplete menu shell command: `Install 'code'` in command PATH