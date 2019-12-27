<h1 id="summary">Summary</h1>

* [VSCode Shortcuts](#shortcuts)
  * [Preview Markdown Mac](#shortcut-mac)
  * [Preview Markdown Windows](#shortcut-win)
* [Set VSCode as Default Editor](#vscode-default-editor)
  * [Default Editor - MAC](#defaul-editor-mac)
* [Commands](#commands)
  * [Log Commits](#git-log)
  * [Log Commits Message Only](#git-log-msg)
  * [Set New Remote Origin](#git-set-origin)
  * [Set Upstream](#git-upstream)
  * [Check Remote/Upstream URL](#git-check-remote)
* [Stash](#git-stash)
  * [Stash Uncommitted Changes](#git-stash-changes)
  * [Stash Apply Changes](#git-stash-apply)
  * [Stash Show Files](#git-stash-show)
  * [Stash Drop Changes](#git-stash-drop)
* [Branch](#branch)
* [Dicard Changes - Not Committed](#discard-not-committed-changes)
* [Unstage](#unstage)
  * [Remove All From Stage - KEEP the Modifications](#git-reset-head-file)
  * [Rmove a Specific File From Stage - KEEP the Modifications](#git-reset-file)
  * [Remove All From Stage - DISCARD the Modifications](#git-reset-head)
  * [Reset HEAD to Last Commit - DISCARD the Modificaions](#git-reset-hard-2)
  * [Reset [mode] [commit]](#git-reset-modes)
* [Change Commit Msg](#change-commit-msg)
  * [Change Commit Message - Not Pushed](#git-commit-msg-not-pushed)
  * [Change Commit Message - Already Pushed](#git-commit-msg-already-pushed)
  * [Change Commit Message - Not Pushed + Old Commit](#git-commit-msg-already-not-pushed-old)
  * [Change Commit Message - Already Pushed + Old Commit](#git-commit-msg-pushed-old)
* [Track/Untrack Files](#track-untrack-files)
  * [Untrack Pushed File (Like .gitignore)](#untrack-pushed-files)
  * [Track Back Ingnored Files](#track-back-pushed-files)
  * [List Ignored Files](#list-ignored-files)
* [Fetch Modifications From Branch/Remote Apply to Local](#fetch-modifications)
* [Revert Full Commit](#revert-full-commit)
* [Delete Pushed Files From Repo](#delete-pushed-files)
* [Change File Path From Remote](#change-file-path)
* [GitHub Gist](#github-gist)

<h1 id="shortcuts">VSCODE SHORTCUTS</h1>

<h3 id="shortcut-mac">Preview Markdown Mac</h3>

[Go Back To Summary](#summary)

* `CMD+Shift+V`: open README Preview in VSCode

<h3 id="shortcut-win">Preview Markdown Windows</h3>

[Go Back To Summary](#summary)

* `Ctrl+Alt+V`: open README Preview in VSCode

<h1 id="vscode-default-editor">SET VSCODE AS DEFAULT EDITOR</h1>

<h4 id="defaul-editor-mac">Default Editor - MAC</h4>

[Go Back To Summary](#summary)

* If you manually install Visual Studio Code, rather than using Homebrew, you will need to add the code executable to your PATH.

   ```bash
      brew cask install visual-studio-code
   ```

* **In terminal**

   1. Type: `open ~/.bash_profile`
   2. Delete everything and insert: `export EDITOR="code -w"`

* **In visual studio code**

   1. Press: `CMD + SHIFT + P`
   2. Insert: install code and select from autocomplete menu shell command: `Install 'code'` in command PATH

<h1 id="commands">COMMANDS</h1>

<h4 id="git-log">Log Commits</h4>

[Go Back To Summary](#summary)

* List all commits (enteire log)
 
   ```bash
      git log
   ```

* List all commits (**simple log**)
 
   ```bash
      git log --oneline
   ```

<h4 id="git-log-msg">Log Commit Message</h4>

[Go Back To Summary](#summary)

```bash
   git log -n --pretty=format:%s $hash
```

* **Option 1)** If you want to view the last message, you can just add the `-n` = **number of past commit(s)**, whitout `$hash`. Example:

   ```bash
      git log -1 --pretty=format:%s
   ```

* **Option 2)** IF you want to view a specific commit, you use `-n` = `1` and `$hash` = `hash key`

   ```bash
      git log -n 1--pretty=format:%s a63ef55
   ```

   * `a63ef55` is my hash key

<h4 id="git-set-origin"><a href="https://help.github.com/en/articles/changing-a-remotes-url">Set New Remote Origin</a></h4>

[Go Back To Summary](#summary)

* If you need to change the remote url

   ```bash
      git remote set-url origin <url>
   ```

<h4 id="git-upstream">Set Remove Upstream</h4>

[Go Back To Summary](#summary)

   ```bash
      git remote add upstream <url>
   ```

<h4 id="git-check-remote">Check Remote/Upstream URL</h4> 

[Go Back To Summary](#summary)

   ```bash
      git remote -v
   ```
<h1 id="git-stash">STASH</h1>

<h4 id="git-stash-changes">Stash Uncommitted Changes</h4>

[Go Back To Summary](#summary)

* To stash all the changes whitout the need to commit/push 

   ```bash
      git stash
   ```

<h4 id="git-stash-apply">Stash Apply Changes</h4>

[Go Back To Summary](#summary)

* To apply back the changes

   ```bash
      git stash apply   
   ```
<h4 id="git-stash-show">Stash Show Files</h4>

[Go Back To Summary](#summary)

* Show all the files that you have stashed
  
   ```bash
      git stash show
   ```

<h4 id="git-stash-drop">Stash Drop Changes</h4>

[Go Back To Summary](#summary)

* `git stash drop` will discard all the stashed files

   ```bash
      git stash drop
   ```

<h1 id="branch">BRANCH</h1>

[Go Back To Summary](#summary)

* **1. Create a Branch**

   ```bash
      git branch <branch name>
   ```

* **2. List Branches**

   2.1 List all my local branches

   ```bash
      git branch
   ```

   2.2 Lista all my branches (local/remote)

   ```bash
      git branch -a
   ```

* **3. To Work on a Branch**

   ```bash
      git checkout <branch name>
   ```
* **1. [Alternative] Create a Branch and Checkout to the New Branch**

   ```bash
      git checkout -b <branch name>
   ```

* **4. After You've Made the Changes on the Branch**

   ```bash
      git add -A
      git commit -m "message"
   ```

* **5. After Commit, Push Branch to Remote (Origin/Branch)**

   ```bash
      git push origin <branch name>
   ```

* **6. Merge a Branch to Local HEAD (Master) and Push to Master to Remote (Origin)**

   ```bash
      git checkout master       # to change to master branch
      git pull origin master    # just to be sure that local master is up to date
      git branch --merged       # to check if the branch was merged, right now is just "master"
      git merge <branch name>   # to merge the changes to local master
      git branch --merged       # to check if the branch was merged
      git push origin master    # to push this changes to remote master
   ```

* **7. Delete Branch After You Finish Using this Feature**

   ```bash
      git branch -d <branch name>              # to delete local branch
      git push origin --delete <branch name>   # to delete remote branch
   ```

<h1 id="discard-not-committed-changes">DISCARD CHANGES - NOT COMMITTED</h1>

[Go Back To Summary](#summary)

* To revert the file back to the state it was in before the changes. This will put your local git (HEAD) on your last commit and will erase all your modifications.

   ```bash
      git checkout -- <filename>
   ```

<h1 id="unstage">UNSTAGE</h1>

[Go Back To Summary](#summary)

* Remove from stage (after `git add -A` , `git add <file>` or `git add .`) - **NOT COMMITTED FILES**
  
<h4 id="git-reset-head-file">Remove All From Stage - <strong>KEEP</strong> the Modifications</h4>

[Go Back To Summary](#summary)

* To remove files from stage use `reset HEAD`. This will unstage the file(s) and **KEEP** all the modifications.

   ```bash
      git reset

      #or

      git reset HEAD          # unstage all files
   ```

<h4 id="git-reset-file">Remove a Specific File From Stage - <strong>KEEP</strong> the Modifications</h4>

[Go Back To Summary](#summary)

* Remove from stage (after `git add -A` or `git add <filename>`). This will unstage the file and **KEEP** all the modifications.

   ```bash
      git reset <filename>    # unstage a specific file
   ```

<h4 id="git-reset-head">Remove All From Stage - <strong>DICARD</strong> the Modifications</h4>

[Go Back To Summary](#summary)

* To remove files from stage use `reset HEAD`. This will unstage the file(s) and **DISCARD** all the modifications.

   ```bash
      git --hard reset HEAD          # unstage all files
   ```

<h4 id="git-reset-hard-2">Reset HEAD to Last Commit - <strong>DISCARD</strong> the Modifications</h4>

[Go Back To Summary](#summary)

* This will **DISCARD** all the modifications and will set the HEAD to your previous commit(s).

   ```bash
      git reset --hard HEAD~1        # reset last commit
   ```
   * `~1` is the number of commit(s)

<h4 id="git-reset-modes"><a href="https://gist.github.com/CrookedNumber/8964442">Reset [mode] [commit]</a></h4>

[Go Back To Summary](#summary)

* This form resets the current branch head to `<commit>` and possibly updates the index (resetting it to the tree of `<commit>`) and the working tree depending on `<mode>`. If `<mode>` is omitted, defaults to `--mixed`. The `<mode>` must be one of the following:

* **`--soft`**

  * Does not touch the index file or the working tree at all (but resets the head to `<commit>`, just like all modes do). This leaves all your changed files "Changes to be committed", as git status would put it.

* **`--mixed`**

  * Resets the index but not the working tree (i.e., the changed files are preserved but not marked for commit) and reports what has not been updated. This is the default action.
  * If `-N` is specified, removed paths are marked as intent-to-add (see git-add[1]).

* **`--hard`**
  * Resets the index and working tree. Any changes to tracked files in the working tree since `<commit>` are **DISCARDED**.

* **`--merge`**

  * Resets the index and updates the files in the working tree that are different between `<commit>` and HEAD, but keeps those which are different between the index and working tree (i.e. which have changes which have not been added). If a file that is different between `<commit>` and the index has unstaged changes, reset is aborted.
  * In other words, `--merge` does something like a git read-tree `-u -m <commit>`, but carries forward unmerged index entries.

* **`--keep`**

  * Resets index entries and updates files in the working tree that are different between `<commit>` and HEAD. If a file that is different between `<commit>` and HEAD has local changes, reset is aborted.

<h1 id="change-commit-msg">CHANGE COMMIT MESSAGE</h1>

[Go Back To Summary](#summary)

* At some point you’ll find yourself in a situation where you need edit a commit message. That commit might already be pushed or not, be the most recent or burried below 10 other commits

<h4 id="git-commit-msg-not-pushed">Change Commit Message - Not Pushed</h4>

[Go Back To Summary](#summary)

* This will open your $EDITOR and let you change the message. Continue with your usual git push origin master.

   ```bash
      git commit --amend
   ```

<h4 id="git-commit-msg-already-pushed">Change Commit Message - Already Pushed</h4>

[Go Back To Summary](#summary)

* We edit the message like just above. But need to `--force` the push to update the remote history.

* ⚠️ But! Force pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

   ```bash
      git commit --amend
      git push origin master --force
   ```

<h4 id="git-commit-msg-already-not-pushed-old">Change Commit Message - Not Pushed + Old Commit</h4>

[Go Back To Summary](#summary)

* Rebase opened your history and let you pick what to change. With edit you tell you want to change the message. Git moves you to a new branch to let you `--amend` the message. git rebase `--continue` puts you back in your previous branch with the message changed.

   ```bash
      git rebase -i HEAD~X       # X is the number of commits to go back
                                 # Move to the line of your commit, change pick into edit
      git commit --amend         # Change your commit message
      git rebase --continue      # Finish the rebase
   ```

<h4 id="git-commit-msg-pushed-old">Change Commit Message - Already Pushed + Old Commit</h4>

[Go Back To Summary](#summary)

* Edit your message with the same 3 steps process as above (`rebase -i, commit --amend, rebase --continue`). Then force push the commit:

   ```bash
      git push origin master --force
   ```

⚠️ But! Remember re-pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

<h1 id="track-untrack-files">TRACK/UNTRACK FILES</h1>

[Go Back To Summary](#summary)

* There are often times when you want to modify a file but not commit the changes, for example changing the database configuration to run on your local machine.

* Adding the file to .gitignore doesn’t work, because the file is already tracked. Luckily, Git will allow you to manually “ignore” changes to a file or directory.

<h4 id="untrack-pushed-files">Untrack Pushed File (Like .gitignore)</h4>

[Go Back To Summary](#summary)

   ```bash
      git update-index --assume-unchanged <filename>
   ```

<h4 id="track-back-pushed-files">Track Back Ingnored Files</h4>

[Go Back To Summary](#summary)

```bash
   git update-index --no-assume-unchanged <filename>
```

<h4 id="list-ignored-files">List Ignored Files</h4>

[Go Back To Summary](#summary)

* If you  forgot what file did you `--assume-unchanged`, you can call the list using the following command:

* Windows Command

```bash
      git ls-files -v | findstr /B h
```

* Mac/Unix Command

```bash
      git ls-files -v | grep '^h'
```

<h1 id="fetch-modifications">FETCH MODIFICATIONS FROM BRANCH/REMOTE APPLY TO LOCAL</h1>

[Go Back To Summary](#summary)

* Fetch all the remote files that have been changed (just the paths)
   ```bash
      git fetch
   ```

* Pull all the modified files

   ```bash
      git pull origin master/branch
   ```

<h1 id="revert-full-commit">REVERT FULL COMMIT</h1>

[Go Back To Summary](#summary)

* Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.

   ```bash
      git revert {commit_id}
   ```

<h1 id="delete-pushed-files">DELETE COMMITTED FILES</h1>

[Go Back To Summary](#summary)

* 1) Log all the pushed/committed files:

   ```bash
      git log --oneline
   ```

   ```bash
      268186e (HEAD -> master, origin/master, origin/HEAD) remove
      3bdb527 Week 4, Day 1 - Exercise 2 - Express
      1002de7 Week 4, Day 1 - Exercise 1 - Node
      5ed3cc5 rename folders
      bec7979 rename folders
      a6f5fe2 Week 4, Day 1 - Exercise 3 - Lab Express
      b707a70 Week 4, Day 1 - Exercise 2 - Express
      e10d893 Week 4, Day 1 - Exercise 1 - Node
      b92f8b6 Week 4, Day 1 - Exercise 3 - Lab Express
      1ad7b97 Week 4, Day 1 - Exercise 2 - Express
      05694f2 Week 4, Day 1 - Exercise 1 - Node
   ```

* 2) Copy all the hashs that you want to delete from github

   ```bash
      268186e
      3bdb527
      1002de7
      5ed3cc5
      bec7979
      a6f5fe2
      b707a70
      e10d893
      b92f8b6
      1ad7b97
      05694f2
   ```

* 3) Revert the HEAD as many times you need:

   ```bash
      git reset HEAD~1        #this will revert the HEAD 1 commit 

      In this example, we are going to use 

      git reset HEAD~11       #this will revert the HEAD 11 commits 
   ```

* 4) Delete from GitHub

   ```bash
      git push origin +268186e^:master
      git push origin +3bdb527^:master
      git push origin +1002de7^:master
      git push origin +5ed3cc5^:master
      git push origin +bec7979^:master
      git push origin +a6f5fe2^:master
      git push origin +b707a70^:master
      git push origin +e10d893^:master
      git push origin +b92f8b6^:master
      git push origin +1ad7b97^:master
      git push origin +05694f2^:master
   ```

* 5) Double check if everything went all right:

   ```bash
      git pull origin master
      git status
   ```

<h1 id="change-file-path">Change File Path From Repo</h1>

* ⚠️ Before you continue, read all the steps first to understand what will happen to your files/git history.
* If you want to rename or change the file path from repo, first you have to change the file locally and then push the modifications to your repo.

* 1) Use `git rm <./origin path/file> <./destination path/file>`

   ```bash
      # Example:
      
      git mv SCHEDULE.md work/      # Moving SCHEDULE.md from root to folder 'work'
   ```

  * You can rename the file during this process, you just need to change the file name.
  
* 2) `git status`, you will see that git renamed the file and added to stage
  
   ```bash
      Changes to be committed:
         (use "git reset HEAD <file>..." to unstage)

	   renamed:    SCHEDULE.md -> work/SCHEDULE.md
   ```

* 3) Add a commit message `git commit -m "your message"`
* 4) `git push origin master`

* If you check your git history on github, you won't see the previous commits, you will only see your last commit.
  * ⚠️ So far I haven't found a command that can migrate the git history with the destination path/file. One way to view the past commits (before you moved your files) is to use `--follow`. On terminal:

   ```bash
      git log --follow --oneline <./path/file>
   ```
   * This command accepts only one file
   * I doesn't matter if you renamed the file 


<h1 id="github-gist">GitHub GIST</h1>

[Go Back To Summary](#summary)

`https://gist.github.com/Roger-Takeshita`

* **Gist description**: A brief description about your gist

* **File**: Create any file just to GitHub let you create your gist
