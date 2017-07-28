---
# required metadata

title: Secure workspaces using a workspace class
description: Workspace class can be used to secure workspaces.
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


# Secure workspaces using a workspace class
Workspace class can be used to secure workspaces.

## Assign a menu item to workspace
Workspaces can be tied to a menu item. Users who do not have access to the menu item will not be able to use the workspace, because the workspace is only shown to users who have rights to the menu item. 

If a menu item is not assigned to a workspace than the workspace is always shown to the user.

Follow the steps below to secure your workspaces by assigning a menu item.

1. Add a **SysAppWorkspaceSecurityAttribute** attribute to the workspace class providing a menu item to assign to the workspace.

![Assign menu item to workspace](media/workspace-api/SecureWorkspaceOption1.png)

2. Build and test the menu item and workspace by logging in to mobile app with a user account that does’t have access to the menu item. 

## Override the workspaceHidden method
You can also specify that the workspace is hidden or shown based on parameters. By overriding the **workspaceHidden** method, your code controls hiding and showing the workspace, as shown in the following code example.

![Override the workspaceHidden method](media/workspace-api/SecureWorkspaceOption2.png)

## Add an menu item and override the workspaceHidden method
You can use both methods in your app. The menu item provides a security check and the **wordspaceHidden** method contains additional logic relative to hiding and showing the workspace.
