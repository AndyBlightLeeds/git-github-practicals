# Git Commands for the workshop

| Command | Explanation |
| --- | --- |
| `git status` | Shows the status of the repo. |
| `git log` | Shows the revisions on the current branch of the repo. |
| `git switch -c <branch>` | Creates a new branch and switches to it. |
| `git switch <branch>` | Switches to the specified branch. |
| `git branch` | Lists the branches in the current repo. |
| `git branch <branch>` | Creates a new branch but does not switch to it. |
| `git branch  -a` | Lists the branches in the current and any remote repos. |
| `git branch -m <new branch name>` | Modifies the name of the current branch to `<new branch name>` |
| `git branch -d <branch name>` | Deletes the specified branch name. |
| `git diff <branch>` | Show the differences between this branch and the specified `<branch>` |
| `git difftool <branch>` | Show the differences between this branch and the specified `<branch>` in an external program, e.g. `meld` |
| `git commit -am "Commit message"` | Commit the current changeset to the Git repo. |
| `git commit --amend` | Amend the current revision.  Files can be added using `git add`, any modified files are included and the commit message can be edited. |
| `git merge <branch>` | Merges the specified branch into the current branch. |
| `git mergetool <branch>` | Perform the merge in a different program, e.g. `meld`. Great when things go wrong with the automatic merge. |
| `git push --set-upstream origin <your_branch>` | Pushes your local branch to the server. |
| `git checkout -b <branch>` | Creates a new branch and switches to it. |
| `git checkout <branch>` | Switches to the specified branch. |
| `git fetch` | Fetches any changes from the default upstream repo (normally `origin`). |
