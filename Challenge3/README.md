![Azure Sprint Series Logo](../Banner.jpg)

# Challenge 3: Building a deployment pipeline
The customer is happy with the state of the project and would you to establish Test and Prod environments. This challenge leverages Azure Pipelines to create a release and then deploy the compiled assets. DevOps concepts covered:
- Releasing
- Deploying

Following on from the previous challenge the code has been built and artifacts are ready to be released. Release and deployment is done through the Azure Pipelines section of Azure DevOps.

# Exercise 1
Log into Azure [portal.azure.com](https://portal.azure.com) and provision your test environment. Ensure that when code is pushed into your release branch, code automatically is deployed into the test environment.

## Hints
- Two Resource Groups have already been created for you to use, they represent your Testing and Production environments.
- We recommend sharing a single App Service Plan between all the components in each environment. **Use S1 as the resource tier for the App Service Plan.**
- Make sure you pay close attention to the region where you are deploying the resources.
- You will need to set up a service connection in Azure DevOps.
- Ensure that the two environments are completely seperate, having production services accidentally accessing test data can lead to some pretty dire consequences!

## Helpful resources
- [Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/overview)
- [Configure Service Connections](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml)

# Exercise 2
Now is time to deploy the code. Create a release pipeline and ensure that when code matches certain conditions a release is automatically created and deployed into your test environment. 

## Hints
- You do not need to release into your production environment at this stage
- Certain settings will need to be set in order to run the application. You can find these in the appsettings.development.json file
- It is helpful to have one release definition per product to ensure all your services are at the versions you expect. (you can have multiple build artifacts per a solution)

## Helpful resources
- [Deploy an Azure Web App](https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/webapp?view=azure-devops&tabs=yaml)

# Exercise 3
The next step is to ensure that when the code is released, it passes certain functional tests. Create a new front end functional test and apply it against your new test environment automatically after the release has deployed. Finally put in a manual intervention step to ensure manual tests are followed

## Hints
- The front end interface has an example UI test for you to base your work off. It may be easier to get this working in the build pipeline first before you create a new functional test. You also can split this work within your team and test locally on a seperate branch.
- Manual Intervention steps can include test instructions. Testers can also refer back to related work in this release and if you have attached specific test tasks, they can check them off the board.

## Helpful resources
- [UI Tests with Selenium](https://docs.microsoft.com/en-us/azure/devops/pipelines/test/continuous-test-selenium?view=azure-devops)

# Exercise 4
Depending on how you implemented your pipeline you may have chosen to insert application settings manually through the Azure Portal, if this is the case investigate how you would set application settings if you did not have permissions to the Azure Portal. If you have used Azure DevOps to deploy your application settings using release variables and not through the Azure Portal, ensure you know where these variables end up in the Azure Portal.

When applications are leveraging external services (such as Databases, external APIs etc), often these services are secured with security keys or credentials. Azure has a service for this called Azure KeyVault. 

In this exercise, we will store the secrets in KeyVault and then update the pipeline to leverage the KeyVault for secure deployments.

This pattern is especially useful when production keys are managed externally from the development team.

## Hints
- There are a few methods of integrating Azure KeyVault. Experiment with each method and see what works best for your use case.

## Helpful resources
- [Link secrets from Azure KeyVault as variables in a pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/variable-groups?view=azure-devops&tabs=yaml#link-secrets-from-an-azure-key-vault)
- [Using a custom task to include secret variables in a pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/azure-key-vault)
- [Embedding Keyvault dependencies in the application](https://docs.microsoft.com/en-us/azure/key-vault/vs-secure-secret-appsettings)
- [Keyvault References](https://docs.microsoft.com/en-us/azure/app-service/app-service-key-vault-references)

# Exercise 5
Doing all manual steps to set up a new environment can be tedious, require a lot of documentation and introduce an element of risk via human error. By using resource manager templates you can define your Azure Infrastructure as code and ensure repeatable deployments without having to manually create any resources.

Using your test resource group as a guide create a resource manager template and deploy it alongside your code into production.

## Hints
- Use Azure DevOps variables to set any environment specific variables (such as resource group name)

## Helpful resources
- [Integrate resource manager templates with Azure Pipelines](https://docs.microsoft.com/en-us/azure/azure-resource-manager/vs-resource-groups-project-devops-pipelines)

# Exercise 6
It is important to have a rollback plan if something goes wrong with a deployment. This can be as easy as redeploying a previous release, but some deployment targets allow simpler rollbacks by leveraging built in methods for rolling back with minimal downtime.

Azure App Services allow you to deploy to specific deployment slots that run on the same infrastructure and allow instantaneous switching between and old code. Use Azure pipelines to deploy to a staging slot in your production environment and then make the slot live. After the changes are live - immediately test the website again and switch the slot back if the website does not respond with a "200" status.

## Hints
- Slots can be automatically swapped by configuring "auto swap"
- Slots can be configure to divert a percentage of traffic to allow monitoring while only effecting a small portion of your userbase

## Helpful resources
- [Set up staging slots](https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots)
