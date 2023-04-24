# Challenges

As you progress through each chapter you will be given a small set of challenges to complete. In order to complete the challenges there is a complementary GitHub template repository found on the Monash DeepNeuron GitHub organisation called [HPC Training Challenges](https://github.com/MonashDeepNeuron/HPC-Training-Challenges). As a template you are able to create your own copy of the repository and complete the challenges completely independent of the other recruits.

## Setting Up Challenges Repository

To get setup:

- Click the link above to go to the repository on GitHub.
- Click 'Use this template' button (green) and select 'Create a new repository'.
- Give it a name and make sure it is private.
- Ensure you are copying it to your personal account and not the Monash DeepNeuron organisation. There will be a dropdown next to where you give the repo a name from which you can select your account.
- Click 'Create repository from template'.
- This will open the page for the repository. Click the '<> Code' button (green), make sure you are in the HTTPS tab and copy the link.
- Open a terminal in your dev directory.
- Run:

```sh
git clone <repo-link>                                   # Clone to your machine
cd <repo-name>                                          # Enter clone's directory
git remote add upstream <repo-link>                     # Create link to template called 'upstream' 
git remote set-url --push upstream DISABLE              # Disable pushing to template
git fetch upstream                                      # Sync with 'upstream'
git merge upstream/main --allow-unrelated-histories     # Merge 'upstream' main branch with your main
code .
```

This will clone the repository into you current working directory maintaining its link to its `origin` (your remote copy on GitHub) allowing you to sync changes between you local and remote copies. This also sets up a link called `upstream` to the original template directory with pushing disabled. This allows you to sync the base of the repository with your copy, similar to a fork but prevents changes from being pushed to the template.

Once you completed a challenge or made some changes you want to save to your remote repository you can simply add to a commit stage, combine the changes in a commit and then push the commit to `origin`.

```sh
git add .               # Add any untracked or modified files
git commit -m "msg"     # Commit changes locally with a message
git push origin         # Push to your GitHub repository
```

If you need to sync your local repository with the remote version you can either fetch the changes to add them to the logs without modifying the codebase or pull them to integrate the changes into your version.

```sh
git fetch origin    # Sync changes with remote without integrating (downloading) them
git pull origin     # Sync and integrate remote changes locally
```

In order to sync your copy of the challenges repository with the remote template you must re-fetch the changes from `upstream` and then merge the `upstream` remote with your local repository.

```sh
git merge upstream/main --allow-unrelated-histories
```

> Note: Look at the README.md of the repo for the for more instructions.

## Challenges Repository

The challenges repository is broken down into different directories for each chapter. For each chapter their will be a series of additional directories corresponding to the specific challenge. These will contain any and all the resources needed for the challenge except programs that you are required to complete.

When you want to attempt a challenge it is good practice to create a branch. This allows you to make changes to the codebase that do not affect other branches each with their own history. You can then later merge branches to integrate changes together. To create a new branch you can use the `git-branch` command or the the `-b` flag with the `git-checkout` command giving both the name of the new branch. This will branch from your current position in the repositories history. Switching branches is achieved using the `git-checkout` command (with no `-b` flag). You use the regular `git-add`, `git-commit` and `git-push` commands interact and save the changes that only affect this new branch.

```sh
git branch <branch-name>        # Create new branch
git checkout <branch-name>      # Checkout to the new branch
# or
git checkout -b <branch-name    # Checkout to a new branch
```

For your training. I would recommend creating a new branch for every challenge you attempt and merging them with the `main` (default) branch once you are done. This allows you to make modifications to each of your attempts independent of each other as well as make it easier to resync with the template repository should anything change at its base. it also allows you to get some meaningful practice with Git which is one of the most used developer tools in the world.

When you want to merge your changes, checkout back to the `main` branch and run a merge request. This will pull the changes from the deviating branch into main and update it accordingly.

```sh
# On your deviant branch
git fetch origin
git checkout main
git fetch origin
git merge <branch-name>
```

> Note: Merging sometimes creates merge conflicts. This happens when the two branches histories cannot automatically merge. Git has many tools to assist resolving these conflicts and there is a plethora of resources online to assist you. If you get stuck do not hesitate to reach out.
