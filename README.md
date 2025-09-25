Welcome to SonarQube workshop. In this exercise we will look at core SonarQube features.

<details>
  <summary>Task 0. Initial setup</summary>
Use this repository template to create a new repository. If the Action gods were merciful today, the automation has already invited you to SonarQube Workshop organisation, created a repository from the template and used your GutHub username for repository name.

If you haven't done so yet, please log into SonarQube Cloud from https://sonarcloud.io/login. Please make sure to use GitHub for authentication. 

![GitHub Login](workshop_images/github_login.jpg)

While it's possible to log in with other DevOps platforms, we will be using GitHub in this exercise. Your SonarQube Cloud account will be created if this is the first time you are logging into the platform. Once your account is created, the admin will add you to the SonarQube Workshop organisation.
</details>

<details>
  <summary>Task 1. Create a SonarQube Cloud project from a GitHub Repository</summary>

To create a new project in SonarQube Cloud from your GitHub repository, follow these steps:
  1. Log in to [SonarQube Cloud](https://sonarcloud.io/login) using your GitHub account.
  2. Click on **"+ Analyze new project"** 
  ![Create project](workshop_images/create_project.jpg)
  
  3. Make sure to select **SonarQube Workshop** in organisation list. In the list of repositories, find and select the repository that was created for you. Make sure the repository name includes your GitHub username (e.g., `sq-workshop-yourusername`). Click on **Set Up** button.
  ![Select the repository](workshop_images/select_reporitory.jpg)
  
  4. In the **Set up project for Clean as You Code** screen, select **Number of days** and accept the default 30 days period. Click on **Create project** button.
  ![New code](workshop_images/clean_as_you_code.jpg)
  
  5. SonarQube will start the analysis of the project which will take a few minutes
  ![Initial analysis](workshop_images/initial_analysis.jpg)
  
  6. When the initial analysis is completed, you should be able to see all issues found by SonarQube (make sure to select `Main branch` on the left):
  ![Initial analysis result](workshop_images/initial_analysis_result.jpg)
  </details>

<details>
  <summary>Task 2. Review the results</summary>
  Go to `Issues` tab. Here you can see all the issues that were detected in your code. Feel free to filter by various parameters. 

  Go to `Security Hotspots` tab. A security hotspot highlights a security-sensitive piece of code that the developer needs to review. SonarQube Cloud helps you find security hotspots in your code when running analyses. You can read more about Security Hotspots on https://docs.sonarsource.com/sonarqube-cloud/digging-deeper/security-hotspots
  
  Go to `Inventory` -> `Dependencies`. This is where Sonar reports on what [third party libraries](https://docs.sonarsource.com/sonarqube-cloud/advanced-security/viewing-dependencies) were imported into your application. But wait.... why there are 0 dependnencies? If you look at `package.json` file in your repositories - there are definitely a few packages that were declared! 

  The reason for this is how the scanning is configured. With GitHub it is possible to have your code [scanned automatically](https://docs.sonarsource.com/sonarqube-cloud/advanced-setup/automatic-analysis). In order to scan for vulnerable packages we need to implement scanning in our pipelines.
</details>

<details>
  <summary>Task 3. Setup Sonar scanning in GitHub Actions</summary>
  Go to `Administration` -> `Analisys Method`. As you can see, the automated analysis is enabled by default. We will need to turn that off and set up the analysis with GitHub Actions.
  
</details>
