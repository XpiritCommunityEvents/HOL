# 2. Setting up Codespaces to develop a web-app

You just migrated a repository that contains a web application. With codespaces you can configure a full development environment as part of your code repository. 

For more information on Codespaces, visit: [https://github.com/features/codespaces](https://github.com/features/codespaces)

## Objectives
This hands-on lab introduces you to the concept of Codespaces, working with Codespaces and prepares your Codespaces environment for the subsequent hands-on labs. where you will further experience the benefits of working with CodeSpaces.


## Setting up your CodeSpaces development environment
Please go to your repository and start your Codespace instance by clicking the button `Code`, then the tab `Codespaces` and select `New Codespace`.

![starting codespaces](../images/codespaces.png)

The first time you create a Codespace You will see the following screen.

![creating codespace container](../images/settingup-codespaces.png)
Please wait for this to complete. The reason it takes some more time the first time has to do with the fact the container needs to be build for the first time. Next time you start a Codespace you will get access in a few seconds.

When your Codespace is ready you will see the full IDE appear in your browser. This is a full Visual Studio Code experience in your browser! This looks as follows:
![code space ide](../images/codespace-ide.png)


Once you are in your Code Space, you can follow the next steps to add an extension to your Code Space.



## Adjusting codespaces for your team and your type of work.

You will now make changes to the codespaces environment so you are able to do software development as a web developer using .NET and C#.

We will make use of the `auto detect` features of visual studio code by browsing to one of the c# files that makes up the web solution in your repository.

In the file explorer browse to the file `startup.cs` whch van be found in the folder `TailwindTraders.Website\Source\Tailwind.Traders.Web`. The moment you open the file `startup.cs` you will see a pop-up apear in the bottom right corner of your ide.

![install C# plugin](../images/codespaces-new-installcsharp.PNG)

Click on the install button so the plugin gets installed in this instance of codespaces.

While the plugin gets installed, we would like the installation not only to be in this instance but also for all your team mates. For this you click the gear icon in the extentions window and select the option `add to devcontainer.json`

![Code Spaces - Add to devcontainer.json](../images/codespaces-new-add-to-devcontainer-and-add-missing-assets.PNG)

In the meanwhile you also should see some messages poping up from the plugin that it is missing assets. Click on the yet button to add them to the project.

>Note: You'll get a pop-up stating "*We've noticed a change to the devcontainer configuration. Rebuild the container to apply them now*". We will wait with this, so dismiss this dialog. 

## Check if we can debug our webapplication
The new plugin added the option to debug .NET applications. In the left of your screen you will see the button with the `play` icon on there and a little symbol of a bug. Click this button and it will open the debug tools. In the top of the window you can now select which application you would like to debug. Select the application `.NET Core Launch (web)` 
![debugger window](../images/codespaces-new-debug-web.PNG)

The moment you click the small play button in the top, the debugger will start. In your console in the bottom, you will see the compilation process. 
>Note: The actual compilation is now done in the devcontainer running in the cloud. The output you see is streamed from that container and the commands for debugging are send to this container

Next you will see a popup in the right bottom corner and if you have a pop-up blocker enabled a message a popup is blocked. This is because the debugger tries to start a new window that shows the website you are debugging. You either need to enable the pop-up or click on the message in the bottom `Open in Browser` on the forwarded port.

![port forwaring](../images/codespaces-new-portforward-popup.PNG)

In the new opened tab you should now see the tailwindtraiders website.

![Tailwindtraders website](../images/tailwindtraders-website.PNG)

## Make a code change
In your ide find the file `translation.json` which can be fond in the folder `TailwindTraders.Website\Source\Tailwind.Traders.Web\ClientApp\src\assets`
In this file you will find the value for the free shipping promotion. We are going to change this from $300 to $100 as part of a holiday promotion.
After you have made a change to the file, go back to the tab with the website and see it chenged there also immediately.

## Commit the changes to the devcontainer
We now know the plugin works great and we want to share this with our team. For this we need to commit some changes that were made during the excersise. Firs we want to commit the change to the website. For this you goto the git toolwindow that can be fond by the git symbol in the left of yoru screen with a notification on there stating the number 3.
This means we have 3 changes that we can commit.
You now first stage the change to the `translation.json` file. And you commit this change to the local repo.

Next you stage the `devcontainer.json` and the `launch.json` file as a seperate commit.

Now that your chanegs have been saved, you can rebuild te container and validate it works as expected with a new fresh instance.

## Rebuild the devcontainer
Open the Command Palette. Use either  (ctrl-shift-p/cmd-shift-p) or or use the cog icon in the left bottom corner and open the command palette over there.

![command palette](../images/codespaces-new-command-palette.PNG)

Now type "*Rebuild Codespace*". [More information can be found here](https://docs.github.com/en/codespaces/customizing-your-codespace/configuring-codespaces-for-your-project#applying-changes-to-your-configuration).


Great job! :thumbsup: You've now added an extension to the Code Spaces container in a way that will ensure this extension is always available when you open your Code Space. So, next time you open your Code Space - this extension will be available without any manual intervention.
