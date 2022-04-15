---
# required metadata

title: Dynamics 365 Translation Service Visual Studio Code extension (Public Preview)
description: This topic explains how to integrate the Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio Code into your Visual Studio Code workflow.
author: joshftb
ms.date: 4/13/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ROBOTS: NOINDEX, NOFOLLOW
ms.search.region: Global
ms.author: joshsantana
ms.search.validFrom: 2022-5-2

---
# Dynamics 365 Translation Service Visual Studio Code extension (Public Preview)

[!include[banner](../includes/banner.md)]
[!include[preview banner](../includes/preview-banner.md)]

The Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio
Code (VS Code) allows users to interact with DTS from the editor. It was created
for Dynamics 365 Business central users developing extensions in AL. This
extension provides a user interface for creating, submitting, and retrieving new
DTS translation requests.

Before you start, you should be familiar with Development in Al as well as
working with translation files from within the Business Central Development
environment.

Links to those topics are available here:
* [Developing Extensions in AL](/dynamics365/business-central/dev-itpro/developer/devenv-dev-overview)

* [Working with Translation Files - Business Central](/dynamics365/business-central/dev-itpro/developer/devenv-work-with-translation-files)



## Install Visual Studio Code and the Dynamics Translation service extension

If you have not already done so, install [VS
Code](https://code.visualstudio.com/).

Next, install the Dynamics 365 Translation Service extension for VS Code from
the Visual Studio Marketplace. For additional details on installing extensions,
see [Extension
Marketplace](https://code.visualstudio.com/docs/editor/extension-marketplace).

## Using the extension

The extension will be active if you are in an AL workspace. To access the
extension, first select the DTS icon in the sidebar:

![Screenshot of Visual Studio Code with the DTS extension icon in the sidebar](media/dtsvsc-icon.png)

This will open the DTS view which is comprised of the resource file explorer and the translation request configuration view.

If you don’t have any resource files yet, see [Working with Translation
Files](/dynamics365/business-central/dev-itpro/developer/devenv-work-with-translation-files)
for guidance on generating those. Once you have generated the XLIFF, you will be
able to see it in the resource file explorer view.

![A screenshot of the DTS view](media/dtsvsc-dtsview.png)

## Resource file explorer

The resource file explorer contributes a tree view for navigating through your
project’s resources.

In the image below, we are working with multiple AL project folders within one
workspace. To see the translation files for a given source XLIFF, click or tap
on the source node to expand it. You may also use the refresh button if the tree
view wasn’t automatically refreshed after a translation job.

**![A screenshot of the resource file explorer](media/dtsvsc-resourceexplorer.png)**

## Configuring Translation Requests

You can configure the translation request in 5 steps:

1.  From the configuration view, select the AL project you wish to configure.
    Note that only one project will be available unless you are working with
    multiple AL project folders within one workspace.

2.  Select the target languages from the language list.

3.  If you have any XLIFF files for recycling, you may add them using the
    “choose files” button.

4.  If you wish to have all data processed within the European Union (EU), check
    the last checkbox.

5.  Click or tap on the blue “Save” button.

**![Screenshot of the DTS Translation configuration view](media/dtsvsc-reqconfig.png)**

## Submitting Translation Requests

Before you submit a new translation request, make sure that you have saved the
configuration for the requests. This configuration will be used for future
requests unless overridden by a new save.

To submit a new request, use the “Submit Translation Request” command located in
the “Resources View” context menu.  


**![A screenshot of the "Submit Request" toolbar item](media/dtsvsc-submit.png)**  

You will receive a notification when the request begins processing and another
upon completion.

Each translation file is written to the same folder that the source translation
file is located in.

**![A screenshot of notifications regarding request status](media/dtsvsc-submit.png)**  


## Authentication

If you aren’t logged in, you will be prompted to do so. Take note of the
authentication code, then select the blue “Open URL” button. This should open a
new browser window. If a new browser window doesn’t open, you can use your
browser to visit the page listed in the prompt. From the browser, enter the
authentication code. You will be redirected to a sign-in page. Log in with your
credentials.

**![A screenshot of an authentication notification ](media/dtsvsc-auth.png)**

## Pending requests

If you terminate your VS Code session before all translation requests have been
downloaded the extension you will receive a notification allowing you to
download those completed requests.

**![A screenshot of a pending DTS request](media/dtsvsc-pending.png)**


