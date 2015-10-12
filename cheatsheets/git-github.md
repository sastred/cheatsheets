# Git & Github Cheatsheet


# Git

https://github.com/oslugr/curso-git

http://marklodato.github.io/visual-git-guide/index-en.html

https://git-scm.com/docs

https://git-scm.com/book/en/v2

https://www.atlassian.com/git/tutorials


## Configuration

Global: ~/.gitconfig

Local: .git/config

**$ git config --list**

**$ git config --global user.name "User Name"**

**$ git config --global user.email "user@email.com"**

**$ git config --global merge.tool meld**

**$ git config --global core.editor vim**

**$ git config --global color.ui true**

**$ git config --global push.default simple** -> New in git V2: only pushes current branch.


## Create/Clone repository

**$ git init**

**$ git clone *url***


## Help, info and state

**$ git help [*command*]**

**$ git status** -> Pending changes in workdir and index.

**$ git show *commit[:file]*** -> (file) status in commit.

**$ git show *commit file*** -> File changes in commit.

**$ git blame *file*** -> Who and when made a change in file.

**$ git reflog** -> History of changes in Tip.

**$ git log [-n] [--graph] [--oneline]** -> Latest (n) commits in repo.


## Differences
*(add --name-status to see only status and name)*

**$ git diff** -> Diff between workdir and index.

**$ git diff --cached** -> Diff between index and latest commit.

**$ git diff HEAD** -> Diff between workdir and HEAD.

**$ git diff *commit1*..*commit2 *[-- *file*]** -> Diff between 2 commits (of a file).

**$ git diff *path* *path*** -> File system diff.

**$ git difftool** -> Diff with external editor.


## Remotes

**$ git remote -v**

**$ git remote add *repo_alias repo_path***

**$ git remote rm *repo_alias***

**$ git remote rename *previous_alias new_alias"**


## Commit

**$ git add *file_or_dir*** -> Adds file changes to index.

**$ git add -u *file_or_dir*** -> Update the index to match the workdir, but adds no new files.

**$ git add -A** -> Adds, modifies, and removes index entries to match workdir.

**$ git commit -m "*msg*"** -> Commit changes from index to the repo.

**$ git commit -a** -> Commit all files that have been modified and deleted. Doesn't add new files.

**$ git commit --amend** -> Adds changes to the latest commit.


## Delete, undo and reset

**$ git clean** -> Deletes unversioned files from workdir.

**$ git rm *file*** -> Deletes from workdir and index.

**$ git rm --cached *file*** -> Deletes only from index.

**$ git reset [*file*]** -> Resets changes from repo to index.

**$ git checkout [*file*]** -> Restores file from index to workdir.

**$ git checkout [*commit*]** -> Restores changes from repo to index and workdir.

**$ git reset --soft [*commit*]** -> Reset current branch to commit leaving changes in workdir.

**$ git reset --mixed [*commit*]** -> Idem in index.

**$ git reset --hard [*commit*]**  -> Idem deleting all changes.


## Push, pull and merge

**$ git fetch *remote branch*** -> Downloads branch changes from remote repo.

**$ git pull *remote branch*** -> git fetch && git merge.

**$ git pull --rebase *remote branch*** -> git fetch && git rebase.

**$ git push *remote branch*** -> Sends branch changes to remote repo.

**$ git merge *branch*** -> Merges *branch* in current branch.


## Rebase

https://git-scm.com/book/en/v2/Git-Branching-Rebasing

**$ git rebase *branch*** -> Moves commits from current branch after *branch* commits. If there are no conflicts, do git checkout *branch *&& git merge *rama_actual* && git commit -m "msg".

**$ git rebase --continue** -> If there are conflicts rebase stops and you have to resolve conflicts manually. Then you can continue the rebase.

**$ git rebase --abort** -> If there are conflicts you can abort the rebase as if nothing has happened.

**$ git rebase -i *branch*** -> Same as first but in interactive mode letting the user edit the list of commits before rebasing.


## Tags

**$ git tag** -> Lists all tags.

**$ git tag -l [*pattern*]** -> Lists all tags that satisfies the pattern.

**$ git tag *tag_name*** -> Creates lightweight tag.

**$ git tag -a *tag_name* -m "msg"** -> Creates annotated tag.

**$ git push --tags** -> Push tags to repo.

**$ git describe [*commit*]** -> Path from last commit to current commit of the tag.


## Branches

**$ git branch [--all] [-vv]** -> Lists (all) branches.

**$ git branch *branch*** -> Creates new branch from current branch.

**$ git branch -d *branch*** -> Deletes branch.

**$ git checkout *branch*** -> Change to branch loosing uncommited changes.

**$ git checkout -b *branch*** -> git branch *branch* && git checkout *branch*.

**$ git push --set-upstream origin *branch*** -> Creates branch in remote repo.

**$ git push origin --delete *branch*** -> Deletes branch in remote repo.


## Stash

**$ git stash** -> Save workdir and index changes in the stash stack.

**$ git stash list** -> Lists all saved stashes.

**$ git stash show [*stash_name*]** -> Shows stash changes.

**$ git stash apply [*stash_name*]** -> Merges the stash in workdir.

**$ git stash drop *stash_name*** -> Deletes stash from the stack.

**$ git stash pop** -> git stash apply && git stash drop.

**$ git stash branch *branch* *stash_name*** -> Creates a new branch, checkout the commit you were on when you stashed your work, reapplies your work there, and then drops the stash if it applies successfull.


# Github
https://hub.github.com

**$ hub fork** -> Creates fork and adds a remote with the username.

**$ hub pull-request** -> Opens editor to write a message and sends a PR.

**$ hub clone repo** -> git clone git://github.com/user/repo.git

**$ hub clone *user/repo*** -> git clone git://github.com/user/repo.git

**$ hub browse -- issues** -> Opens https://github.com/user/repo/issues

**$ hub browse *user/repo* wiki** -> Opens https://github.com/user/repo/wiki