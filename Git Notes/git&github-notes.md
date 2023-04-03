# SOURCE AND VERSION CONTROL NOTES

## INITIATING REPO IN DIRECTORY w/ EXISTING FILES

1. Navigate to the local directory that will be turned into a Git repo
2. Run `git init` to initialize the repo in directory
3. Run `git add .` to add all of the files in the directory to the staging area for initial commit
4. Run `git commit -m "Initial commit"`
5. Create a new repository on GH (w/o initializing a README.md)
6. Copy URL of new repo from GH
7. Run `git remote add origin <remote-repository-url>`
8. Run `git push -u origin main`

### GIT MERGE

Command to merge branches --> `git merge`

**Explanation:**

- allows you to combine changes from different branches into a single branch
- used when working on feature branch and want to merge the changes back into the main branch (or master)
- Git compares the two branches & combines changes that have been made

**What is a "Merge Commit"?**

- two parent commits
- shows history of both branches

**How to deal with merge conflicts in VSCode?**

1. Open the Git panel in VSCode.
2. Select the branch that has conflicts and click on the "Merge Changes" button. 
3. Click on a file to open it in the editor. The conflicting sections will be highlighted and marked with the <<<<<<, ======, and >>>>>> markers.
4. To resolve the conflict, edit the code between the <<<<<< and ====== markers to include the changes you want to keep, and remove the <<<<<< and ====== markers. Similarly, edit the code between the ====== and >>>>>> markers to include the changes you want to keep, and remove the ====== and >>>>>> markers.
5. After resolving the conflicts, save the file.
6. After saving the file, stage all changes.
7. Commit the changes.

**Merge Example with GH/Git:**

1. Switch to the branch you want to merge another branch into using the `git checkout` command.
2. Merge other bramch into the current branch using the `git merge` command.
    > Applies all changes from the other brsanch onto the current branch.
3. Resolve merge conflicts.
4. Push the changes to the remote repository to make them available to other users.
    > If merged branch is no longer needed:
    `git branch -d <branch-to-merge>`

**Merge Advantages:**

- PRESERVING ORIGINAL BRANCH HISTORY

    MERGE: useful if working on long-lived branch with many commits and need to keep the original history intact; creates new merge commit with two parent commits, preseerving the history of both branches

    REBASE: end up with linear history and lose some of the original context of the branch

- AVOIDING CONFLICTS

    MERGE: useful for keeping your branch up-to-date with changes from the main branch; conflicts if multiple people working on the same codebase so use to merge changes from multiple branches together and resolve conflicts that arise

- COLLABORATIVE WORKFLOWS

    MERGE: if collaborating with others not familiar with rebasing, easier to use to integrate their changes into your branch to avoid confusion, making it easier for everyone to understand what changes have been made

- MAINTAINING STABLE BRANCH

    MERGE: if working on branch that represents a stable release of your software, use instead of `git rebase` to help ensure that the branch remains stable and any new changes are carefully reviewed and tested before being merged

### GIT BRANCHING

Command to create a new branch & switch to the new branch --> `git checkout -b new-branch`
Alt. Command to create a new branch --> `git branch new-branch`
Command to switch between branches --> `git checkout my-branch`
> *If uncommitted changes in current branch, commit or stash changes before switching branches!*

- allows you to create separate "branches" of your code that can be worked on independently
- useful when working on complex projects with multiple developers
- allows each person to work on separate feature or bug fix without interfereing with each other's work
- each Git branch represents a separate version of the code base, with unique changes and commits

### GIT REBASE

Go to the branch to rebase --> `git checkout my-branch`
Command to rebase on a specific branch --> `git rebase some-branch`

**Explanation:**

- to rebase onto another branch means to essentially move the entire branch so that it starts from the current tip of the other branch
- creates a linear history where ALL changes are applied IN ORDER, making it easier to understand what changes were made and when

**What is `$ git rebase`?**

- alt. way to combine changes from different branches
- rewrites the commit history of the branch
- create a new set of commits that incorporate the changes from the other branch instead of simply merging the two branches together
- useful in some cases, but *risky* and *more difficult* to track changes and revert to earlier versions of the code

**How to deal with conflicts between branches?**

- git will prompt you to resolve conflicts manually before rebase can complete

- After conflicts resolved, continue the rebase:
    `git rebase --continue`

- To abort the rebase and not continue:
    `git rebase --abort`

- Keep a backup of code! *

**Rebase Example w/ Github and Git:**

1. Create a new repository on GH and clone to local machine. `cd` into the repository.
2. Create a new branch (i.e. "feature-branch") and switch to the branch.
3. Make changes to code and commit them.
4. Push the "feature-branch" to GH.
5. Switch to the "main-branch" and make changes.
6. Push the changes on the "main-branch" to GH.
7. Switch back to the "feature-branch" and rebase it onto the "main-branch".
    Default text editor will open and prompt you to resolve any conflicts between the two branches. Choose with version of the conflicting files to keep given both branches have changes made to them.
8. Resolve conflicts and continue the rebase.
9. Force the "rebased feautre-branch" to GH.
10. Verify the changes were pushed to GH.

**Rebase Advantages:**

- COMMIT HISTORY

    REBASE: cleaner commit history due to the linear commit history provided

    MERGE: can become cluttered and harder to read due to parent commits and child commits

- RESOLVING CONFLICTS

    REBASE: changes applied one-by-obe on top of the other branch to easily resolve conflicts as they arise and keep track of what branches certain changes came from

    MERGE: merge commits created even if no conflicts between branches making it harder to see which changes came from which branch if the history needs to be reviewed later

- COLLABORATIVE WORKFLOWS

    REBASE: keeps commit history as clean as possible to make it easier for others to review and understand changes to the code

### GIT ADD

`git add`

- add changes to staging area; prepare the changes to be committed to the local repository
<!-- What is the staging area exactly? Can I have some type of analogy to remember the order of pushing changes to github? -->

### GIT COMMIT

`git commit -m <commit-message>`

- commits changes to the local repository w/ commit message describing the changes
<!-- What is the industry standard rules for writing commit clean messages? -->

### PUSH

`git push`

- pushes the local changes to a remote repository (i.e. Github!)

`git push -u or --upstream`

- pushes local changes to the remote repository on GH (the "official version" of the code)
- allows others to see and access your changes

### FORCE PUSH

`git push -f        <remote-branch> <local-branch>`
`git push --force   <remote-branch> <local-branch>`

- overwrites the remote repository with the local changes, even if they conflict with changes made by others
- **use with caution** --> can result in losing other's changes or creating conflicts
- generally recommended to avoid force pushing unless sure it won't cause problems

### GIT PULL

`git pull`

- fetches changes from the remote repository and merges them into the local branch
<!-- What is the difference between fetching and pulling? Why pull and not rebase or merge? -->

### GIT CLONE

`git clone`

- creates a local copy of a remote repository

### GIT STATUS

`git status`

- displays the current status of the repository (including any changes that have been made)

### GIT LOG

`git log`

- displays a list of all commits in the repository, along with the commit messages and other details

**Staging Area:**

- a.k.a. *index*
- allows you to control which changes you want to include in your next commit
- similar to a "holding area" between your working directory and repository
- review and selectively add changes before they become part of the permanent history
- a checkpoint before making a permanent record of your changes

**What is a "remote" repository?**

- a copy of a repository that's hosted on a server (Github)

**What is a "branch"?**

- a separate line of development within the repository that can be used for experimenting with new features of fixing bugs

- common name for default branch: **origin**

**What is a "pull request"?**

- a.k.a. *PR*
- allows developers to propose changes to a codebase hosted in a remote repository
- a request for the maintainer(s) of a repository to review and merge the changes made in your fork of the repository to the main codebase
- includes a diff of the changes made to the code
- may include discussion around the proposed changes
- maintainer(s) review the changes, provide feedback, and ultimately decide wheter or not to merge the changes into the main codebase

**Why are pull requests important?**

- allow developers to share their code and receive feedback from peers before code is merged into the main codebase
- ensures code is of high quality, follows established coding standards, and is well-documented

**How to do a pull request in Github:**

1. Fork the repository you wish to work on
2. Clone the forked repository to local machine
3. Create a new branch to work on changes
4. Make changes to the codebase in local repository
5. Commit changes w/ commit message
6. Push changes to forked repository on GH
7. Go to repository page and click "Compare & pull request" button (next to the newly pushed branch)
8. Review changes made, add a description for pull request, and confirm pull request creation
9. Repository maintainer(s) will be notifed and can review changes, ask for feedback or revisions, and merge the changes into the main codebase if approved

**FORKING vs. CLONING Explained by ChatGPT:**
When you fork a repository on GitHub, it creates a new copy of the entire repository under your own account on GitHub. This copy is a standalone repository, which means you can clone it to your local machine just like any other repository.

If you clone a repository to your local machine without forking it first, you are creating a copy of the repository on your local machine only. You can modify this copy on your local machine and commit changes to it, but you will not be able to push those changes back to the original repository without first forking it and creating a new copy of the repository under your own account on GitHub.

In short, if you want to contribute changes back to an existing project on GitHub, you should fork the repository first to create your own copy, make your changes to that copy, and then create a pull request to propose your changes to the original repository. If you just want to create a copy of a repository for your own use without contributing back to the original project, you can simply clone the repository to your local machine.

**Branch-naming Conventions:**

- use lowercase letters and hyphens to separate words
    > "feature-add-login-page"

**Common Commit Message Conventions:**

- Use the imperative mood
    > "Add feature" --> NOT "Added feature"
- Keep subject line under 50 characters
- Start with a capital letter
- Use body to provide more detail about the changes and why they were made
- Separate the subject line and body with a blank line

**Mail Analogy:**

- Write the letter (make changes to local file)
- Put the letter in an envelope and address it (stage the changes and write commit message)
- Put letter in mailbox and send off (push the changes to remote repo on GH)

**When to use Git Merge & Git Rebase:**

`git merge` and `git rebase` are both useful when:

- working with multiple branches
- collaborating with others
- managing the history of codebase
- integrating changes from different sources

