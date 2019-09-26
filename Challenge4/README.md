![Azure Sprint Series Logo](../Banner.jpg)

# Challenge 4: Monitoring your solution
TAA has received some feedback and would like to increase the reliability of the web portal. In order to do this they have asked you to find a solution to reduce the time that outages take to resolve. Proper tooling and instrumentation is key to timely resolutions and enables the ability to monitor releases and roll back automatically if problems are detected.

In this challenge you will be tasked to implement Application Insights, set up Azure Monitor and integrate both with Azure DevOps.

# Exercise 1
The first step is to create an Application Insights resource in the Azure Portal and then install the approprate SDK's into into each of the five services.

## Hints
- The sample code includes a environment variable `SimulatedFailureChance` that can be set in each service to simulate errors. You can use this to see application insights in action without changing the code!
- Application Insights has extensions for Visual Studio that can make it easier to view alerts inline with your code, however most of the functionality is exposed in the portal and be used without the dependency on Visual Studio.

## Helpful resources
- [Start monitoring your ASP.NET Core Application](https://docs.microsoft.com/en-us/azure/azure-monitor/learn/dotnetcore-quick-start)


# Exercise 2
It is important to know if your users can access your services. Application Insights provides availability tests out of box to test that your application is up and responding to requests. 

Set up Application Insights to alert when any service has an availability issue. Now turn off a service and view the error that is created within Application Insights. Use the Application Insights interface to create a bug in your teams Kanban board in Azure DevOps for that availablity issue.

## Hints
- You can use URL Ping Tests for most of the services, however the Web Portal is a good candidate to use Custom Track Availability Tests.

## Helpful resources
- [Monitor Web App Availablity](https://docs.microsoft.com/en-us/azure/azure-monitor/app/monitor-web-app-availability)
- [Manually create a work item using Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/diagnostic-search#create-work-item)


# Exercise 3
Application Insights makes it easy to quickly turn errors into work items within Azure DevOps. However it can be important that critical errors are immediately surfaced to the team rather than requiring a human to review the error first. Using Azure Monitor we can configure rules to alert users to issues within your environment. Set up two alerts that integrate with two different systems, some examples are below.

- Creating an email when errors occur across a threshold for five minutes.
- Creating work items when errors occur in a specific service.
- Create a message in teams when a certain number of errors are raised.

## Hints
- Azure Monitor can be used to monitor multiple resources within Azure and not just Application Insights, have a look to see what other metrics are available for other resources you have deployed.

## Helpful resources
- [Create Azure Monitor Alerts with Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/learn/tutorial-alert)
- [Record runtime exceptions with Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/learn/tutorial-runtime-exceptions)


# Exercise 4
Now we have the metrics flowing into Azure Monitor we can integrate with Azure DevOps to ensure that a new deployment did not cause an increase in failed traffic. Set up Azure DevOps and Azure Monitor to fail a release and switch slots back to the previous state if errors occur.

## Hints
- You can further extend this task by splitting the traffic by a specific percentage across both slots at the same time before switching all users across.
- Be careful about monitoring too small a timeframe especially if you recieve errors that spike and trail off later due to transient issues caused by the deployment process. It may help to create a custom metric to compare the failures per request across both slots.
- You can test a failure by turning off a service and using the application, or setting the `SimulatedFailureChance` variable for slot specific variables.

## Helpful resources
- [7 best practices for continuous monitoring with Azure Monitor](https://azure.microsoft.com/sv-se/blog/7-best-practices-for-continuous-monitoring-with-azure-monitor/)
- [Azure Pipeline Conditions](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/conditions?view=azure-devops&tabs=yaml)
- [Routing traffic using App Service Slots](https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots#route-traffic)
- [Martin Fowler on Blue Green Deployments](https://martinfowler.com/bliki/BlueGreenDeployment.html)
