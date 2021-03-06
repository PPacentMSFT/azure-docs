---
title: Create your first function in Azure using Visual Studio | Microsoft Docs
description: Create and publish a simple HTTP triggered function to Azure by using Azure Functions Tools for Visual Studio. 
services: functions
documentationcenter: na
author: ggailey777
manager: cfowler
editor: ''
tags: ''
keywords: azure functions, functions, event processing, compute, serverless architecture

ms.assetid: 82db1177-2295-4e39-bd42-763f6082e796
ms.service: functions
ms.devlang: multiple
ms.topic: quickstart
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 03/13/2018
ms.author: glenga
ms.custom: mvc, devcenter

---
# Create your first function using Visual Studio

Azure Functions lets you execute your code in a [serverless](https://azure.microsoft.com/overview/serverless-computing/) environment without having to first create a VM or publish a web application.

In this article, you learn how to use the Visual Studio 2017 tools for Azure Functions to locally create and test a "hello world" function. You then publish the function code to Azure. These tools are available as part of the Azure development workload in Visual Studio 2017.

![Azure Functions code in a Visual Studio project](./media/functions-create-your-first-function-visual-studio/functions-vstools-intro.png)

This topic includes [a video](#watch-the-video) that demonstrates the same basic steps.

## Prerequisites

To complete this tutorial:

* Install [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/) or a later version, including the **Azure development** workload.

    ![Install Visual Studio 2017 with the Azure development workload](./media/functions-create-your-first-function-visual-studio/functions-vs-workloads.png)

    If you have already installed Visual Studio, make sure you have installed any pending updates. 

* If you installed the Azure development workload with Visual Studio 2017 version 15.4 or earlier, you may also need to [update your Azure Functions tools](functions-develop-vs.md#check-your-tools-version). 
    
[!INCLUDE [quickstarts-free-trial-note](../../includes/quickstarts-free-trial-note.md)] 

## Create a function app project

[!INCLUDE [Create a project using the Azure Functions template](../../includes/functions-vstools-create.md)]

Visual Studio creates a project and in it a class that contains boilerplate code for the chosen function type. The **FunctionName** attribute on the method sets the name of the function. The **HttpTrigger** attribute specifies that the function is triggered by an HTTP request. The boilerplate code sends an HTTP response that includes a value from the request body or query string. You can add input and output bindings to a function by applying the appropriate attributes to the method. For more information, see the [Triggers and bindings](functions-dotnet-class-library.md#triggers-and-bindings) section of the [Azure Functions C# developer reference](functions-dotnet-class-library.md).

![Function code file](./media/functions-create-your-first-function-visual-studio/functions-code-page.png)

Now that you've created your function project and an HTTP-triggered function, you can test it on your local computer.

## Test the function locally

Azure Functions Core Tools lets you run an Azure Functions project on your local development computer. You are prompted to install these tools the first time you start a function from Visual Studio.  

1. To test your function, press F5. If prompted, accept the request from Visual Studio to download and install Azure Functions Core (CLI) tools. You may also need to enable a firewall exception so that the tools can handle HTTP requests.

2. Copy the URL of your function from the Azure Functions runtime output.  

    ![Azure local runtime](./media/functions-create-your-first-function-visual-studio/functions-vstools-f5.png)

3. Paste the URL for the HTTP request into your browser's address bar. Append the query string `?name=<yourname>` to this URL and execute the request. The following shows the response in the browser to the local GET request returned by the function: 

    ![Function localhost response in the browser](./media/functions-create-your-first-function-visual-studio/functions-test-local-browser.png)

4. To stop debugging, press Shift + F5.

After you have verified that the function runs correctly on your local computer, it's time to publish the project to Azure.

## Publish the project to Azure

You must have a function app in your Azure subscription before you can publish your project. You can create a function app right from Visual Studio.

[!INCLUDE [Publish the project to Azure](../../includes/functions-vstools-publish.md)]

## Test your function in Azure

1. Copy the base URL of the function app from the Publish profile page. Replace the `localhost:port` portion of the URL you used when testing the function locally with the new base URL. As before, make sure to append the query string `?name=<yourname>` to this URL and execute the request.

    The URL that calls your HTTP triggered function should be in the following format:

        http://<functionappname>.azurewebsites.net/api/<functionname>?name=<yourname> 

2. Paste this new URL for the HTTP request into your browser's address bar. The following shows the response in the browser to the remote GET request returned by the function: 

    ![Function response in the browser](./media/functions-create-your-first-function-visual-studio/functions-test-remote-browser.png)

## Watch the video

> [!VIDEO https://www.youtube-nocookie.com/embed/DrhG-Rdm80k]

## Next steps

You have used Visual Studio to create and publish a C# function app with a simple HTTP triggered function. 

+ To learn how to configure your project to support other types of triggers and bindings, see the [Configure the project for local development](functions-develop-vs.md#configure-the-project-for-local-development) section in [Azure Functions Tools for Visual Studio](functions-develop-vs.md).
+ To learn more about local testing and debugging using the Azure Functions Core Tools, see [Code and test Azure Functions locally](functions-run-local.md). 
+ To learn more about developing functions as .NET class libraries, see [Using .NET class libraries with Azure Functions](functions-dotnet-class-library.md). 

