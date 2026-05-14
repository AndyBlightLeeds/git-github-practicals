# Working In Small Teams

This folder contains this file, and a `design.md` file.  Please follow the instructions below.

## Instructions

There are lots of Git commands in this section, so here is [a handy reference.](../git-commands.md)

### Start work

Now that you have cloned this repo, you can go ahead and create a new branch.  Name the branch with your first name so we can work out who has made each set of changes.

NOTE: If you make a mistake with the name of the branch, you can rename the branch you are on using `git branch -m <new branch name>`.  However, if the branch has been pushed to the server, it is best not to change the local branch name.

1. Open the `design.md` file and add a description of a new feature.  Make it a bit silly or sensible as you want!
1. Save it and then commit that change.
1. Add a new file in this folder, use `<your name>.md`, open it and add a line or two of text.
1. Save it and then commit that change.
1. Now that you have completed your work, review you own changes using `git diff main`.
1. If you don't like the changes, you can fix the problem two ways.
    1. If you have a typo or two, then you can fix the problems and do this:

        ```bash
        git status
        # You should see a changed file.
        git add <changed file>
        git commit --amend
        ```

    1. If you realise that you have missed a big chunk of work, then add the work and commit it in the usual way.

    After either method, then review you code again using `git diff main`.
1. Once you are happy with the changes, `push` your branch to the `origin` repo.

NOTE: This will fail if you don't have access to the repo.  Andy will have to add you as a collaborator before you can push.

**When you get to here, let Andy know and we will wait for the others to catch up.**

Congratulations! You have just completed your changes, so now for the fun bit, getting those changes on to the `main` branch without breaking other people's changes.

### Review the changes

Now that all the branches have been pushed, we want to review the changes.  First, we need to fetch the changes from the server.

* Print out the branches that your repo knows about. `git branch -a`
* Switch back to the `main` branch and `fetch` the latest changes.  You'll see that there is some information about the new branches that have appeared.
* Print out the branches that your repo knows about. `git branch -a`.  You'll see the new branches listed as `remotes\origin\<branch name>`.
* Check the `git log`.  `main` hasn't changed.

NOTE: The `fetch` command fetches the changes from the server but does not update the branch you are on.  When you do a `pull`, it is two commands run one after the other:

```bash
git switch main
# Now do the "pull"
git fetch origin
git merge origin/main
```

When would you use `fetch` instead of `pull`?  You might be working on a local branch and want to check if someone has pushed a new branch for review.  If there is no upstream branch with the same name, or you have local changes, the `pull` command will fail to do the merge, so you'll get an error message.

So how do we do the review?

* Pick one of the new branches and switch to it like this: `git switch <branch name>`.

NOTE: when you do this, it creates a new local branch with the name `<branch name>` that exactly matches the upstream branch `remotes\origin\<branch name>`.

* Check the `git log` to see what changes have been made.
* Use `git diff main` to show the changes.
* Open the changed files and read the changes.

At this point, if we were developing a program, we would run the modified program and test it to make sure the bug has been fixed or the new feature works as expected.  Let the other person know that you have done the review and you are happy with it.

If you want to delete the review branch to keep your repo tidy, use the command  `git branch -d <branch name>`.

### The developer merges their changes

** We are going to take it in turns to to do the merge, so let Andy know and wait here. **

If you are the first one to merge your changes to the `main` branch, you can just type:

```bash
# Make sure you are the main branch
git switch main
# Merge the changes
git merge <your branch name>
# Then you push the changes to origin main.
git push
```

If all goes well, you'll get no error messages.

However, if you don't know if someone else has pushed changes, it is safer to do these commands:

```bash
# Make sure you are the main branch
git switch main
# Pull any changes that have been merged.
git pull
# Merge the changes
git merge <your branch name>
# This may fail! If it does, you'll have to do this.
# Find out what the problems are and resolve them manually.
# You can use the mergetool if installed.
git mergetool
# Otherwise use an editor and fix up the merge errors.
# Commit the merge.
git commit
# Then you push the changes to origin main.
git push
```
