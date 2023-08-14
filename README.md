Creating an Azure App Service and Deploying a .NET Application
In this guide, we will walk through the steps to create an Azure App Service using Terraform, connect it to GitHub for deployment, and successfully deploy a sample .NET application.
Table of Contents
1.	Introduction
•	Overview of the goal and approach.
2.	Prerequisites
•	List of requirements before starting.
3.	Setting Up Azure Environment
•	Creating a Resource Group
•	Creating a Storage Account for Terraform State
4.	Terraform Configuration
•	Configuring main.tf for App Service Plan and App Service
•	Creating a Resource Group using resource_group.tf
•	Setting Up Backend Configuration in backend.tf
5.	Azure App Service Setup
•	Defining the Azure App Service Plan in Terraform
•	Creating an Azure App Service
6.	GitHub Deployment Setup
•	Overview of the deployment process
•	Configuring GitHub Repository for Deployment
•	Adding GitHub as a Deployment Source in Azure App Service
7.	Deployment and Verification
•	Creating a .NET Sample Application
•	Configuring Deployment Settings
•	Initiating Deployment in GitHub Actions
•	Verifying the Deployed Application
8.	Conclusion
•	Recap of the steps
•	Next steps and considerations



1. Introduction
This document outlines the process of creating an Azure App Service using Terraform, configuring it to deploy a sample .NET application from GitHub, and successfully verifying the deployment.
2. Prerequisites
Before you begin, make sure you have the following:
•	An active Azure subscription
•	Terraform installed on your local machine
•	GitHub account
•	.NET SDK installed (for creating the sample application)
3. Setting Up Azure Environment
Creating a Resource Group
•	Launch the Azure Portal (https://portal.azure.com/).
Set environment variables : 
1.	ARM_CLIENT_ID: Azure Active Directory Application Client ID
2.	ARM_CLIENT_SECRET: Azure Active Directory Application Client Secret
3.	ARM_SUBSCRIPTION_ID: Azure Subscription ID
4.	ARM_TENANT_ID: Azure Active Directory Tenant ID
•	•	Create an Azure service principal
•	To enable Terraform to provision resources into your Azure subscription, you should first create an Azure service principal (SP) in Azure Active Directory. This Azure SP grants your Terraform scripts to provision resources in your Azure subscription.

•	Create a new Resource Group named tfstate-rg.
•	Choose a suitable region (e.g., "US EAST") for the Resource Group.







Creating a Storage Account for Terraform State
•	Create a new Storage Account named tfstatestorageaccount within the tfstate-rg Resource Group.
•	Configure the storage account to use "Standard" tier and "LRS" replication.







 
























4. Terraform Configuration
Configuring main.tf for App Service Plan and App Service
•	In your Terraform configuration file (main.tf), define the resources for the App Service Plan and App Service.
•	Use the "Free" tier and size "F1" for the App Service Plan.
•	Specify the Resource Group name and other necessary details.
 
Creating a Resource Group using resource_group.tf
•	Create a file named resource_group.tf.
•	Define the resource group using the azurerm_resource_group resource.
•	Set the name and location of the resource group.
 
Setting Up Backend Configuration in backend.tf
•	Create a file named backend.tf.
•	Configure the Terraform backend to use the previously created storage account for storing the state.
•	Set the resource group name, storage account name, container name, and state file name.
 
5. Azure App Service Setup
Defining the Azure App Service Plan in Terraform
•	In your Terraform configuration (main.tf), define the Azure App Service Plan using azurerm_app_service_plan resource.
•	Use the previously created Resource Group and configure the "Free" tier and size "F1".
Creating an Azure App Service
•	Define the Azure App Service using the azurerm_app_service resource in your Terraform configuration.
•	Set the Resource Group, App Service Plan, and other necessary details.
 


6. GitHub Deployment Setup
Configuring GitHub Repository for Deployment
•	Log in to your GitHub account.
•	Create or select a repository for your .NET application.
•	Ensure that the application code is in the repository.
Adding GitHub as a Deployment Source in Azure App Service
•	Go to the Azure Portal.
•	Navigate to the created App Service.
•	Open the "Deployment Center" section.
•	Choose GitHub as the source and provide repository details.
•	Configure GitHub Actions for deployment.
 



7. Deployment and Verification
Creating a .NET Sample Application
•	Create a simple .NET application that prints "Welcome to 2023" on the screen.
•	Push the application code to your GitHub repository.
 
Configuring Deployment Settings
•	In the App Service's Deployment Center, configure build and runtime settings.
•	Choose "GitHub Actions" as the build provider and "dotnet7" as the runtime.
 
Initiating Deployment in GitHub Actions
•	Check your GitHub repository for the automatically created GitHub Actions workflow.
•	Trigger the workflow to initiate the deployment.
 
Verifying the Deployed Application
•	Once the deployment is successful, access the deployed application using the App Service URL.
•	Verify that the application displays "Welcome to 2023."
•	App url: https://welcome-app-service.azurewebsites.net/
•	 




8. Conclusion
In this guide, you successfully created an Azure App Service using Terraform, integrated it with GitHub for automated deployment, and verified the deployment of a sample .NET application. This demonstrates the power of Infrastructure as Code (IaC) and the seamless integration between Azure services and DevOps practices.
________________________________________


