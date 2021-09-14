# Migrating pipelines from Azure DevOps to Github Actions using Valet 
In this hands-on lab you will get a first glance at the tooling that is build to migrate CI/CD solutions to GitHub actions. This tool is called **Valet**

We will start with setting up the tools, use the tools for a dry-run and do a migration of one pipleline to Azure Devops to get a feel on how the tools work.

All the hands-on labs will use the CodeSapces capabillity of GitHub. During the import of the git repository, we more or leass sneaked in the configuration for the codespaces setup. This is done because we included a folder called .devcontainer. This contains the setup of our development environment for this hands-on exersise.
So before we continue the hands-on lab, goto your repository and start your codespace instance by clicking the button "create new codespace"

![starting codespaces](images/codespaces.png)

The first time you create a codespace You will see the following screen.

![creating codespace container](images/settingup-codespaces.png)
Please wait for this to complete. The reason it takes some more time the first time has to do with the fact the container needs to be build for the first time. Next time you start a codespace you will get access in a few seconds.

When your codespace is ready you will see the full IDE apear in your browser. This is a full visual studio code exeprience in your browser! this looks as follwos:
![code space ide](images/codespace-ide.png)codespace-ide

The place we will all our work for this hands-on lab is in the terminal window that you can find in the richt bottom part. it should show you a command-line and it is currently in the folder /workspaces/<your-repo-name> (main)
  
> note all command-line steps assume the above environment to work. So please ensure this is the case before you start.

## Adding Valet to your development environment.

Valet uses a docker container to do all the work. This container is available the moment you are onboarded to valet.
Valet consist primaraly out of two thigns we need to setup before we can do some work:
- a docker image that we need on our machine
- a script called valet, that drives the use of the docker container on our workstation.

Let us get started by settign up the tools so they work.

### Pulling the docker image for valet

In the terminal window in your codespace environment (or in visual studio code if you prefer to use that)
type at the command-line:
> docker images
This should return an empty list of images
```
codespace ➜ /workspaces/<your repo name> (main) $ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
  ```

now pull the docker image for valet:
> $ docker login ghcr.io/valet-customers/valet-cli

>Username: **yourdockerhandle**

>Password: **your github personal access token here**

expected output:
```
Username: <yourgithubhandle>
Password: *******
WARNING! Your password will be stored unencrypted in /home/codespace/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store
  ```

Next we pull the image to the local codespace 

>$ docker pull ghcr.io/valet-customers/valet-cli

expected output:
```
Using default tag: latest
latest: Pulling from valet-customers/valet-cli
540db60ca938: Pull complete 
98a867505730: Pull complete 
69c77620f610: Pull complete 
9b370d66bb99: Pull complete 
d9f4ad4e4f54: Pull complete 
141b99f6eb7e: Pull complete 
c30228028dd8: Pull complete 
89a422fd482f: Pull complete 
Digest: sha256:a16b34607e98311fd6568700ed774382f63d213b36d7cbd82ec060a5e998a86a
Status: Downloaded newer image for ghcr.io/valet-customers/valet-cli:latest
ghcr.io/valet-customers/valet-cli:latest
```

Now we want to try to create some migrations of the Azure DevOps project that you can find in the Xpirit Repository (dev.azure.com/xpirit). 
The Team project name we can use for this excersise is **TailWindTraders**

> note: please feel free to use your own azure devops projects, the lab is more step by step prepared, feel free to go of script!

Now goto the folder **valet** on your local repo in your codespaces IDE.
In this folder you find the valet scripts. We already put them on the development environment, this is a step you ave to take when you do this in the future on your own development environment. You can find this script in the valet/customer repo that you should have access to.
  
Try to run this script. 

if it fails with a security message, it is possible the file is not executable. For this run the command:
> chmod +x valet
This should mark it as executable on your local dev container.

Now run the command valet again.

It should now output the valet commands that are available:

```
Valet commands:
  valet audit                               # An audit will output a list of data used in a CI/CD instance.
  valet dry-run                             # Convert a pipeline to a GitHub Actions workflow and output it's yaml file.
  valet help [COMMAND]                      # Describe available commands or one specific command
  valet migrate                             # Convert a pipeline to a GitHub Actions workflow and open a pull request with the changes.
  valet upload-audit --audit-dir=AUDIT_DIR  # Upload the output of an audit for the Valet product team.
  valet version                             # valet version

Options:
      [--allowed-actions=one two three]                                      # An allowed list of GitHub actions to map to.
      [--allow-verified-actions], [--no-allow-verified-actions]              # Boolean value to only allow verified actions.
      [--allow-github-created-actions], [--no-allow-github-created-actions]  # Boolean value allowing only GitHub created actions.
      [--yaml-verbosity=YAML_VERBOSITY]                                      # YAML verbosity level.
                                                                             # Possible values: quiet, minimal, info
      [--custom-transformers=one two three]                                  # Paths to custom transformers.
  o, [--output-dir=OUTPUT_DIR]                                               # The location for any output files.
      [--credentials-file=CREDENTIALS_FILE]                                  # The file containing the credentials to use.
      [--no-telemetry], [--no-no-telemetry]                                  # Boolean value to disallow telemetry.
```
## Run an audit on the existing Azure DevOps project
to run valet commands we need to pass in the arguments at each command or we can set up a file called .env.local. We provided this file already in the valet folder. It is most convinient to use this file and only fill in the missing details for Azure DevOps and for GitHub. 
Add the following parameters to the file:
```
AZURE_DEVOPS_ACCESS_TOKEN=<token will be provided>
AZURE_DEVOPS_PROJECT=TailWindTraders
AZURE_DEVOPS_ORGANIZATION=xpirit
AZURE_DEVOPS_INSTANCE_URL=https://dev.azure.com/xpirit
```

now run the following command:
> $ valet audit azure-devops --output-dir . 

This will run the tool with the options you specified in the .env.local file.

The output of this audit run will result in a set of files that got generated to become the future action workflows and a summary page that contains the autput of the audit. 
Here you can see how the migration will happen and how successfull it will be. Note not everythign will be migrated and manual fixes are needed to succeed
  
# Execute the migration
valet migrate azure-devops pipeline --target-url https://github.com/Microsoft-Bootcamp/<your-repo-name> --pipeline-id ###number from azdo pipeline###

Now inspect the action workflow and try to run it and see if it works out of the box.
  
