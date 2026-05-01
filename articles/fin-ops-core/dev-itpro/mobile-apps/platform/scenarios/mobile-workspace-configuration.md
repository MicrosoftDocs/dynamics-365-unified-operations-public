---
title: Configure workspaces by using the SysAppWorkspace class
description: Learn about how you can use the SysAppWorkspace class to configure and publish workspaces on the server, including on overview on creating a new workspace class.
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

# Configure workspaces by using the SysAppWorkspace class

[!include [banner](../../../includes/banner.md)]
[!include [mobile app deprecated](../../../includes/mobile-app-deprecation-banner.md)]

Use the workspace class, **SysAppWorkspace**, to create, configure, and publish workspaces on the server. The sysAppWorkspace class provides the following categories of APIs:

- **Workspace attributes** - Use these APIs to create pages, tasks, entities, lookups, and relationships to build mobile workspaces.
  - Download the sample project for Fleet Management Mobile App. This project is an .axpp file available at [Dynamics365-for-Operations-mobile-FleetManagementSamples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples).
  - After downloading the file, open Visual Studio on your Operations development environment, select **Dynamics 365 > Import Project**, and browse for the downloaded project file. On the same dialog box, select **Overwrite** and select **Create a new solution**. After the import finishes, build the solution (or build the Fleet Management model).
  - To review the example, start by reviewing the FMReservationManagementWorkspace class to see all the pages and actions included in the workspace. Use Solution Explorer to find page and task classes, and all the assets included in each. Use the API reference for more details on each API.
  - You can create a mobile workspace through the designer pane, by using X++ attribute APIs, or by using a combination of both. For more details about how to import mobile app metadata from designer to AOT, see the "Use the workspace class to publish workspaces from AOT resources" section. The sample project Fleet Management Mobile App is a complete mobile app built by using X++ attribute APIs.

- **Workspace metadata classes** - Use these APIs to inspect and apply server-side business logic to metadata for mobile workspaces.

For a complete list of server-side APIs, see [Server-side development (workspace X++ APIs)](../mobile-workspace-server-apis.md).

## Create a new workspace class

To use the **SysAppWorkspace** class for your workspace, create a new class for the workspace that extends the **SysAppWorkspace** class. Use the new class to modify workspace metadata. The new class also provides hooks for life cycle management of the mobile app.

Follow these steps to create a new workspace class for your workspace.

1. Create a new class for your workspace, and extend it from the **SysAppWorkspace** class.

    :::image type="content" source="media/workspace-api/WorkspaceClass.png" alt-text="Screenshot of the workspace class.":::

1. Add the **SysAppWorkspaceAttribute** attribute to the new class, and provide the **AppID** value for your workspace. You can find the app ID for your app on the **Summary** page in the mobile app designer.

    :::image type="content" source="media/workspace-api/workspaceSummary.png" alt-text="Screenshot of the app ID in the workspace summary.":::

    :::image type="content" source="media/workspace-api/WorkspaceClassWithAppId.png" alt-text="Screenshot of the AppID value in the workspace class.":::

1. (Optional) If your workspace is an Application Object Tree (AOT) resource, provide the AOT resource name as the second parameter for the **SysAppWorkspaceAttribute** constructor.

    :::image type="content" source="media/workspace-api/WorkspaceClassWithAOTResource.png" alt-text="Screenshot of the AOT resource name in the workspace class.":::

## Use the workspace class to publish workspaces from AOT resources

Workspaces can reside in the database or in the AOT as resources. To provide visibility into workspaces that are stored in AOT resources, you must create a workspace class and point it to the name of the AOT resource that contains the workspace. You can't edit or delete workspaces that are stored as AOT resources by using the mobile app designer. You can only export those workspaces.

Follow these steps to publish a workspace that resides in an AOT resource.

1. When you're developing a workspace that is stored in the database, export it from the mobile app designer so that you can store it as an AOT resource. Export the workspace as an XML file.

    :::image type="content" source="media/workspace-api/ExportWorkspace.png" alt-text="Screenshot of exporting a workspace.":::

1. Delete the workspace from the mobile app designer. You will load it from an AOT resource later.

    :::image type="content" source="media/workspace-api/DeleteWorkspace.png" alt-text="Screenshot of deleting a workspace.":::

1. Create a new AOT resource, and select the exported workspace for the resource.

    :::image type="content" source="media/workspace-api/WorkspaceAsResource.png" alt-text="Screenshot of the workspace as a resource.":::

1. Create a new class for your workspace. Extend this class from **SysAppWorkspace**. Apply the **SysAppWorkspaceAttribute** attribute to the class, and provide the app ID and the AOT resource name that contains the resource.

    :::image type="content" source="media/workspace-api/NewWorkspaceClass.png" alt-text="Screenshot of the new workspace class.":::

1. Build the class, and reopen the mobile app designer.

    You published the workspace. It appears in the designer, but you can't edit or delete it. The workspace is loaded from metadata.

    :::image type="content" source="media/workspace-api/WorkspaceInMetadata.png" alt-text="Screenshot of the workspace in metadata.":::

## Update a workspace that you already published

If your workspace is part of an AOT resource, you can't edit it by using the mobile app designer. In the following example, a workspace named **MyWorkspace** exists in the AOT, and it has a backing class named **WorkspaceInAOT**.

:::image type="content" source="media/workspace-api/UpdateWorkspaceInAOT.png" alt-text="Screenshot of the workspace in the AOT.":::

:::image type="content" source="media/workspace-api/UpdateWorkspaceInAOTAndPublished.png" alt-text="Screenshot of the workspace in the AOT and published.":::

Follow these steps to edit the workspace.

1. Export the workspace by using the mobile app designer. The designer automatically creates new app IDs for workspaces that are stored in the AOT.
1. Import the newly exported workspace by using the mobile app designer.

   1. (Optional) Change the name so that you can distinguish the newly added workspace from other workspaces.
   1. Copy the app ID of the newly created workspace.

      :::image type="content" source="media/workspace-api/UpdateWorkspaceNewWorkspace.png" alt-text="Screenshot of the new workspace in database.":::

      :::image type="content" source="media/workspace-api/UpdateWorkspaceNewWorkspaceDetails.png" alt-text="Screenshot of the new workspace details.":::

1. Create a new class that extends your backing class, apply the **SysAppWorkspaceAttribute** attribute, and specify the new app ID.

    :::image type="content" source="media/workspace-api/UpdateWorkspaceNewWorkspaceClass.png" alt-text="Screenshot of the code editor with SysAppWorkspaceAttribute.":::

You can now continue to work with your new workspace and the backing class. After you finish making your changes, you can merge them with the AOT-based workspace.

## Delete a workspace that is an AOT resource

When you store a mobile workspace as an AOT resource, you can't delete it by using the mobile app designer. To delete a workspace that exists as an AOT resource, use the following steps.

1. Delete the AOT resource that contains the workspace.

    :::image type="content" source="media/workspace-api/WorkspaceAsResourceToBeDeleted.png" alt-text="Screenshot of the workspace to delete.":::

1. Delete the workspace class that you created for the workspace.

    :::image type="content" source="media/workspace-api/WorkspaceClassToBeDeleted.png" alt-text="Screenshot of the workspace class to delete.":::

1. Run a full model build that includes the AOT resource and the class. The following illustrations show a full build of the Application Foundation model. The Application Foundation model also contains the AOT resource and workspace class. To speed up the full build, you can clear all the selections on the **Options** tab.

    :::image type="content" source="media/workspace-api/FullBuildMenuItem.png" alt-text="Screenshot of the full build menu item.":::

    :::image type="content" source="media/workspace-api/FullBuild.png" alt-text="Screenshot of the full build.":::

1. When the build finishes, reopen the mobile app designer, and verify that the workspace is no longer there.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
