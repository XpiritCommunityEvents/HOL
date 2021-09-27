# Frequently Asked Questions and Common Errors
This document is a collection of frequently asked questions and common errors that can occur during the execution of the hands on labs, including information on how to solve them.
Feel free to contribute any of your additions: please make the change and create a pull request so your colleagues can benefit in next bootcamp sessions.

## Auto-generated environment variables in the workflow have the wrong casing
**HOL:** [Creating a custom mapping to override the default behavior or non existing mappings](https://github.com/Microsoft-Bootcamp/HOL/blob/main/Adding-Custom-Mappings-for-your-migrations.md)

**Error:**

**Cause of issue:** 
When you run a migration of a pipeline, it generates a set of environment variables. The generated environment variables are all in upper case, but the references to the variables is still Pascal casing as the original casing in the source pipeline. This will result in a failing workflow, since the workflow run on Linux is case sensitive.

**Remediation:** Manually edit the workflow file and ensure the environment variable uses capitals. Perform the following steps:
1. Navigate to your workflow file (`.github/workflows/classic_ci.yml`) and edit the file.
2. Update `${{ env.BuildConfiguration }}` in lines 28, 31 and 34 to `${{ env.BUILDCONFIGURATION }}` and save the file.
3. Rerun the workflow and validate its run in the run history.
**Known issue logged with GitHub:** [https://github.com/github/valet/issues/3125](https://github.com/github/valet/issues/3125)

## Error code 401 - 
**HOL:** [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)

**Error:** 

**Error description:**

**Remediation:** Are you sure you have set the right scope when generating your Personal Access Token? It should have at least scope for `read:packages` and `workflow`. If you are unsure, it is best to generate a new Personal Access Token as you can't change the scope on an existing token. To create a new token, please follow the below steps:
- Go to your GitHub settings > Developer settings > Personal Access Tokens.
- Create a new Personal Access Token that has the scope set for at least `read:packages` and `workflow`.
- Update your Personal Access Token and retry the steps.

## Error 404 when running Valet migrate command
**HOL:** [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)

## Error 422 - Invalid request, "sha" wasn't supplied
**HOL:** [Setting up Code Scanning and Security Scanning for your repository](https://github.com/Microsoft-Bootcamp/HOL/blob/main/codescanning.md)

**Error:** >PUT https://api.github.com/repos/Microsoft-Bootcamp/attendee-<yourGitHubhandle>/contents/.github/workflows/classic_ci.yml: 422 - Invalid request.
  
**Error description:** When we created the `.github/workflows/classic_ci.yml` in the 
  
**Remediation:** To remediate this issue, delete or rename the original `.github/workflows/classic_ci.yml` file. 
  
## Artifact copy
**HOL:** []()
  
**Error description:**
  
**Remediation:** 
Remediation
