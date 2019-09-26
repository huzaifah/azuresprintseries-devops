![Azure Sprint Series Logo](../Banner.jpg)

# Challenge 5: Building and shipping Containers
There are many different ways of deploying code, TAA request and investigation to see if containers can make their solution more portable and easier to manage.
- Releasing
- Deploying
- Monitoring

This challenge introduces containers - which enable easily reproducible environments, perfect for deploying microservices. Azure DevOps has extensive support for building and releasing containers.

# Exercise 1
Run each service inside containers on your development machine.

## Hints
- Refer to the helpful resources for example DockerFiles
- Pass settings using environment variables

## Helpful resources
* [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
* [Dockerize an ASP.NET Core Application](https://docs.docker.com/engine/examples/dotnetcore/)

# Exercise 2
Now that the containers are running successfully locally, update the Azure DevOps Build Pipeline to build the source code into containers and push to an Azure Container Registry (ACR).

## Hints
- Ensure you tag your containers when you release them to ACR.
- Create an Azure Container Registry.

## Helpful resources
* [Azure Container Registry Documentation](https://docs.microsoft.com/en-us/azure/container-registry/)
* [Build and Push to Azure Container Registry](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/containers/acr-template?view=azure-devops&tabs=dotnet-core)
* [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/)

# Exercise 3
Update the Release Pipelines to deploy the Containers for running in Azure Web App for Containers both in test and production.

## Hints
* You can manually deploy the Web App for Containers resources manually and use Azure DevOps to push the containers. Bonus points if you update your ARM template first.


## Helpful resources
* [Deploy to Azure using Docker](https://docs.microsoft.com/en-us/azure/app-service/containers/quickstart-docker)


# Exercise 4
Setting up an entire environment can be challenging. Docker Compose enables developers to design multi-container applications easily while ensuring that the application can be tested easily.

Make a Docker Compose file that starts all the services and runs them locally. 

## Hints
- Pass settings using environment variables from the host to reduce the amount of container changes.
- You may need to trust new self-signed SSL certificates.

## Helpful resources
* [Docker Compose](https://docs.docker.com/compose/)

# Exercise 5
Create a multi-container Web App using Docker Compose, then deploy with  Azure DevOps.

## Hints
- Pass settings using environment variables from the host to reduce the amount of container changes.
- Deploy the Identity Service separately.


## Helpful resources
* [CI/CD for Containers Architecture](https://azure.microsoft.com/en-us/solutions/architecture/cicd-for-containers/) 
* [Create a multi-container app](https://docs.microsoft.com/en-us/azure/app-service/containers/quickstart-multi-container)
* [Docker Compose](https://docs.docker.com/compose/)