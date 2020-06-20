<h1 id="summary">Summary</h1>

-   [VSCode Shortcuts](#shortcuts)
    -   [Preview Markdown Mac | CMD+Shift+V](#shortcut-mac)
    -   [Preview Markdown Windows | Ctrl+Alt+V](#shortcut-win)
-   [Set VSCode as Default Editor](#vscode-default-editor)
    -   [Default Editor - MAC](#defaul-editor-mac)
-   [COMMANDS](#commands)

    -   [REMOTE](#remote)

        -   [Set New Remote Origin | git remote set-url origin](#git-set-origin)
        -   [Set New Remote Upstream | git remote add upstream](#git-upstream)
        -   [Check Remote/Upstream URL | git remote -v](#git-check-remote)

    -   [FETCH/PULL](#fetchpull)

        -   [Check All Modifications from Remote (Origin) | git fetch](#fetch-modifications)
        -   [Download All Modifications from Remote (Origin/Branch) | git pull origin master](#pullmodification)
        -   [Download All Modifications from Upstream](#gitpullup)
        -   [Block repo from pushing to origin](#gitnopush)

    -   [MERGE CONFLICT](#mergeconflict)

        -   [Undo a Merge | git merge --abort](#gitmergeabort)
        -   [Check for Leftover Conflicts | git diff --check | grep -i conflict](#gitdiff1)
        -   [Check for Leftover Conflicts - Only File Names | git ls-files -u | cut -f 2 | sort -u](#gitdiff2)

    -   [LOGS](#logs)

        -   [Log Commits (One Line) | git log --oneline](#git-log)
        -   [Log Commits Message Only | git log -1 --pretty=format:%s](#git-log-msg)

    -   [STASH](#git-stash)

        -   [Stash Uncommitted Files/Changes | git stash](#git-stash-changes)
        -   [Apply Stashed Files/Changes | git stash apply](#git-stash-apply)
        -   [Show Stashed Files/Changes | git stash show](#git-stash-show)
        -   [Delete Stashed Files/Changes | git stash drop](#git-stash-drop)

    -   [TRACK/UNTRACK FILES](#track-untrack-files)

        -   [Untrack Pushed File (Similar to .gitignore) | git update-index --assume-unchanged](#untrack-pushed-files)
        -   [Track Back Ignored Files | git update-index --no-assume-unchanged](#track-back-pushed-files)
        -   [List Untracked Files](#list-untracked-files)
            -   [Windows Command | git ls-files -v | findstr /B h](#untrackwindows)
            -   [Mac/Unix Command | git ls-files -v | grep '^h'](#untrackunix)

    -   [CHANGE COMMIT MESSAGE](#change-commit-msg)

        -   [Change Commit Message - Not Pushed | git commit --amend](#git-commit-msg-not-pushed)
        -   [Change Commit Message - Already Pushed | git commit --amend](#git-commit-msg-already-pushed)
        -   [Change Commit Message - Not Pushed + Old Commit](#git-commit-msg-already-not-pushed-old)
        -   [Change Commit Message - Already Pushed + Old Commit](#git-commit-msg-pushed-old)

    -   [BRANCH](#branch)

        -   [Create a Branch | git branch](#createbranch)
        -   [List All Branches local/remote | git branch -a](#listbranches)
        -   [Switch to Branch | git checkout](#switchtobranch)
        -   [Create and Switch to Branch (in One Command) | git checkout -b](#xxxxxxxxxx)
        -   [Push a Branch | git push origin](#pushbranch)
        -   [Merge a Branch to Master | git merge](#mergebranch)
        -   [Delete a Branch | git branch -d](#deletebranch)

    -   [DISCARD CHANGES](#discard)

        -   [Discard Changes - Not Staged | git checkout --](#discard-not-committed-changes)

    -   [UNSTAGE](#unstage)

        -   [Remove All From Stage - KEEP the Modifications | git reset](#git-reset-head-file)
        -   [Remove a Specific File From Stage - KEEP the Modifications | git reset](#git-reset-file)

    -   [RESET](#reset)

        -   [Reset HEAD Last Commit - KEEP Modifications NOT Staged | git reset HEAD~1](#gitresetmixed)
        -   [Reset HEAD Last Commit - KEEP Modifications Staged | git reset --soft HEAD~1](#gitresetsoft)
        -   [Reset HEAD Stage - DISCARD the Modifications | git --hard reset HEAD](#githardreset1)
        -   [Reset HEAD to X Commits - DISCARD the Modifications | git reset --hard HEAD~1](#githardreset2)

    -   [DELETE](#delete)

        -   [Delete Pushed Files From Origin | git push origin +268186e^:master](#delete-pushed-files)

    -   [REVERT](#revert)

        -   [Revert Full Commit | git revert {hash key}](#revert-full-commit)

-   [GitHub Gist](#github-gist)
-   [Heroku](#heroku)

    -   [LOGIN/CREATE](#logincreate)

        -   [Login | heroku login](#herokulogin)
        -   [Create App | heroku create](#herokucreate)
        -   [Associate Existing Heroku App | heroku git:remote -a](#associateapp)

    -   [DEPLOY](#deploy)

        -   [Deploy to GitHub - Repo | git push heroku master](#deploytogit)
        -   [Deploy to GitHub - Subtree](#deploytogitsubtree)

<h1 id="shortcuts">VSCODE SHORTCUTS</h1>

<h2 id="shortcut-mac">Preview Markdown Mac</h2>

[Go Back To Summary](#summary)

-   `CMD+Shift+V`: open README Preview in VSCode

<h2 id="shortcut-win">Preview Markdown Windows</h2>

[Go Back To Summary](#summary)

-   `Ctrl+Alt+V`: open README Preview in VSCode

<h1 id="vscode-default-editor">SET VSCODE AS DEFAULT EDITOR</h1>

<h2 id="defaul-editor-mac">Default Editor - MAC</h2>

[Go Back To Summary](#summary)

-   If you manually install Visual Studio Code, rather than using Homebrew, you will need to add the code executable to your PATH.

    ```bash
      brew cask install visual-studio-code
    ```

-   **In terminal**

    1. Type: `open ~/.bash_profile`
    2. Delete everything and insert: `export EDITOR="code -w"`

-   **In visual studio code**

    1. Press: `CMD + SHIFT + P`
    2. Insert: install code and select from autocomplete menu shell command: `Install 'code'` in command PATH

<h1 id="commands">Commands</h1>

<h2 id='remote'>REMOTE</h2>

<h3 id="git-set-origin"><a href="https://help.github.com/en/articles/changing-a-remotes-url">Set New Remote Origin</a></h3>

[Go Back To Summary](#summary)

```bash
  git remote set-url origin <url>
```

<h3 id="git-upstream">Set New Remote Upstream</h3>

[Go Back To Summary](#summary)

```bash
  git remote add upstream <url>
```

<h3 id="git-check-remote">Check Remote/Upstream URL</h3>

[Go Back To Summary](#summary)

```bash
  git remote -v
```

<h2 id='fetchpull'>FETCH/PULL MODIFICATIONS</h2>

<h3 id="fetch-modifications">Check All Modifications from Remote (Origin)</h3>

[Go Back To Summary](#summary)

-   Fetch all the remote files that have been changed (just the paths)
-   It doesn't download the modifications

    ```bash
      git fetch
    ```

<h3 id='pullmodification'>Download All Modifications from Remote (Origin/Branch)</h3>

[Go Back to Summary](#summary)

-   Pull all the modified files

    ```bash
      git pull origin master/branch
    ```

<h3 id='gitpullup'>Download All Modifications from Upstream</h3>

[Go Back to Summary](#summary)

-   Download all modifications from upstream (a forked repo) to your local machine (master)

    ```Bash
      git pull upstream master
    ```

<h3 id='gitnopush'>Disable Push to Origin</h3>

[Go Back to Summary](#summary)

-   Disable git from pushing to origin, we can use all features for version control like git pull up upstream

    ```Bash
      git remote set-url --push origin no_push
    ```

<h2 id='mergeconflict'>MERGE CONFLICT</h2>

<h3 id='gitmergeabort'>Undo a Merge</h3>

[Go Back to Summary](#summary)

-   Sometimes we pull the modifications from origin/upstream but we change our mind, and we don't want to merge the modifications on our master branch. But we already pulled.
-   This will return to the state before we started the merge at any time.

    ```Bash
      git merge --abort
    ```

<h3 id='gitdiff1'>Check for Leftover Conflicts</h3>

[Go Back to Summary](#summary)

-   List all the file names that have conflicts + the line and highlight as a **conflict**

    ```Bash
      git diff --check | grep -i conflict
    ```

    ```Bash
      d2bs/kolbot/tools/ToolsThread.js:786: leftover conflict marker
      d2bs/kolbot/tools/ToolsThread.js:788: leftover conflict marker
      d2bs/kolbot/tools/ToolsThread.js:791: leftover conflict marker
    ```

<h3 id='gitdiff2'>Check for Leftover Conflicts - Only File Names</h3>

[Go Back to Summary](#summary)

-   List all the file names that have conflicts

    ```Bash
      git ls-files -u | cut -f 2 | sort -u
    ```

    ```Bash
      d2bs/kolbot/tools/ToolsThread.js
    ```

<h2 id='logs'>LOGS</h2>

<h3 id="git-log">Log Commits (One Line) </h3>

[Go Back To Summary](#summary)

-   List all commits in one line, useful to get `hash keys`

    ```bash
      git log --oneline
    ```

<h3 id="git-log-msg">Log Commits Message Only</h3>

[Go Back To Summary](#summary)

```bash
  git log -n --pretty=format:%s $hash
```

-   **Option 1)** If you want to view the last message, you can just add the `-n` = **number of past commit(s)**, whitout `$hash`. Example:

    ```bash
      git log -1 --pretty=format:%s
    ```

-   **Option 2)** IF you want to view a specific commit, you use `-n` = `1` and `$hash` = `hash key`

    ```bash
      git log -n 1--pretty=format:%s a63ef55
    ```

    -   `a63ef55` is the hash key

<h2 id="git-stash">STASH</h2>

<h3 id="git-stash-changes">Stash Uncommitted Files/Changes</h3>

[Go Back To Summary](#summary)

-   To stash all the changes without the need to commit/push

    ```bash
      git stash
    ```

<h3 id="git-stash-apply">Apply Stashed Files/Changes</h3>

[Go Back To Summary](#summary)

-   To apply back the changes

    ```bash
      git stash apply
    ```

<h3 id="git-stash-show">Show Stashed Files/Changes</h3>

[Go Back To Summary](#summary)

-   Show all the files that you have stashed

    ```bash
      git stash show
    ```

<h3 id="git-stash-drop">Delete Stashed Files/Changes</h3>

[Go Back To Summary](#summary)

-   Discard all the stashed files/changes

    ```bash
      git stash drop
    ```

<h2 id="track-untrack-files">TRACK/UNTRACK FILES</h2>

[Go Back To Summary](#summary)

-   There are often times when you want to modify a file but not commit the changes, for example changing the database configuration to run on your local machine.

-   Adding the file to .gitignore doesn’t work, because the file is already tracked. Luckily, Git will allow you to manually “ignore” changes to a file or directory.

<h3 id="untrack-pushed-files">Untrack Pushed File (Similar to .gitignore)</h3>

[Go Back To Summary](#summary)

```bash
  git update-index --assume-unchanged <filename>
```

<h3 id="track-back-pushed-files">Track Back Ignored Files</h3>

[Go Back To Summary](#summary)

```bash
  git update-index --no-assume-unchanged <filename>
```

<h3 id="list-untracked-files">List Untracked Files</h3>

[Go Back To Summary](#summary)

-   If you forgot what file did you `--assume-unchanged`, you can call the list using the following command:

<h4 id='untrackwindows'>Windows Command</h4>

```bash
  git ls-files -v | findstr /B h
```

<h4 id='untrackunix'>Mac/Unix Command</h4>

```bash
  git ls-files -v | grep '^h'
```

<h2 id="change-commit-msg">CHANGE COMMIT MESSAGE</h2>

-   At some point you’ll find yourself in a situation where you need edit a commit message. That commit might already be pushed or not, be the most recent or burried below 10 other commits

<h3 id="git-commit-msg-not-pushed">Change Commit Message - <strong>Not Pushed</strong></h3>

[Go Back To Summary](#summary)

-   This will open your \$EDITOR and let you change the message. Continue with your usual git push origin master.

    ```bash
      git commit --amend
    ```

<h3 id="git-commit-msg-already-pushed">Change Commit Message - <strong>Already Pushed</strong></h3>

[Go Back To Summary](#summary)

-   We edit the message like just above. But need to `--force` the push to update the remote history.
-   ⚠️ But! Force pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

    ```bash
      git commit --amend
      git push origin master --force
    ```

<h3 id="git-commit-msg-already-not-pushed-old">Change Commit Message - <strong>Not Pushed + Old Commit</strong></h3>

[Go Back To Summary](#summary)

-   Rebase opened your history and let you pick what to change. With edit you tell you want to change the message. Git moves you to a new branch to let you `--amend` the message. git rebase `--continue` puts you back in your previous branch with the message changed.

    ```bash
      git rebase -i HEAD~X       # X is the number of commits to go back
                                  # Move to the line of your commit, change pick into edit
      git commit --amend         # Change your commit message
      git rebase --continue      # Finish the rebase
    ```

<h3 id="git-commit-msg-pushed-old">Change Commit Message - <strong>Already Pushed + Old Commit</strong></h3>

[Go Back To Summary](#summary)

-   Edit your message with the same 3 steps process as above (`rebase -i, commit --amend, rebase --continue`). Then force push the commit:

    ```bash
      git push origin master --force
    ```

⚠️ But! Remember re-pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

<h2 id="branch">BRANCH</h2>

<h3 id='createbranch'>Create a Branch</h3>

[Go Back to Summary](#summary)

```bash
  git branch <branch name>
```

<h3 id='listbranches'>List All Branches local/remote</h3>

[Go Back to Summary](#summary)

```bash
  git branch -a
```

<h3 id='switchtobranch'>Switch to Branch</h3>

[Go Back to Summary](#summary)

```bash
  git checkout <branch name>
```

<h3 id='createswitchbranch'>Create and Switch to Branch (in One Command)</h3>

[Go Back to Summary](#summary)

```bash
  git checkout -b <branch name>
```

<h3 id='pushbranch'>Push a Branch</h3>

[Go Back to Summary](#summary)

-   After You've Made the Changes on the Branch
-   Add and commit

    ```bash
      git add -A
      git commit -m "message"
    ```

-   After Commit, Push Branch to Remote (Origin/Branch)

    ```bash
      git push origin <branch name>
    ```

<h3 id='mergebranch'>Merge a Branch to Master</h3>

[Go Back to Summary](#summary)

-   Merge a Branch to Local HEAD (Master) and Push to Master to Remote (Origin)

    ```bash
      git checkout master       # to change to master branch
      git pull origin master    # just to be sure that local master is up to date
      git branch --merged       # to check if the branch was merged, right now is just "master"
      git merge <branch name>   # to merge the changes to local master
      git branch --merged       # to check if the branch was merged
      git push origin master    # to push this changes to remote master
    ```

<h3 id='deletebranch'>Delete a Branch</h3>

[Go Back to Summary](#summary)

```bash
  git branch -d <branch name>              # to delete local branch
  git push origin --delete <branch name>   # to delete remote branch
```

<h2 id='discard'>DISCARD CHANGES</h2>

[Go Back to Summary](#summary)

<h3 id="discard-not-committed-changes">Discard Changes - <strong>Not Staged</strong></h3>

[Go Back To Summary](#summary)

-   To revert the file back to the state it was in before the changes. This will put your local git (HEAD) on your last commit and will erase all your modifications.

    ```bash
      git checkout -- <filename>
    ```

<h2 id="unstage">UNSTAGE</h2>

-   Remove from stage (after `git add -A` , `git add <file>` or `git add .`) - **NOT COMMITTED FILES**

<h3 id="git-reset-head-file">Remove All From Stage - <strong>KEEP</strong> the Modifications</h3>

[Go Back To Summary](#summary)

-   To remove files from stage use `reset HEAD`. This will unstage the file(s) and **KEEP** all the modifications.

    ```bash
      git reset

      #or

      git reset HEAD          # unstage all files
    ```

<h3 id="git-reset-file">Remove a Specific File From Stage - <strong>KEEP</strong> the Modifications</h3>

[Go Back To Summary](#summary)

-   Remove from stage (after `git add -A` or `git add <filename>`). This will unstage the file and **KEEP** all the modifications.

    ```bash
      git reset <filename>    # unstage a specific file
    ```

<h2 id='reset'>RESET</h2>

<h3 id='gitresetmixed'>Reset HEAD Last Commit - <strong>KEEP</strong> Modifications <strong>NOT</strong> Staged</h3>

[Go Back to Summary](#summary)

-   This command will delete your last commit (not pushed) and all modification will be **not** staged, so you have to manually `git add` them back to stage.

    ```Bash
        git reset HEAD~1
    ```

    -   `~1` is the number of commit(s)
    -   [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

<h3 id='gitresetsoft'>Reset HEAD Last Commit - <strong>KEEP</strong> Modifications Staged</h3>

[Go Back to Summary](#summary)

-   This command will delete your last commit (not pushed) and all modification will be in stage

    ```Bash
      git reset --soft HEAD~1
    ```

    -   `~1` is the number of commit(s)
    -   [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

<h3 id="githardreset1">Reset HEAD Stage - <strong>DISCARD</strong> the Modifications</h3>

[Go Back To Summary](#summary)

-   To remove files from stage use `--hard reset HEAD`. This will unstage the file(s) and **DISCARD** all the modifications.

    ```bash
      git --hard reset HEAD          # unstage all files
    ```

<h3 id="githardreset2">Reset HEAD to X Commits - <strong>DISCARD</strong> the Modifications</h3>

[Go Back To Summary](#summary)

-   This will **DISCARD** all the modifications and will set the HEAD to your previous commit(s).

    ```bash
      git reset --hard HEAD~1        # reset last commit
    ```

    -   `~1` is the number of commit(s)
    -   [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

<h2 id='delete'>DELETE</h2>

<h3 id="delete-pushed-files">Delete Pushed Files From Origin</h3>

[Go Back To Summary](#summary)

-   1. Log all the pushed/committed files:

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

-   2. Copy all the hashes that you want to delete from github

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

-   3. Revert the local HEAD as many times you need:

    ```bash
      git reset HEAD~1        #this will revert the HEAD 1 commit and keep the modifications

      In this example, we are going to use

      git reset HEAD~11       #this will revert the HEAD 11 commits
    ```

-   4. Delete from GitHub

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

-   5. Double check if everything went all right:

    ```bash
      git pull origin master
      git status
    ```

<h2 id='revert'>REVERT</h2>

<h3 id="revert-full-commit">REVERT FULL COMMIT</h3>

[Go Back To Summary](#summary)

-   Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.

    ```bash
      git revert {hash key}
    ```

<h1 id="github-gist">GitHub GIST</h1>

[Go Back To Summary](#summary)

`https://gist.github.com/Roger-Takeshita`

-   **Gist description**: A brief description about your gist

-   **File**: Create any file just to GitHub let you create your gist

<h1 id='heroku'>Heroku</h1>

<h2 id='logincreate'>LOGIN/CREATE</h2>

<h3 id='herokulogin'>Login</h3>

[Go Back to Summary](#summary)

```Bash
  heroku login
```

<h3 id='herokucreate'>Create App</h3>

[Go Back to Summary](#summary)

```Bash
  heroku create <app_name>
```

<h3 id='associateapp'>Associate Existing Heroku App</h3>

[Go Back to Summary](#summary)

```Bash
  heroku git:remote -a <app_name>
```

<h2 id='deploy'>DEPLOY</h2>

<h3 id='deploytogit'>Deploy to GitHub - Repo</h3>

[Go Back to Summary](#summary)

```Bash
  git push heroku master
```

<h3 id='deploytogitsubtree'>Deploy to GitHub - Subtree</h3>

[Go Back to Summary](#summary)

```Bash
  git subtree push --prefix path/to/subdirectory heroku master
```

-   where `path/to/subdirectory` is the path to the project that you want to deploy to heroku
-   for example we have this [repo](https://github.com/Roger-Takeshita/GraphQL)
    -   Inside we have a folder called `2_GraphQL_Prisma` (we want to deploy this folder)

```Bash
    git subtree push --prefix 2_GraphQL_Prisma heroku master
```
