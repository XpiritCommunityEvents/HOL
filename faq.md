#Frequently Asked Questions and Common Errors
This document is a collection of frequently asked questions and common errors that can occur during the execution of the hands on labs, including information on how to solve them.
Feel free to contribute any of your additions: please make the change and create a pull request so we can adopt this in our next workshop.

## Auto-generated environment variables in the workflow have wrong casing
> HOL: [Creating a custom mapping to override the default behavior or non existing mappings](https://github.com/Microsoft-Bootcamp/HOL/blob/main/Adding-Custom-Mappings-for-your-migrations.md)
**Known issue logged with GitHub:** [https://github.com/github/valet/issues/3125](https://github.com/github/valet/issues/3125)
**Cause of issue:** 
> When you run a migration of a pipeline, it generates a set of environment variables. The generated environment variables are all in upper case, but the references to the variables is still Pascal casing as the original casing in the source pipeline. This will result in a failing workflow, since the workflow run on Linux is case sensitive.
**Remediation:** Manually edit the workflow file and ensure the environment variable uses capitals.  
1. Navigate to your workflow file (`.github/workflows/classic_ci.yml`) and edit the file.
2. Update `${{ env.BuildConfiguration }}` in lines 28, 31 and 34 to `${{ env.BUILDCONFIGURATION }}` and save the file.
3. Rerun the workflow and validate its run in the run history.

## CodeSpaces command line Bash
> HOL: []()

## Error code 401 
> HOL: []()
**Error description:**
**Remediation:**

# Error 404 when running Valet migrate command
> HOL: [Migrating pipelines from Azure DevOps to GitHub Actions using Valet](https://github.com/Microsoft-Bootcamp/HOL/blob/main/migration.md)


## Error code 422 - Invalid request
> HOL: []()
> PUT https://api.github.com/repos/Microsoft-Bootcamp/attendee-<yourGitHubhandle>/contents/.github/workflows/classic_ci.yml: 422 - Invalid request.
**Error description:**
**Remediation:**
  
## Artifact copy
> HOL: []()
**Error description:**
**Remediation:**
Remediation
