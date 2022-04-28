---
# required metadata

title: Dynamics 365 Translation Service Visual Studio Code extension (Public Preview)
description: This topic explains how to integrate the Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio Code into your Visual Studio Code workflow.
author: joshftb
ms.date: 4/18/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: joshsantana
ms.search.validFrom: 2022-05-02

---
# Dynamics 365 Translation Service Visual Studio Code extension (Public Preview)

[!include[banner](../includes/banner.md)]
[!include[preview banner](../includes/preview-banner.md)]

The Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio Code (VS Code) lets users interact with DTS from the VS Code editor. This extension was created for Dynamics 365 Business Central users who develop extensions in AL. It provides a user interface (UI) for creating, submitting, and retrieving new DTS translation requests.

Before you start, you should be familiar with development in AL. You should also know how to work with translation files in the Business Central development environment. For more information, see the following topics:

- [Developing extensions in AL](/dynamics365/business-central/dev-itpro/developer/devenv-dev-overview)
- [Working with translation files](/dynamics365/business-central/dev-itpro/developer/devenv-work-with-translation-files)

## Install VS Code and the DTS extension

If you haven't already done so, install [VS Code](https://code.visualstudio.com/).

Next, install the DTS extension for VS Code from the Visual Studio Marketplace. For more information about how to install extensions, see [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-marketplace).

## Access the DTS extension

The extension will be active if you're in an AL workspace. To access the extension, select the DTS icon in the Activity Bar on the side of the VS Code window, as shown in the following illustration.

![DTS icon in the Activity Bar in VS Code.](media/dtsvsc-icon.png)

The DTS view is opened. It consists of the resource file explorer and the translation request configuration view.

![DTS view.](media/dtsvsc-dtsview.png)

If you don't yet have any resource files, see [Working with translation files](/dynamics365/business-central/dev-itpro/developer/devenv-work-with-translation-files) for information about how to generate them. After you've generated the XML Localization Interchange File Format (XLIFF), it will appear in the resource file explorer.

## Resource file explorer

The resource file explorer provides a tree view that you can use to navigate your project's resources.

The following illustration shows an example where you're working with multiple AL project folders in one workspace. To view the translation files for a given source XLIFF, select the source node to expand it. You can also use the **Refresh** button if the tree view wasn't automatically updated after a translation job.

![Resource file explorer.](media/dtsvsc-resourceexplorer.png)

## Configure translation requests

Follow these steps to configure a translation request.

1. In the translation request configuration view, select the AL project that you want to configure. Unless you're working with multiple AL project folders in one workspace, only one project will be available.
2. In the **Target Languages** list, select the target languages.
3. If you have any XLIFF files to recycle, you can add them by using the **Choose Files** button.
4. If you want all data to be processed in the European Union (EU), select the **Process request within the European Union** checkbox.
5. Select **Save**.

![Translation request configuration view.](media/dtsvsc-reqconfig.png)

## Submit translation requests

Before you submit a new translation request, make sure that you've saved the configuration for translation requests. That configuration will be used for all future requests, unless it's overridden by a new save operation.

To submit a new request, use the **Submit Translation Request** command in the **Resources View** context menu.

![Submit Translation Request command.](media/dtsvsc-submit.png) 

You will receive a notification when the processing of the request begins and another notification when it's completed.

![Notifications about request status.](media/dtsvsc-processing.png)

Each translation file is written to the folder where the source translation file is located.

## Authentication

If you aren't signed in, you're prompted to authenticate. Make a note of the authentication code in the prompt, and then select **Open URL**.

![Authentication prompt.](media/dtsvsc-auth.png)

A new web browser window should be opened. If a new browser window isn't opened, open one, and then, in the address bar, enter the URL from the prompt. In the browser window, enter the authentication code. You will be redirected to a sign-in page. Sign in by using your credentials.

## Pending requests

If you terminate your VS Code session before all translation requests have been downloaded, you will receive a notification that lets you download the completed requests.

![Pending DTS request notification.](media/dtsvsc-pending.png)
