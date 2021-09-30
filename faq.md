# Frequently Asked Questions and Common Errors
This document is a collection of frequently asked questions and common errors that can occur during the execution of the hands on labs, including information on how to solve them.
Feel free to contribute any of your additions: please make the change and create a pull request so that other attendees can benefit in next bootcamp sessions.

## Auto-generated environment variables in the workflow have the wrong casing
**HOL:** [Adding Custom Mappings for you migrations](https://github.com/Microsoft-Bootcamp/HOL/blob/main/Adding-Custom-Mappings-for-your-migrations.md)

**Cause of issue:** 
When you run a migration of a pipeline, it generates a set of environment variables. The generated environment variables are all in upper case, but the references to the variables is still Pascal casing as the original casing in the source pipeline. This will result in a failing workflow, since the workflow run on Linux is case sensitive.

**Known issue logged with GitHub:** [https://github.com/github/valet/issues/3125](https://github.com/github/valet/issues/3125)

**Remediation:** Manually edit the workflow file and ensure the environment variable uses capitals. Perform the following steps:
1. Navigate to your workflow file (`.github/workflows/classic_ci.yml`) and edit the file.
2. Update `${{ env.BuildConfiguration }}` in lines 28, 31 and 34 to `${{ env.BUILDCONFIGURATION }}` and save the file.
3. Rerun the workflow and validate its run in the run history.

## Error 401 returned when performing a Valet dry-run of migration
**HOL:** [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)
  
**Error description:** When you perform a Valet dry-run or migration, and your GitHub Personal Access Token is not correct or doesn't have the correct scope set, your get an error with code 401.

**Remediation:** Are you sure you have set the right scope when generating your Personal Access Token? It should have at least scope for `read:packages` and `workflow`. If you are unsure, it is best to generate a new Personal Access Token as you can't change the scope on an existing token. To create a new token, please follow [these steps](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md#generate-a-personal-access-token).

## Invalid Azure DevOps token when performing a Valet dry-run of migration
**HOL:** [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)
  
**Error description:** When you run a valet dry-run or migration and your Azure DevOps token is not valid, you see the following output which is not obvious there is an authentication issue: 
>  valet migrate azure-devops pipeline --target-url https://github.com/Microsoft-Bootcamp/validate-hol --pipeline-id 345
> [2021-09-28 06:47:11] Logs: 'log/valet-20210928-064711.log'                                                                                                         
> WARNING: `Faraday::Connection#basic_auth` is deprecated; it will be removed in version 2.0.                                                                         
> While initializing your connection, use `#request(:basic_auth, ...)` instead.
> See https://lostisland.github.io/faraday/middleware/authentication for more usage info.
> [2021-09-28 06:47:12] There was an error extracting the Azure DevOps pipeline.                                                                                      
> Message: (<unknown>): mapping values are not allowed in this context at line 2 column 10
> [2021-09-28 06:47:13] There was an error extracting the Azure DevOps pipeline.                                                                                      
> Message: (<unknown>): mapping values are not allowed in this context at line 2 column 10

**Remediation:** 

  
## _Error 404_ when running Valet migrate command
**HOL:** [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)

## _Error 422 - Invalid request, "sha" wasn't supplied_ when 
**HOL:** [Adding Custom Mappings for you migrations](https://github.com/Microsoft-Bootcamp/HOL/blob/main/Adding-Custom-Mappings-for-your-migrations.md)

**Error:** >PUT https://api.github.com/repos/Microsoft-Bootcamp/attendee-<yourGitHubhandle>/contents/.github/workflows/classic_ci.yml: 422 - Invalid request.
   
**Remediation:** To remediate this issue, delete or rename the original `.github/workflows/classic_ci.yml` file. 
  
## Artifact copy
**HOL:** []()
  
**Error description:**
  
**Remediation:** 
Remediation
