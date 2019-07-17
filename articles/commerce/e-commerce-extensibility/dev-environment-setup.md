---
# required metadata

title: Set up a development environment
description: This topic demonstrates how to set up a development environment for Dynamics 365 for Commerce. 
author: SamJarawan
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Set up a development environment

Setting up a development environment for Dynamics 365 for Commerce involves installing three freely available tools--Visual Studio Code, Node.js, and Yarn--and installing the Dynamics 365 e-Commerce SDK. The order in which you install the tools is not important.

## Instal Visual Studio Code

A source code editor such as Visual Studio Code is recommended. Visual Studio Code is a lightweight source code editor which runs on your Windows desktop. It comes with built in support for JavaScript, TypeScript, and Node.js.


Go to the [Visual Studio Code site](https://code.visualstudio.com) and download the latest build. When the installation is complete, Visual Studio Code will automatically launch and should look similar to the image below.

![Installing Visual Studio Code](media/setup-vs-code.png)

## Instal Node.js
Node.js is a JavaScript runtime built on [Chrome’s V8 JavaScript Engine](https://v8.dev/).

Go to the [Node JS site](https://nodejs.org and download) and install the latest build (LTS).

If you rely on other versions of node being installed for other projects, we recommend that you look into using [Node Version Manager (nvm)](https://github.com/creationix/nvm) to ensure each version runs in their own isolated environment.

## Installing Yarn

Yarn is a dependency management tool that will ensure you have all the latest packages needed for your Dynamics 365 e-Commerce extensibility needs.

Navigate to https://yarnpkg.com download and insall the latest stable build.

## Installing SDK 

The SDK will give you everything you need to extend your e-Commerce site including the ability to create new modules, data actions and themes.  

The SDK configuration package is available through the following private read-only GitHub repository: [Project.Rushmore](https://github.com/Microsoft/Project.Rushmore).  Download or clone the repo to a local folder on your development machine.  Note the complete SDK and Yarn will not be downloaded and installed until you run the 'yarn' command (see below section on dowloading SDK dependencies).

If you chose to clone the repo, you can remove the .git folder (hidden directory under the root) to unlink, since you'll be using Yarn to pull down updated dependencies.

It is recommended that you use a source code repository to manage your configuration changes.  There are many available options including [Git](https://git-scm.com/downloads).

## Downloading SDK Dependencies
1. From a command prompt, navigate to the root folder of your e-Commerce SDK (c:\repos\myEcommerceSite in the example below)
1. Run the `yarn` command to grab all the latest dependency packages needed
    * This step can take several minutes to complete and should be done after any update to packages.json:
    ```
    c:\repos\MyEcommerceSite>yarn
    ```

## Running the app
1. Start the app with `yarn start`
    * This step will take several seconds to complete.  When complete you will see an output indicating the server has started and the allocated port number (default 4000)
    ```
    c:\repos\MyEcommerceSite>yarn start
    ```
1. To test that the app is running successfully, launch the below pages in a browser:
    * http://localhost:4000/version
    * http://localhost:4000/?mock=default-page
1. To stop the app, in the command prompt hit Ctrl-c twice

## Creating a new module
To add a new module called `campaignBanner`, run the `yarn d365 add-module MODULE_NAME` command, example:
```
c:\repos\MyEcommerceSite>yarn d365 add-module campaignBanner
```
This can take up to a minute to complete and will add a new module under `\src\modules\campaignBanner`.

## Modifying an existing core module
There are several available core modules that can be modified such as alert, banner and hero.
To modify the `hero` module, run the `yarn d365 modify STARTER_KIT_MODULE` command to pull down the source code:
```
c:\repos\MyEcommerceSite>yarn d365 modify hero
```
You will find the module under `\src\modules\hero`.

## Previewing Modules
To view a specific module rendering locally in a browser, such as `campaignBanner`:
1. Start the app from a command prompt with `yarn start`:
    ```
    c:\repos\MyEcommerceSite>yarn start
    ```
2. Launch the following pages in a browser (notice the module name in the query string parameter "type=MODULE_NAME"):
    * http://localhost:4000/modules?type=campaignBanner
    * http://localhost:4000/modules?type=hero
    * http://localhost:4000/modules?type=banner
