![Azure Sprint Series Logo](../Banner.jpg)

# Challenge 1: Introduction to Azure DevOps

TAA has just handed over access to the existing codebase to you. Your challenge is to collaborate with your team to plan out the project tasks and load the code into the TAA Azure DevOps instance. DevOps concepts covered:

- Planning
- Coding

# Exercise 1

Introduce yourself to the rest of the team and your team coach. Choose an animal to act as your team's mascot, sign up and join the teams channel & introduce yourself on the shared chat.

## Hints
 - Details on how you can connect to teams using the lab accounts can be found on your desk.
 - Your team coach is there to guide you and answer any Azure DevOps questions you have - call on them if you get stuck!
 - You can attach media to posts in Teams. Add a photo (such as your team's animal) in your introduction message. Bonus points if you use a gif. 

## Helpful resources

- [Microsoft Teams Documentation](https://docs.microsoft.com/en-us/microsoftteams/microsoft-teams)
- [List of Domesticated Animals](https://en.wikipedia.org/wiki/List_of_domesticated_animals)

# Exercise 2 

Sign into Azure DevOps using the credentials provided to you. Customise your teams project and familarise yourself with the environment. Next, import the repository below into Azure Repos and clone this git repo locally on your development machine.

[Animal Adoption Portal](https://github.com/awaregroup/animal-adoption-portal)

The repository contains TAA's existing codebase you will be extending - note that this code has been built specifically for these labs and should not be adapted for production workloads.

A micro-service architecture has been used by the previous vendor to design the solution. The included services are:

- **Front End Portal**
    - Serves up the front end web portal and provides a gateway to the backend services.
- **Image Service**
    - Serves up images of specific animals
- **Cart Service**
    - Handles holding the current animals the user is interested in adopting
- **Identity Service**
    - Authenticates users based on what animals they click on
- **Animal Information Service**
    - Provides information about animals that are available for adoption

After you have the code locally on your machines, follow the README to run the website on your machine.


## Hints
 - Now is a good time to select one or two team members to look after each service, this will help you to divide and conquer each of the exercises.
 - There are multiple ways to import a repository - feel free to experiment!
 - If in doubt on how to run each service, refer to each service's README.
 - Remember to use the online documentation and the helpful resources provided to find methods to complete each challenge.
 - If you get stuck, talk to your coach!



## Helpful resources
- [Azure Repos Documentation](https://docs.microsoft.com/en-us/azure/devops/repos)
- [Git Quickstart](https://docs.microsoft.com/en-us/azure/devops/user-guide/code-with-git?view=azure-devops)


# Exercise 3
Planning is in important part of the DevOps lifecycle. Azure DevOps allows you to collaborate and plan together using Azure Boards.

As the next exercise will use Git with Azure Repos, now is a good time to set up the method of branching and peer review your team will be using to collaborate together. Azure DevOps has many policies that can be set up to ensure code review and the branching strategy you select is enforced.

Work with your team to plan how you will change the code you cloned in the previous exercise to remove the following placeholders. Demonstrate to your team coach how you will split the work using Azure Boards, it is recommended you split the work up in such a way that each member of your team can contribute.

- **Front End Portal**
    - Change text that mentions placeholder animal
- **Image Service**
    - Change the images to serve up your teams animal
- **Identity Service**
    - Change the placeholder image to a picture of your teams animal 
    - Change the placeholder name that is returned to the front end in the hello text
- **Animal Information Service**
    - Change the information to have details about your animal


*You do not need to change the code in this step.*


## Hints
- There is no one-size-fits-all branching strategy, choose one that balances out the complexity with your requirements and team size.
- Similarly there is no correct way to plan for work. As different methods of planning usually trade off between visiblity of work, accuracy of time quoted and time spent in the planning phase, it is important to choose a planning method that works for your team.
- Refer to the links below for guidance and introduction to various branching strategies.
- It may be useful to search through the code for "Placeholder" to ensure you have planned out the entire scope of work.


## Helpful resources
- [Adopt a Git Branching Strategy](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance)
- [How Microsoft uses Git](https://docs.microsoft.com/en-us/azure/devops/learn/devops-at-microsoft/use-git-microsoft)
- [Git Tags](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-tags)


# Exercise 4

Following your teams plan in the previous example, implement the changes to change the placeholders in the sample code using your branching & peer review strategy and show your coach the final product!

## Hints
- If this is the first time you are using git, check out the helpful resources first.
- Using your branching strategy and Git within Azure Repos, every member in your team should be able to focus on a seperate area of code simultaneously.
- This exercise is not a test of your development skills, if you do not know JavaScript or C# ask your coach to help out!


## Helpful resources
- [How to code with Git](https://docs.microsoft.com/en-us/azure/devops/user-guide/code-with-git)
- [Git Cheatsheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet/)