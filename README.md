# Azure function local development and testing

## Overview

This project contains an Azure Function designed to [describe the primary purpose of the function, e.g., "process incoming HTTP requests and store data in Azure Storage"]. Azure Functions is a serverless compute service that enables you to run event-triggered code without having to explicitly provision or manage infrastructure.

## Features

- **Serverless Architecture**: Automatically scales based on demand.
- **Event-Driven**: Triggered by various events such as HTTP requests, timers, or messages from other Azure services.
- **Cost-Efficient**: Pay only for the time your code runs.

## Prerequisites

- **Azure Subscription**: Required to create and manage Azure resources.
- **Azure Functions Core Tools**: For local development and testing.
- **Visual Studio Code**: Recommended IDE for development.
- **.NET SDK**: Required for building and running the function locally.

## Configuration

- **local.settings.json**: Contains local configuration settings.
- **host.json**: Contains global configuration options that affect all functions in the project.
 
## Steps

### Create your local project

In this section, you use Visual Studio Code to create a local Azure Functions project in C#. Later in this exercise, you publish your function code to Azure.

1. In Visual Studio Code, press F1 to open the command palette and search for and run the command `Azure Functions: Create New Project...`.
2. Select the directory location for your project workspace and choose `Select`. You should either create a new folder or choose an empty folder for the project workspace. Don't choose a project folder that is already part of a workspace.
3. Provide the following information at the prompts:
   - **Select a language**: Choose C#.
   - **Select a .NET runtime**: Choose .NET 8.0 Isolated (LTS).
   - **Select a template for your project's first function**: Choose HTTP trigger.
   - **Provide a function name**: Type `HttpExample`.
   - **Provide a namespace**: Type `My.Function`.
   - **Authorization level**: Choose `Anonymous`, which enables anyone to call your function endpoint.
   - **Select how you would like to open your project**: Select `Open in current window`.

Visual Studio Code uses the provided information and generates an Azure Functions project with an HTTP trigger. You can view the local project files in the Explorer.

### Run the function locally

Visual Studio Code integrates with Azure Functions Core tools to let you run this project on your local development computer before you publish to Azure.

1. Make sure the terminal is open in Visual Studio Code. You can open the terminal by selecting `Terminal` and then `New Terminal` in the menu bar.
2. Press F5 to start the function app project in the debugger. Output from Core Tools is displayed in the Terminal panel. Your app starts in the Terminal panel. You can see the URL endpoint of your HTTP-triggered function running locally.
3. With Core Tools running, go to the `Azure: Functions` area. Under `Functions`, expand `Local Project > Functions`. Right-click the `HttpExample` function and choose `Execute Function Now...`.
4. In `Enter request body` type the request message body value of `{ "name": "Azure" }`. Press Enter to send this request message to your function. When the function executes locally and returns a response, a notification is raised in Visual Studio Code. Information about the function execution is shown in Terminal panel.
5. Press Shift + F5 to stop Core Tools and disconnect the debugger.
   
![vscode](https://github.com/user-attachments/assets/29dc3679-2fe4-4d28-ab46-4b01e06badf0)

### Sign in to Azure

Before you can publish your app, you must sign in to Azure. If you already signed in, go to the next section.

1. If you aren't already signed in, choose the Azure icon in the Activity bar, then in the `Azure: Functions` area, choose `Sign in to Azure...`.
2. When prompted in the browser, choose your Azure account and sign in using your Azure account credentials.
3. After successfully signing in, you can close the new browser window. The subscriptions that belong to your Azure account are displayed in the Side bar.

### Create resources in Azure

In this section, you create the Azure resources you need to deploy your local function app.

1. Choose the Azure icon in the Activity bar, then in the `Resources` area select the `Create resource...` button.
2. Provide the following information at the prompts:
   - **Select Create Function App in Azure...**
   - **Enter a globally unique name for the function app**: Type a name that is valid in a URL path. The name you type is validated to make sure that it's unique in Azure Functions.
   - **Select a runtime stack**: Use the same choice you made in the Create your local project section earlier in this exercise.
   - **Select a location for new resources**: For better performance, choose a region near you.
   - **Select subscription**: Choose the subscription to use. You won't see this if you only have one subscription.

  ![register_azure function](https://github.com/user-attachments/assets/a0e7ec6f-a3ef-4f7d-bc38-09e9bb788367)

The extension shows the status of individual resources as they're being created in Azure in the `AZURE: ACTIVITY LOG` area of the terminal window.

When completed, the following Azure resources are created in your subscription, using names based on your function app name:

- A resource group, which is a logical container for related resources.
- A standard Azure Storage account, which maintains state and other information about your projects.
- A consumption plan, which defines the underlying host for your serverless function app.
- A function app, which provides the environment for executing your function code. A function app lets you group functions as a logical unit for easier management, deployment, and sharing of resources within the same hosting plan.
- An Application Insights instance connected to the function app, which tracks usage of your serverless function.
  
![function_in_azure](https://github.com/user-attachments/assets/e29efc52-2c5a-4303-ad3e-9119e4a742ba)

## Run the function in Azure

1. Back in the `Resources` area in the side bar, expand your subscription, your new function app, and `Functions`. Right-click the `HttpExample` function and choose `Execute Function Now...`.
2. In `Enter request body` you see the request message body value of `{ "name": "Azure" }`. Press Enter to send this request message to your function.
3. When the function executes in Azure and returns a response, a notification is raised in Visual Studio Code.

![function_created_in_azure](https://github.com/user-attachments/assets/9e8956b9-a922-44c5-b261-55645dacc5dd)

4. Otherwise, you can trigger the Azure function from the Azure portal.
  
## Conclusion

In conclusion, you can efficiently create, test, run, and deploy an Azure Function using Visual Studio Code. This setup facilitates streamlined development and testing of serverless functions, harnessing the capabilities of Azure's cloud infrastructure.
