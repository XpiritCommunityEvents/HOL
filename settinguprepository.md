# Migrating your repository from AzureDevops
This hands-on lab has the goal to show you how you can migrate an existing Azure DevOps git repository to GitHub. This is the first step that needs to be finished fo all the other labs to succeed. 

For this bootcamp, we have prepared a public Azure DevOps repository for you and created a private GitHub repository for you.

## Acquire the Azure DevOps Git repository URI
Before you can clone an existing repo, you'll need an URI that points to the existing repo. This URI represents the source of the repo you're going to copy. 
For the purpose of this bootcamp, we have prepared an Azure DevOps repository for you. 

**For this bootcamp, please use the following URL: https://dev.azure.com/xpirit/TailWindTraders**

Normally, you would first start with retrieving the URL of the Azure DevOps repository you want to migrate. For that you would follow the below steps, that are not required  
1. From your web browser, open the team project for your Azure DevOps organization and choose `Repos`, then `Files`.

![get clone uri](https://docs.microsoft.com/en-us/azure/devops/repos/git/media/clone-repo/repos-files.png?view=azure-devops)

2. Select `Clone` in the upper right. Copy this URL into the clipboard or store it in a place where you can find it easily. You can't clone a repo without a clone URL.

![copy clone uri](https://docs.microsoft.com/en-us/azure/devops/repos/git/media/get_clone_url.gif?view=azure-devops) 

## Clone the repository 
Now, let's clone the Azure DevOps repository into the GitHub repository.
Start a command prompt and move to a location where you want to clone the repo. e.g. c:\sources 

Enter the command 
> `git clone [PASTE_AZURE_DEVOPS_REPO_URL_HERE]`

Now we have a cloned repository with the full history on your local drive. Next we want to move this repo with the history to the GitHub repo that is available for you.
You should have access to a GitHub Repo in the organization https://github.com/Microsoft-Bootcamp. This repo has the name `attendee-<yourgithubhandle>`

Now we need to remove the current origin in the git repo that it is pointing to. For this we enter the following command:

> `git remove origin`. 

In our local repo, your main branch is called `master`. Let's rename it to `main`so it matches the expected name in the new target repository at GitHub. for this you enter the command 

>`git branch -m main`.
From this point onwards, your main branch will be called `main` instead of `master`.

Now, we'll add a new remote pointing to your GitHub repository. for this you use the  command 
> `git remote add origin` followed by the URL of your GitHub repo. 

So, your command would look something like `git remote add origin https://github.com/Microsoft-Bootcamp/attendee-<yourgh-handle>.git`

Now we are ready to push the complete repo, including it's history to the GitHub repo.
For this you can use the command:
>`git push -u origin main`

> Note: if you are asking what does the `-u` option do:
> The -u option does the following: For every branch that is up to date or successfully pushed, add upstream (tracking) reference, used by argument-less git-pull and other commands. So, after pushing your local branch with -u option, this local branch will be automatically linked with remote branch, and you can use git pull without any arguments.

The repository is now migrated from Azure DevOps to GitHub with full history. In the next part of the bootcamp, we'll look at what is migrated, and what we are missing after the migration.

# If time permits: Create a Branch Rule
By now your repository at GitHub has content and we can now protecting our branches against unwanted direct updates. This is a very common setup in the enterprise.
In this excersise we will create a branch rule that prevents you to commit to the main branch direct and require you to create a pull request.

In your GitHub repo goto the settings tab and click the branches option as shown here:
![branch protection rules](images/branch-protection-rules.png)

Now add a new rule and define which branch you want to protect. e.g. provide the pattern name `main`
Next you select the following options:
1. `Require pull request reviews before merging`
2. `Include administrators`

Now save this Branch Rule and see if it works.

To check if it works, create a change on one of the files that is in the main branch. Just use the portal to make the change and verify that the moment you want to commit the change you see the below indicator that you need to create a new branch before you can commit:

![create branch before commit](images/branch-before-commit.png)

Now, create a new branch and create a pull request that enables the code review from someone else in your organization/repository.

# If time permits: enforce CODEOWNERS review

If you want to enforce certain teams can only approve parts of the codebase, like a web development team for all the web application code and a docs team for the documentation, you can use the code owners file. We can enforce the code owners need to be part of the review process by adding this to the Branch Protection Rule.
There is already a CODEOWNERS file in the repo that you migrated.

Add to the branch protection rule the option `Require review from Code Owners`
Save the branch protection rule and see if you can enforce that if any file is changed in the documents folder, you need someone from the docs team. Work together in the teams chat to find other attendees that you can add to the team to do the review in a pull request.
