# Git & Github Cheatsheet


# Git

http://rogerdudler.github.io/git-guide/

https://www.atlassian.com/git/tutorials

https://git-scm.com/docs

https://git-scm.com/book/en/v2


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

**$ git show _commit [:file]_** -> (file) status in commit.

**$ git blame _file_** -> Who and when made a change in file.

**$ git reflog** -> History of changes in Tip.

**$ git log [-n] [--graph] [--oneline] [--decorate] [--all]** -> Latest (n) commits in repo.


## Differences
*(add --name-status to see only status and name)*

**$ git diff** -> Diff between workdir and index.

**$ git diff --cached** -> Diff between index and latest commit.

**$ git diff HEAD** -> Diff between workdir and HEAD.

**$ git diff *commit1*..*commit2 *[-- *file*]** -> Diff between 2 commits (of a file).

**$ git diff *path* _path_** -> File system diff.

**$ git difftool** -> Diff with external editor.


## Remotes

**$ git remote -v**

**$ git remote add *repo_alias repo_path***

**$ git remote rm _repo_alias_**

**$ git remote rename _previous_alias new_alias_**


## Commit

**$ git add _file_or_dir_** -> Adds file changes to index.

**$ git add -u _file_or_dir_** -> Update the index to match the workdir, but adds no new files.

**$ git add -A** -> Adds, modifies, and removes index entries to match workdir.

**$ git commit -m "*msg*"** -> Commit changes from index to the repo.

**$ git commit -a** -> Commit all files that have been modified and deleted. Doesn't add new files.

**$ git commit --amend** -> Adds changes to the latest commit.


## Delete, undo and reset

**$ git clean** -> Deletes unversioned files from workdir.

**$ git rm _file_** -> Deletes from workdir and index.

**$ git rm --cached _file_** -> Deletes only from index.

**$ git checkout [*file*]** -> Restores file from index to workdir.

**$ git checkout -- _filename_** -> Restores file from repo to workdir without modifying the index.

**$ git checkout [*commit*]** -> Restores changes from repo to index and workdir.

**$ git reset [*file*]** -> Resets changes from repo to index.

**$ git reset --soft [*commit*]** -> Reset current branch to commit leaving changes in index.

**$ git reset --mixed [*commit*]** -> Idem in workdir.

**$ git reset --hard [*commit*]**  -> Idem deleting all changes.


## Push, pull and merge

**$ git fetch _remote branch_** -> Downloads branch changes from remote repo.

**$ git pull _remote branch_** -> git fetch && git merge.

**$ git pull --rebase _remote branch_** -> git fetch && git rebase.

**$ git push _remote branch_** -> Sends branch changes to remote repo.

**$ git merge _branch_** -> Merges *branch* in current branch.


## Rebase

https://git-scm.com/book/en/v2/Git-Branching-Rebasing

**$ git rebase _branch_** -> Moves commits from current branch after *branch* commits. If there are no conflicts, do git checkout *branch* && git merge *current_branch* && git commit -m "msg".

**$ git rebase --continue** -> If there are conflicts rebase stops and you have to resolve conflicts manually. Then you can continue the rebase.

**$ git rebase --abort** -> If there are conflicts you can abort the rebase as if nothing has happened.

**$ git rebase -i _branch_** -> Same as first but in interactive mode letting the user edit the list of commits before rebasing.


## Tags

**$ git tag** -> Lists all tags.

**$ git tag -l [*pattern*]** -> Lists all tags that satisfies the pattern.

**$ git tag _tag_name_** -> Creates lightweight tag.

**$ git tag -a *tag_name* -m "msg"** -> Creates annotated tag.

**$ git push --tags** -> Push tags to repo.

**$ git describe [*commit*]** -> Path from last commit to current commit of the tag.


## Branches

**$ git branch [--all] [-vv]** -> Lists (all) branches.

**$ git branch _branch_** -> Creates new branch from current branch.

**$ git branch -d _branch_** -> Deletes branch.

**$ git checkout _branch_** -> Change to branch loosing uncommited changes.

**$ git checkout -b _branch_** -> git branch *branch* && git checkout *branch*.

**$ git push --set-upstream *remote* _branch_** -> Creates branch in remote repo.

**$ git push *remote* --delete _branch_** -> Deletes branch in remote repo.


## Stash

**$ git stash** -> Save workdir and index changes in the stash stack.

**$ git stash list** -> Lists all saved stashes.

**$ git stash show [*stash_name*]** -> Shows stash changes.

**$ git stash apply [*stash_name*]** -> Merges the stash in workdir.

**$ git stash drop _stash_name_** -> Deletes stash from the stack.

**$ git stash pop** -> git stash apply && git stash drop.

**$ git stash branch *branch* _stash_name_** -> Creates a new branch, checkout the commit you were on when you stashed your work, reapplies your work there, and then drops the stash if it applies successfull.


# Github
https://hub.github.com

**$ hub fork** -> Creates fork and adds a remote with the username.

**$ hub pull-request** -> Opens editor to write a message and sends a PR.

**$ hub clone repo** -> git clone git://github.com/user/repo.git

**$ hub clone _user/repo_** -> git clone git://github.com/user/repo.git

**$ hub browse -- issues** -> Opens https://github.com/user/repo/issues

**$ hub browse *user/repo* wiki** -> Opens https://github.com/user/repo/wiki
