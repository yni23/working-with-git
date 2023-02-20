# Working with Git (and GitHub)

Basic commands for managing repositories with `git` and [GitHub](https://github.com)

## Local Setup

1. Create an account on GitHub (skip this step if you already have an account)
2. Configure your GitHub account to use an SSH key - [Instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
1. Make sure your local machine has `git` installed - [Instructions](https://github.com/git-guides/install-git)
2. Install a GitHub client on your local machine
    + Windows - Git bash
    + Linux/Mac - terminal window
    
    UI-based tools are available for using `git` locally, but we will stick with command line clients

# Working with Repositories You Own

You own a repository at GitHub.com and would like to work on its contents locally.

First clone the repository to your local machine.

```bash
git clone git@github.com:username/reponame.git
```

where `username` is your GitHub user name, e.g., `mhscott`, and `reponame` is the name of the repository, e.g., `bennyframe-1.0`.

The `clone` command will copy the current contents of the repository to your local machine.

You will see a `reponame/` subdirectory created in the directory where you issued the `clone` command.

## Local Repository Status

You can check the status of your local repo to find important information like which branch you are on, which tracked files you've modified, which files are not tracked, which files are staged for your next commit, etc.

```bash
git status
```

This will give the status of all directories in your local repo regardless of your current working directory.

Optionally, you can limit the status check to a specific directory, e.g., the current working directory `.`

```bash
git status .
```

## Creating Branches

You will often work simultaneously on multiple features of your code. Branches help you stay organized.

You can obtain a list of the current branches in your local repo

```bash
git branch
```

You should see a `main` branch and any other branches.

The branch with an asterik, e.g., `* main`, is the current working branch.

You can create a new branch to implement a new feature. Give the branch a name you can remember.

```bash
git branch new-feature
```

This command only *creates* the new branch. Type `git branch` and you will see `* main` and `new-feature`.

A second command is required to switch to the new branch.

```bash
git checkout new-feature
```

Now you are on the new branch, which you can verify with `git branch`.

To create a new branch *and* switch to that new branch with one command, use the `-b` option.

```bash
git checkout -b fix-element
```

You can then switch back and forth between branches, e.g., back to `main`

```bash
git checkout main
```

## Commiting Files to Your GitHub Repository

Committing files to your online GitHub repository requires a few steps.

As frequently as you like, you can commit changes in files to any local branch.

```bash
git checkout new-feature
```

To implement this new feature, you make changes to an existing file and/or added new files.

```bash
git status
```

You can see the differences between your current file and its last committed version on your local repo.

```bash
git diff existing-file.cpp
```

Once you are comfortable with the changes you've made and any new files you've added, you can now "stage", or add, the files for a commit.

```bash
git add existing-file.cpp new-file.cpp
```

Do another `git status` and you'll see these files listed as staged for commit.

Now you can commit the files along with a brief message that summarizes the changes you've made.

```bash
git commit -m "Adding stiffness calculation for shear deformations"
```

**Important**: This only commits the modified/new files to your local repository.

One more command is required to push your commits to your repository at GitHub.com.

```bash
git push
```

You should now see your changes/added files listed at `github.com/username/reponame` along with the commit history from your push.

# Working with Forks of Repositories You Do Not Own

Frequently, you want to contribute code back to an existing repository owned by another user or organization, e.g., `github.com/OpenSees/OpenSees`.

In this case, a couple extra steps are necessary, after which the commands described above will suit your workflows.
