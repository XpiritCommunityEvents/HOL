# Setting up your repository
This file describes how you will set up your repository to enable you to do the hands-on labs. We'll migrate from an existing Azure DevOps repository to a Github repository. 
For this bootcamp, we have prepared a public Azure DevOps repository for you and created a private GitHub repository for you.

## Acquire the Azure DevOps repository URL
Before you can clone an existing repo, you'll need an URL that points to the existing repo. This URL represents the source of the repo you're going to copy. 
For the purpose of this bootcamp, we have prepared an Azure DevOps repository for you. 

**For this bootcamp, please use the following URL:** (...) **<TODO**

Normally, you would perform the following steps to obtain the URL of the Azure DevOps repository you want to migrate. 
1. From your web browser, open the team project for your Azure DevOps organization and choose `Repos`, then `Files`.

![](https://docs.microsoft.com/en-us/azure/devops/repos/git/media/clone-repo/repos-files.png?view=azure-devops)

2. Select `Clone` in the upper right. Copy this URL into the clipboard or store it in a place where you can find it easily. You can't clone a repo without a clone URL.

![](https://docs.microsoft.com/en-us/azure/devops/repos/git/media/get_clone_url.gif?view=azure-devops) 

## Clone the repository 
Now, let's clone the Azure DevOps repository into the GitHub repository.
1. Enter the command `git clone [PASTE_AZURE_DEVOPS_REPO_URL_HERE]`. You'll be asked for your credentials. **<TODO: insert Xpirit TailWind Traders repo**

2. Enter the command `git remove origin`. The git remote remove command removes a remote URL from a repository.

3. Currently, your main branch is called `master`. Let's rename it to `main` Enter the command `git branch -m main`. From this point onwards, your main branch will be called `main` instead of `master`.

4. Now, we'll add a new remote pointing to your GitHub repository. Enter the command `git remote add` followed by the URL of your GitHub repo. So, your command would look something like `git remote add https://github.com/user/repo.git` **<TODO: insert appropriate URL structure**

5. Now, let's push the commit to the repository. Enter the command `git push remote main`.
The repository is now migrated from Azure DevOps to GitHub wil full history. In the next part of the bootcamp, we'll look at what is migrated, and what we are missing after the migration.

**^^TODO: validate**
