<h1 id="summary">Summary</h1>

- [VSCODE SHORTCUTS](#vscode-shortcuts)
  - [Preview Markdown Mac](#preview-markdown-mac)
  - [Preview Markdown Windows](#preview-markdown-windows)
- [SET VSCODE AS DEFAULT EDITOR](#set-vscode-as-default-editor)
  - [Default Editor - MAC](#default-editor---mac)
- [COMMANDS](#commands)
  - [REMOTE](#remote)
    - [Set New Remote Origin](#set-new-remote-origin)
    - [Set New Remote Upstream](#set-new-remote-upstream)
    - [Check Remote/Upstream URL](#check-remoteupstream-url)
    - [Set Different Repos Into a Single Repo](#set-different-repos-into-a-single-repo)
  - [FETCH/PULL MODIFICATIONS](#fetchpull-modifications)
    - [Check All Modifications from Remote (Origin)](#check-all-modifications-from-remote-origin)
    - [Download All Modifications from Remote (Origin/Branch)](#download-all-modifications-from-remote-originbranch)
    - [Download All Modifications from Upstream](#download-all-modifications-from-upstream)
    - [Disable Push to Origin](#disable-push-to-origin)
  - [MERGE CONFLICT](#merge-conflict)
    - [Undo a Merge](#undo-a-merge)
    - [Check for Leftover Conflicts](#check-for-leftover-conflicts)
    - [Check for Leftover Conflicts - Only File Names](#check-for-leftover-conflicts---only-file-names)
  - [LOGS](#logs)
    - [Log Commits (One Line)](#log-commits-one-line)
    - [Log Commits Message Only](#log-commits-message-only)
  - [STASH](#stash)
    - [Stash Uncommitted Files/Changes](#stash-uncommitted-fileschanges)
    - [Apply Stashed Files/Changes](#apply-stashed-fileschanges)
    - [Show Stashed Files/Changes](#show-stashed-fileschanges)
    - [Delete Stashed Files/Changes](#delete-stashed-fileschanges)
  - [TRACK/UNTRACK FILES](#trackuntrack-files)
    - [Untrack Pushed File (Similar to .gitignore)](#untrack-pushed-file-similar-to-gitignore)
    - [Track Back Ignored Files](#track-back-ignored-files)
    - [List Untracked Files](#list-untracked-files)
      - [Windows Command](#windows-command)
      - [Mac/Unix Command](#macunix-command)
  - [CHANGE COMMIT MESSAGE](#change-commit-message)
    - [Change Commit Message - Not Pushed](#change-commit-message---not-pushed)
    - [Change Commit Message - Already Pushed](#change-commit-message---already-pushed)
    - [Change Commit Message - Not Pushed + Old Commit](#change-commit-message---not-pushed--old-commit)
    - [Change Commit Message - Already Pushed + Old Commit](#change-commit-message---already-pushed--old-commit)
  - [BRANCH](#branch)
    - [Create a Branch](#create-a-branch)
    - [List All Branches local/remote](#list-all-branches-localremote)
    - [Switch to Branch](#switch-to-branch)
    - [Create and Switch to Branch (in One Command)](#create-and-switch-to-branch-in-one-command)
    - [Push a Branch](#push-a-branch)
    - [Merge a Branch to Master](#merge-a-branch-to-master)
    - [Delete a Branch](#delete-a-branch)
  - [DISCARD CHANGES](#discard-changes)
    - [Discard Changes - Not Staged](#discard-changes---not-staged)
  - [UNSTAGE](#unstage)
    - [Remove All From Stage - KEEP the Modifications](#remove-all-from-stage---keep-the-modifications)
    - [Remove a Specific File From Stage - KEEP the Modifications](#remove-a-specific-file-from-stage---keep-the-modifications)
  - [RESET](#reset)
    - [Reset HEAD Last Commit - KEEP Modifications NOT Staged](#reset-head-last-commit---keep-modifications-not-staged)
    - [Reset HEAD Last Commit - KEEP Modifications Staged](#reset-head-last-commit---keep-modifications-staged)
    - [Reset HEAD Stage - DISCARD the Modifications](#reset-head-stage---discard-the-modifications)
    - [Reset HEAD to X Commits - DISCARD the Modifications](#reset-head-to-x-commits---discard-the-modifications)
  - [DELETE](#delete)
    - [Delete Pushed Files From Remote/Origin](#delete-pushed-files-from-remoteorigin)
    - [Removing Sensitive Data From a Repository](#removing-sensitive-data-from-a-repository)
  - [REVERT](#revert)
    - [Revert Full Commit](#revert-full-commit)
- [GitHub GIST](#github-gist)
- [HEROKU](#heroku)
  - [LOGIN/CREATE](#logincreate)
    - [Login](#login)
    - [Create App](#create-app)
    - [Associate Existing Heroku App](#associate-existing-heroku-app)
  - [DEPLOY](#deploy)
    - [Deploy to GitHub - Repo](#deploy-to-github---repo)
    - [Deploy to GitHub - Subtree](#deploy-to-github---subtree)

# VSCODE SHORTCUTS

## Preview Markdown Mac

[Go Back to Summary](#summary)

- `CMD+Shift+V`: open README Preview in VSCode

## Preview Markdown Windows

[Go Back to Summary](#summary)

- `Ctrl+Alt+V`: open README Preview in VSCode

# SET VSCODE AS DEFAULT EDITOR

## Default Editor - MAC

[Go Back to Summary](#summary)

- If you manually install Visual Studio Code, rather than using Homebrew, you will need to add the code executable to your PATH.

  ```bash
    brew cask install visual-studio-code
  ```

- **In terminal**

  1. Type: `open ~/.bash_profile`
  2. Delete everything and insert: `export EDITOR="code -w"`

- **In visual studio code**

  1. Press: `CMD + SHIFT + P`
  2. Insert: install code and select from autocomplete menu shell command: `Install 'code'` in command PATH

# COMMANDS

## REMOTE

### [Set New Remote Origin](https://help.github.com/en/articles/changing-a-remotes-url)

[Go Back to Summary](#summary)

```bash
  git remote set-url origin <url>
```

### Set New Remote Upstream

[Go Back to Summary](#summary)

```bash
  git remote add upstream <url>
```

### Check Remote/Upstream URL

[Go Back to Summary](#summary)

```bash
  git remote -v
```

### Set Different Repos Into a Single Repo

[Go Back to Summary](#summary)

- It often happens that while working on one project, you need to use another project from within it. Perhaps it’s a library that a third party developed or that you’re developing separately and using in multiple parent projects. A common issue arises in these scenarios: you want to be able to treat the two projects as separate yet still be able to use one from within the other.
- More information how to clone a project with **submodules** [Official Docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

  ```Bash
    git submodule add <repo_url>
  ```

## FETCH/PULL MODIFICATIONS

### Check All Modifications from Remote (Origin)

[Go Back to Summary](#summary)

- Fetch all the remote files that have been changed (just the paths)
- It doesn't download the modifications

  ```bash
    git fetch
  ```

### Download All Modifications from Remote (Origin/Branch)

[Go Back to Summary](#summary)

- Pull all the modified files

  ```bash
    git pull origin master/branch
  ```

### Download All Modifications from Upstream

[Go Back to Summary](#summary)

- Download all modifications from upstream (a forked repo) to your local machine (master)

  ```Bash
    git pull upstream master
  ```

### Disable Push to Origin

[Go Back to Summary](#summary)

- Disable git from pushing to origin, we can use all features for version control like git pull up upstream

  ```Bash
    git remote set-url --push origin no_push
  ```

## MERGE CONFLICT

### Undo a Merge

[Go Back to Summary](#summary)

- Sometimes we pull the modifications from origin/upstream but we change our mind, and we don't want to merge the modifications on our master branch. But we already pulled.
- This will return to the state before we started the merge at any time.

  ```Bash
    git merge --abort
  ```

### Check for Leftover Conflicts

[Go Back to Summary](#summary)

- List all the file names that have conflicts + the line and highlight as a **conflict**

  ```Bash
    git diff --check | grep -i conflict
  ```

  ```Bash
    d2bs/kolbot/tools/ToolsThread.js:786: leftover conflict marker
    d2bs/kolbot/tools/ToolsThread.js:788: leftover conflict marker
    d2bs/kolbot/tools/ToolsThread.js:791: leftover conflict marker
  ```

### Check for Leftover Conflicts - Only File Names

[Go Back to Summary](#summary)

- List all the file names that have conflicts

  ```Bash
    git ls-files -u | cut -f 2 | sort -u
  ```

  ```Bash
    d2bs/kolbot/tools/ToolsThread.js
  ```

## LOGS

### Log Commits (One Line)

[Go Back to Summary](#summary)

- List all commits in one line, useful to get `hash keys`

  ```bash
    git log --oneline
  ```

### Log Commits Message Only

[Go Back to Summary](#summary)

```bash
  git log -n --pretty=format:%s $hash
```

- **Option 1)** If you want to view the last message, you can just add the `-n` = **number of past commit(s)**, whitout `$hash`. Example:

  ```bash
    git log -1 --pretty=format:%s
  ```

- **Option 2)** IF you want to view a specific commit, you use `-n` = `1` and `$hash` = `hash key`

  ```bash
    git log -n 1--pretty=format:%s a63ef55
  ```

  - `a63ef55` is the hash key

## STASH

### Stash Uncommitted Files/Changes

[Go Back to Summary](#summary)

- To stash all the changes without the need to commit/push

  ```bash
    git stash
  ```

### Apply Stashed Files/Changes

[Go Back to Summary](#summary)

- To apply back the changes

  ```bash
    git stash apply
  ```

### Show Stashed Files/Changes

[Go Back to Summary](#summary)

- Show all the files that you have stashed

  ```bash
    git stash show
  ```

### Delete Stashed Files/Changes

[Go Back to Summary](#summary)

- Discard all the stashed files/changes

  ```bash
    git stash drop
  ```

## TRACK/UNTRACK FILES

[Go Back to Summary](#summary)

- There are often times when you want to modify a file but not commit the changes, for example changing the database configuration to run on your local machine.

- Adding the file to .gitignore doesn’t work, because the file is already tracked. Luckily, Git will allow you to manually “ignore” changes to a file or directory.

### Untrack Pushed File (Similar to .gitignore)

[Go Back to Summary](#summary)

```bash
  git update-index --assume-unchanged <filename>
```

### Track Back Ignored Files

[Go Back to Summary](#summary)

```bash
  git update-index --no-assume-unchanged <filename>
```

### List Untracked Files

[Go Back to Summary](#summary)

- If you forgot what file did you `--assume-unchanged`, you can call the list using the following command:

#### Windows Command

[Go Back to Summary](#summary)

```bash
  git ls-files -v | findstr /B h
```

#### Mac/Unix Command

[Go Back to Summary](#summary)

```bash
  git ls-files -v | grep '^h'
```

## CHANGE COMMIT MESSAGE

[Go Back to Summary](#summary)

- At some point you’ll find yourself in a situation where you need edit a commit message. That commit might already be pushed or not, be the most recent or burried below 10 other commits

### Change Commit Message - Not Pushed

[Go Back to Summary](#summary)

- This will open your \$EDITOR and let you change the message. Continue with your usual git push origin master.

  ```bash
    git commit --amend
  ```

### Change Commit Message - Already Pushed

[Go Back to Summary](#summary)

- We edit the message like just above. But need to `--force` the push to update the remote history.
- ⚠️ But! Force pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

  ```bash
    git commit --amend
    git push origin master --force
  ```

### Change Commit Message - Not Pushed + Old Commit

[Go Back to Summary](#summary)

- Rebase opened your history and let you pick what to change. With edit you tell you want to change the message. Git moves you to a new branch to let you `--amend` the message. git rebase `--continue` puts you back in your previous branch with the message changed.

  ```bash
    git rebase -i HEAD~X       # X is the number of commits to go back
                                # Move to the line of your commit, change pick into edit
    git commit --amend         # Change your commit message
    git rebase --continue      # Finish the rebase
  ```

### Change Commit Message - Already Pushed + Old Commit

[Go Back to Summary](#summary)

- Edit your message with the same 3 steps process as above (`rebase -i, commit --amend, rebase --continue`). Then force push the commit:

  ```bash
    git push origin master --force
  ```

⚠️ But! Remember re-pushing your commit after changing it will very likely prevent others to sync with the repo, if they already pulled a copy. You should first check with them.

## BRANCH

### Create a Branch

[Go Back to Summary](#summary)

```bash
  git branch <branch name>
```

### List All Branches local/remote

[Go Back to Summary](#summary)

```bash
  git branch -a
```

### Switch to Branch

[Go Back to Summary](#summary)

```bash
  git checkout <branch name>
```

### Create and Switch to Branch (in One Command)

[Go Back to Summary](#summary)

```bash
  git checkout -b <branch name>
```

### Push a Branch

[Go Back to Summary](#summary)

- After You've Made the Changes on the Branch
- Add and commit

  ```bash
    git add -A
    git commit -m "message"
  ```

- After Commit, Push Branch to Remote (Origin/Branch)

  ```bash
    git push origin <branch name>
  ```

### Merge a Branch to Master

[Go Back to Summary](#summary)

- Merge a Branch to Local HEAD (Master) and Push to Master to Remote (Origin)

  ```bash
    git checkout master       # to change to master branch
    git pull origin master    # just to be sure that local master is up to date
    git branch --merged       # to check if the branch was merged, right now is just "master"
    git merge <branch name>   # to merge the changes to local master
    git branch --merged       # to check if the branch was merged
    git push origin master    # to push this changes to remote master
  ```

### Delete a Branch

[Go Back to Summary](#summary)

```bash
  git branch -d <branch name>              # to delete local branch
  git push origin --delete <branch name>   # to delete remote branch
```

## DISCARD CHANGES

### Discard Changes - Not Staged

[Go Back to Summary](#summary)

- To revert the file back to the state it was in before the changes. This will put your local git (HEAD) on your last commit and will erase all your modifications.

  ```bash
    git checkout -- <filename>
  ```

## UNSTAGE

[Go Back to Summary](#summary)

- Remove from stage (after `git add -A` , `git add <file>` or `git add .`) - **NOT COMMITTED FILES**

### Remove All From Stage - KEEP the Modifications

[Go Back to Summary](#summary)

- To remove files from stage use `reset HEAD`. This will unstage the file(s) and **KEEP** all the modifications.

  ```bash
    git reset

    #or

    git reset HEAD          # unstage all files
  ```

### Remove a Specific File From Stage - KEEP the Modifications

[Go Back to Summary](#summary)

- Remove from stage (after `git add -A` or `git add <filename>`). This will unstage the file and **KEEP** all the modifications.

  ```bash
    git reset <filename>    # unstage a specific file
  ```

## RESET

### Reset HEAD Last Commit - KEEP Modifications NOT Staged

[Go Back to Summary](#summary)

- This command will delete your last commit (not pushed) and all modification will be **not** staged, so you have to manually `git add` them back to stage.

  ```Bash
      git reset HEAD~1
  ```

  - `~1` is the number of commit(s)
  - [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

### Reset HEAD Last Commit - KEEP Modifications Staged

[Go Back to Summary](#summary)

- This command will delete your last commit (not pushed) and all modification will be in stage

  ```Bash
    git reset --soft HEAD~1
  ```

  - `~1` is the number of commit(s)
  - [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

### Reset HEAD Stage - DISCARD the Modifications

[Go Back to Summary](#summary)

- To remove files from stage use `--hard reset HEAD`. This will unstage the file(s) and **DISCARD** all the modifications.

  ```bash
    git --hard reset HEAD          # unstage all files
  ```

### Reset HEAD to X Commits - DISCARD the Modifications

[Go Back to Summary](#summary)

- This will **DISCARD** all the modifications and will set the HEAD to your previous commit(s).

  ```bash
    git reset --hard HEAD~1        # reset last commit
  ```

  - `~1` is the number of commit(s)
  - [~ vs ^](https://stackoverflow.com/questions/40141493/difference-between-git-reset-hard-head-vs-git-reset-hard-head)

## DELETE

### Delete Pushed Files From Remote/Origin

[Go Back to Summary](#summary)

- 1. Log all the pushed/committed files:

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

- 2. Copy all the hashes that you want to delete from github

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

- 3. Revert the local HEAD as many times you need:

  ```bash
    git reset HEAD~1        #this will revert the HEAD 1 commit and keep the modifications

    In this example, we are going to use

    git reset HEAD~11       #this will revert the HEAD 11 commits
  ```

- 4. Delete from GitHub

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

- 5. Double check if everything went all right:

  ```bash
    git pull origin master
    git status
  ```

### [Removing Sensitive Data From a Repository](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/removing-sensitive-data-from-a-repository)

[Go Back to Summary](#summary)

- Using `filter-branch`

  - **WARNING**: If you run `git filter-branch` after stashing changes, you won't be able to retrieve your changes with other stash commands. Before running git `filter-branch`, we recommend unstashing any changes you've made. To unstash the last set of changes you've stashed, run `git stash show -p | git apply -R`

1. Run the following command, replacing `PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA` with the path to the file you - want to remove, not just its filename. These arguments will:

   - Force Git to process, but not check out, the entire history of every branch and tag
   - Remove the specified file, as well as any empty commits generated as a result
   - Overwrite your existing tags

   ```Bash
      git filter-branch --force --index-filter \
      "git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" \
      --prune-empty --tag-name-filter cat -- --all
   ```

   ```Bash
      # Example

      git filter-branch --force --index-filter \
      "git rm --cached --ignore-unmatch 3-Taks-Manager/env/dev.env" \
      --prune-empty --tag-name-filter cat -- --all

      # Rewrite 48dc599c80e20527ed902928085e7861e6b3cbe6 (266/266)
      # Ref 'refs/heads/master' was rewritten
   ```

2. Add your file with sensitive data to `.gitignore` to ensure that you don't accidentally commit it again.

   ```Bash
      # Example

      echo "YOUR-FILE-WITH-SENSITIVE-DATA" >> .gitignore
      git add .gitignore
      git commit -m "Add YOUR-FILE-WITH-SENSITIVE-DATA to .gitignore"

      # [master 051452f] Add YOUR-FILE-WITH-SENSITIVE-DATA to .gitignore
      #  1 files changed, 1 insertions(+), 0 deletions(-)
   ```

3. Once you're happy with the state of your repository, force-push your local changes to overwrite your GitHub repository, as well as all the branches you've pushed up:

   ```Bash
      git push origin --force --all
   ```

   ```Bash
      # Example

      $ git push origin --force --all

      # Counting objects: 1074, done.
      # Delta compression using 2 threads.
      # Compressing objects: 100% (677/677), done.
      # Writing objects: 100% (1058/1058), 148.85 KiB, done.
      # Total 1058 (delta 590), reused 602 (delta 378)
      # To https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
      #  + 48dc599...051452f master -> master (forced update)
   ```

4. In order to remove the sensitive file from your tagged releases, you'll also need to force-push against your Git tags:

   ```Bash
      git push origin --force --tags
   ```

   ```Bash
      # Example

      $ git push origin --force --tags

      # Counting objects: 321, done.
      # Delta compression using up to 8 threads.
      # Compressing objects: 100% (166/166), done.
      # Writing objects: 100% (321/321), 331.74 KiB | 0 bytes/s, done.
      # Total 321 (delta 124), reused 269 (delta 108)
      # To https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
      #  + 48dc599...051452f master -> master (forced update)
   ```

## REVERT

### Revert Full Commit

[Go Back to Summary](#summary)

- Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.

  ```bash
    git revert {hash key}
  ```

# GitHub GIST

[Go Back to Summary](#summary)

`https://gist.github.com/Roger-Takeshita`

- **Gist description**: A brief description about your gist

- **File**: Create any file just to GitHub let you create your gist

# HEROKU

## LOGIN/CREATE

### Login

[Go Back to Summary](#summary)

```Bash
  heroku login
```

### Create App

[Go Back to Summary](#summary)

```Bash
  heroku create <app_name>
```

### Associate Existing Heroku App

[Go Back to Summary](#summary)

```Bash
  heroku git:remote -a <app_name>
```

## DEPLOY

### Deploy to GitHub - Repo

[Go Back to Summary](#summary)

```Bash
  git push heroku master
```

### Deploy to GitHub - Subtree

[Go Back to Summary](#summary)

```Bash
  git subtree push --prefix path/to/subdirectory heroku master
```

- where `path/to/subdirectory` is the path to the project that you want to deploy to heroku
- for example we have this [repo](https://github.com/Roger-Takeshita/GraphQL)
  - Inside we have a folder called `2_GraphQL_Prisma` (we want to deploy this folder)

```Bash
    git subtree push --prefix 2_GraphQL_Prisma heroku master
```
