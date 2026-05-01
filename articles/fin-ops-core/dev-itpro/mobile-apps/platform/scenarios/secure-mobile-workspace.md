---
title: Help secure mobile workspaces
description: Learn about how to limit a user's access to a workspace, including an overview on assigning a menu item to workspaces.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-07-20
ms.custom: 
  - bap-template
---

# Help secure mobile workspaces

[!include [banner](../../../includes/banner.md)]
[!include [mobile app deprecated](../../../includes/mobile-app-deprecation-banner.md)]

This article describes how to limit a user's access to a workspace.

## Assign a menu item to workspace

You can tie workspaces to a menu item. Users who don't have access to the menu item can't use the workspace, because the workspace only appears to users who have rights to the menu item.

If you don't assign a menu item to a workspace, the workspace always appears to the user.

Follow these steps to help secure your workspaces by assigning a menu item.

1. Add a **SysAppWorkspaceSecurityAttribute** attribute to the workspace class, and specify the menu item to assign to the workspace.

   :::image type="content" source="media/workspace-api/SecureWorkspaceOption1.png" alt-text="Screenshot of assigning a menu item to a workspace.":::

1. Build the menu item and workspace. To test your changes, sign in to the mobile app by using a user account that doesn't have access to the menu item.

## Override the workspaceHidden method

You can also specify whether the workspace is hidden or shown, based on parameters. By overriding the **workspaceHidden** method, you enable your code to control the visibility of the workspace, as shown in the following code example.

:::image type="content" source="media/workspace-api/SecureWorkspaceOption2.png" alt-text="Screenshot of overriding the workspaceHidden method.":::

## Add a menu item and override the workspaceHidden method

You can use both the preceding methods in your app. The menu item provides a security check, and the **workspaceHidden** method contains extra logic that's related to the visibility of the workspace.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
