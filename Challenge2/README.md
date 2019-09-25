![Azure Sprint Series Logo](../Banner.jpg)

# Challenge 2: Create a Build Pipeline
With the code loaded, it's now time to make sure the code works! Your task is to validate the code builds correctly using Azure Pipelines. DevOps concepts covered: 
- Building
- Testing

This challenge is focused on building an Azure Pipeline that will compile your code, run unit tests and package up the code, ready for release.

Having the code working on your device is great for testing, but we need to deploy this solution so our users can also test it! 

Azure DevOps hosts build servers that can build your code and package it up ready for release. Having code built using these Build Servers allows code to be built in a consistent and repeatable fashion, ensuring only proper code goes into the build. 

Having the compiled code packaged up at this step also helps to enforce the  same code is being tested in a staging environment before it is deployed to production.


# Exercise 1
Create a YAML pipeline to build your code and produce artifacts for deployment. A build should have the associated Work Items and Commits attached. The build should only trigger on Pull Requests on the master branch.

## Hints
- Building all the services seperately using multiple YAML files may take longer but will provide you more flexability in the future and reduce the time spent waiting for a build to finish, you can leverage build filters to only rebuild code that has changed.

## Helpful resources
- [Build, test, and deploy .NET Core apps](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/dotnet-core?view=azure-devops])
- [Create your first pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline?view=azure-devops)

# Exercise 2
Set up automatic builds for the master branch, any time a pull request is made. Build pipelines can also be used to ensure code quality by testing aspects of your code whenever any changes are made. 

Create unit tests and run them on your build to ensure that code changes don't have unintended consequences in other areas of the code. 

## Hints
 - The web portal has an example of a front end unit test.
 - The cart controller has an example of a back end unit test.
 - Unit tests should be small and cover specific functions. Refer to the helpful resources to ensure that your unit test isn't testing too much at one time.
 - Investigate code coverage, it can indicate areas of the code that may need testing.

## Helpful resources
* [Unit Testing Best Practices](https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)
* [Unit Testing in .NET Core and .NET Standard](https://docs.microsoft.com/en-us/dotnet/core/testing/)

# Exercise 3
You may have noticed that the portal has a contracts folder that references the contracts. This project is useful to ensure that the consuming service can communicate using the same objects.

This pattern only works for consumers within the repository and complicates the build by requiring build triggers outside when you are setting up automated builds. 

We can package up these contracts in the build process of the other projects and decouple the backend by publishing them as a nuget package and storing them within Azure Artifacts.

Extend the build pipeline to publish contracts as Azure Artifacts and configure the front end web portal to use these new contracts.

## Hints    
- You can also leverage Azure Artifacts to run specific business code that may be useful in more than one project.
- Using a versioning system such as semantic versioning can help consumers understand what changes have taken place and the level of testing required when updating packages.


## Helpful resources
- [Azure Artifacts Documentation](https://docs.microsoft.com/en-us/azure/devops/artifacts/index?view=azure-devops)
- [Azure Artifacts Nuget Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/artifacts/nuget?toc=%2Fazure%2Fdevops%2Fartifacts%2Ftoc.json&view=azure-devops&tabs=yaml)
- [Creating a NuGet package using Visual Studio](https://docs.microsoft.com/en-us/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

# Exercise 4
Now that we have a number of processes building, testing, publishing and releasing, we want to be notified of potential issues. Make sure that Build  email notifications are enabled. These may also be enabled by default, check your inbox to make sure: [mail.office365.com](https://mail.office365.com).

One of the downfalls of email notifications is that it is hard for the rest of the team to see actions taking place as a result of the notification. Azure DevOps also supports connecting to Microsoft Teams. Implement to ChatOps, by creating a channel in Microsoft Teams and connecting it to Azure DevOps. Make sure you are receing notifications in the team for Pull Requests, and Build Failures.

## Hints
- This task can require elevated permissions that may not be set on your account, let your coach know if you run into issues.

## Helpful resources
- [Azure DevOps integration with Microsoft Teams](https://docs.microsoft.com/en-us/azure/devops/service-hooks/services/teams?view=azure-devops)
- [Azure Pipelines integration with Microsoft Teams](https://docs.microsoft.com/en-us/azure/devops/pipelines/integrations/microsoft-teams?view=azure-devops)