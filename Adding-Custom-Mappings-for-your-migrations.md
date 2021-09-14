# Creating a custom mapping to override the default behavior or non existing mappings
In this lab you will create a custom plugin that transforms some of the exising migration mapping and replace it by your own mapping. 
For this you need to start coding in Ruby.

## Creating a mapping
To create a mapping, you need to create a Ruby file that looks as follows:
``` ruby
transform "azuredevopstaskname" do |item|
   # your ruby code here that produces output
  end
```  
If we look at the transformation that was generated for our CI pipeline, we have seen the transformation does not take into account the fact we specified a wildcard pattern to match any of the csproj files we might have in our repo. This now results in a workflow that fails the build if we accept the default mapping.

Let's see if we can fix this by providing an alternative.

We start by changing the function name to match the Azure DevOps task name `DotNetCoreCLI@2`.
The way you find this name is by clicking the view yaml button at a task in the pipeline:
![view yaml](images/view-yaml-task.png)

This results int he following code:
``` ruby
transform "DotNetCoreCLI@2" do |item|
   # your ruby code here that produces output
  end
```  
The parameter item is a collection of items than contain the properties of the original task that was retrieved from Azure DevOps.
In our case we can see in the yaml the properties that are set are e.g. `command` and `projects`.

This is what you can expect to find when we would dump the information. The way you can figure out what is in the item being passed you can do the following:
``` ruby
transform "DotNetCoreCLI@2" do |item|
   puts item
  end
```  
and then run a Valet commandline where we pass in the custom mapping like this:
