---
# required metadata

title: Localize workspaces on the server
description: Workspace classes can be used in multiple ways to provide localization support to workspaces.
author: makhabaz
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: makhabaz
ms.search.validFrom: 2017-07-20
ms.dyn365.ops.version: Platform update 3

---

# Localize workspaces on server
Workspace classes can be used in multiple ways to provide localization support to workspaces.

## Using config objects to pass localized labels
A config object can be added to the workspace metadata when it is requested by the mobile app. The config object can later be used to provide localization support. Suppose you have the following scenario where a workspace requires localized labels for the **pageLink** control that you added via the business logic.

 ![Customer details with Rentals that is not localized](media/workspace-api/ConfigObjectsPage.png)

The business logic for the app contains a call to the **addLink** method to add a link to Rentals page for the current customer. In this case, the label is "Rentals". The problem is that there isn't a localized label for the link and it will always show up as "Rentals".

![Call to metadataService.addLink](media/workspace-api/ConfigObjectsBusinessLogicOriginal.png)


To use a config object to provide localized labels:

1. Create a config class that contains the fields for the labels. One field, **rentalLinkLabel**, is added to the class that will contain the label for the **pageLink** control. The config class needs to be a data contract class.

    ![Config class code](media/workspace-api/ConfigClass.png)

2. The config class is used by a workspace class for the workspace. The workspace class requires the appId of the workspace. The appId is listed on the App designer, as shown in the following image.

    ![Workspace summary](media/workspace-api/ConfigWorkspaceSummary.png)

3. The following image shows the workspace class looks like with the appId set on the attribute. The class also contains a method, **addConfig**, to set a config object that contains value for the label.

    ![Workspace class](media/workspace-api/ConfigWorkspace.png)

4. The following image shows the config object in appInit call in the mobile app.

    ![Config object in mobile app](media/workspace-api/ConfigClientSide.png)

5. The config object can now be used and passed to the addLink method instead of the hard-coded label.

    ![metadataService.addLink with call to config object](media/workspace-api/ConfigObjectsBusinessLogicFinal.png=)

## Using workspace class to update workspace title and description
Workspace api can be used to localize workspace title and description so that they are shown in the same language as the user mobile phone is using. Without doing the localization the workspace title and description fields will always be shown in the language which you have used to create them.

1. Consider the following workspace which you would like to localize
In the designer you have entered "MyWorkspace" and "A sample workspace" as title and description.

|![alt text](media/workspace-api/LocalizeWorkspaceTitle.png)| ![alt text](media/workspace-api/LocalizeWorkspaceOriginal.png) |
|--|--|


2. For localizing workspace title and description you need to create a workspace class if a workspace class do not exist for your workspace.


3. Override method getWorkspaceMetadata to get the workspace metadata. You will need workspace metadata in order to provide labels for workspace title and description fields.

4. Use properties workspaceTitle and workspaceDescription to set the workspace title and description from a label.
For the demo I have assigned dummy labels to workspaceTitle and workspaceDescription properties.

    ![alt text](media/workspace-api/LocalizeWorkspaceClass.png "Providing title and description in workspace class")



5. Build the workspace class.

6. Refresh the app list on the mobile client.

7. Below is how the workspace title and description are shown when opened from a mobile running english and danish language.

    ![alt text](media/workspace-api/LocalizeWorkspaceFinal.png "Final workspace")


