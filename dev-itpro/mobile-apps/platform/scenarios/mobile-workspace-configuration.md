---
# required metadata

title: Configure a workspace by using the SysAppWorkspace class
description: You can use the SysAppWorkspace class to configure and publish workspaces on the server. 
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

# Configure a workspace by using the SysAppWorkspace class
You can use the **SysAppWorkspace** class to configure and publish workspaces on the server.

## Create a new workspace class
To use the **SysAppWorkspace** class for your worksapce, you need to create a new class for your workspace by extending the **SysAppWorkspace** class. The new class can then be used to modify workspace metadata along with providing hooks for mobile app life cycle management.

Follow the steps below to create  a new workspace class for your workspace.

1. Create a new class for your workspace and extend it from the **SysAppWorkspace** class.

    ![Workspace class](media/workspace-api/WorkspaceClass.png)

2. Add the **SysAppWorkspaceAttribute** attribute to your class and provide the AppID of your workspace. You can find the AppId for your app from the Summary page in the mobile app designer.

    ![Workspace summary](media/workspace-api/workspaceSummary.png)
    
    ![Workspace class with appId](media/workspace-api/WorkspaceClassWithAppId.png)

3. (Optional) If your workspace is an AOT resource, then provide the AOT resource name as the second parameter to the **SysAppWorkspaceAttribute** constructor.

    ![Workspace class with AOT Resource](media/workspace-api/WorkspaceClassWithAOTResource.png)

## Workspace life cycle methods
The workspace class provides the following methods that can be overridden.

### getWorkspaceMetadata
This method is called to retrieve workspace metadata. You can override this method to update the workspace metadata. For more information, see the "Workspace metadata classes" section below. Some ways you can use the metadata are:

+ Update the workspace, page, action and control metadata.
+ Provide custom configs.
+ Hide pages, actions and controls in a workspace.
+ Mark fields as mandatory.

### isWorkspaceHidden
This method can be overridden to hide or show the workspace on the mobile client. You can use custom parameters to determine if the workspace needs to be hidden for a particular user. For more information, see [Secure a mobile app workspace](secure-mobile-workspace.md).

### onBeginJob
This method is called before a job request is executed on the server. You can override this method to change the request parameters. You have access to the page or action name that the job request is for. Using **onBeginJob**, you can:

+ Change the filter context for the job. For example, if there is a scenario that requires that one record be sent, you can change the filter context to it.
+ You can change the job values. Job values are sent for a job that is initiated by actions on the mobile client. You can change or inspect values that are being sent to start a job on the server.

### onEndJob
This method is called after a job has been executed on the server. You can override this method to change the result that is sent back to mobile client. You have access to the page or action name that the job result is for. Using **onEndJob**, you can:

+ Change the job result. For example, you can change the values or add new set of values.
+ You can ignore the values that are being returned from server and instead send some other values back.

## Use the workspace class for publishing workspaces from AOT resources
Workspaces can live in the database as well as in AOT as resources. In order to provide visibility to workspaces stored in AOT resources you need to create a workspace class and point it to the AOT resource name that contains the workspace. Workspaces that are stored as AOT resource cannot be edited or deleted using the mobile app designer, they can only be exported.

To publish a workspace that resides in an AOT resource:

1. When you are developing a workspace that is stored in database, you must export it from the mobile app designer so that it can be stored as an AOT resource. The workspace will be exported as an xml file.

    ![Export a workspace](media/workspace-api/ExportWorkspace.png)

2. Delete the workspace from the mobile app designer.It will be loaded from an AOT resource later.

    ![Delete a workspace](media/workspace-api/DeleteWorkspace.png)

3. Create a new AOT resource and select the exported workspace for the resource.

    ![Workspace as resource](media/workspace-api/WorkspaceAsResource.png)

4. Create a new class for your workspace that extends **SysAppWorkspace**. Apply the **SysAppWorkspaceAttribute** attribute to the class and provide the AppId and the AOT resource name which contains the resource.

    ![New workspace class](media/workspace-api/NewWorkspaceClass.png)

5. Build the class and reopen the mobile app designer.

6. The workspace is now published. The workspace shows up in designer but cannot be edited or deleted. Note that the workspace is loaded from metadata.

    ![Workspace in metadata](media/workspace-api/WorkspaceInMetadata.png)

## Update a workspace that has already been published
If you have your workspace as part of AOT resource, you cannot edit it from the mobile app designer. In the following example, a workspace called **MyWorkspace** exists in AOT, and it has a backing class called **WorkspaceInAOT**.

    ![Workspace in AOT](media/workspace-api/UpdateWorkspaceInAOT.png)
    
    ![Workspace in AOT and published](media/workspace-api/UpdateWorkspaceInAOTAndPublished.png)

To edit the workspace, follow these steps:

1. Export the workspace using the mobile app designer. The designer automatically creates new appIDs for workspaces that are stored in the AOT.
2. Import the newly exported workspace using the mobile app designer.
    a. (Optional) Change the name so that the newly added workspace can be distinquished from other workspaces.
    b. Copy the appID of the newly created workspace.

    ![New workspace in database](media/workspace-api/UpdateWorkspaceNewWorkspace.png)
    ![New workspace details](media/workspace-api/UpdateWorkspaceNewWorkspaceDetails.png)

3. Create a new class that extends from your backing class and apply the **SysAppWorkspaceAttribute** attribute with the new appID.

    ![Workspace in metadata](media/workspace-api/UpdateWorkspaceNewWorkspaceClass.png)

Now you can keep on working with your new workspace and the backing class. Once you are done with the changes you can merge them with the AOT-based workspace.

## Delete a workspace that is an AOT resource
When a mobile workspace is stored as an AOT resource, it cannot be deleted in the mobile app designer. Follow the following steps to delete a workspace that exist as an AOT resource.

1. Delete the AOT resource that contains the workspace.

    ![Workspace to be deleted](media/workspace-api/WorkspaceAsResourceToBeDeleted.png)

2. Delete the workspace class that was created for the workspace.

    ![Workspace class to be deleted](media/workspace-api/WorkspaceClassToBeDeleted.png)

3. Do a full model build that contains the AOT resource and the class. The following images shows a full build of the "Application Foundation" model. The AOT resource and workspace class are contained in "Application Foundation". You can uncheck everything from Options tab to speed up the full build.

    ![Full build menu item](media/workspace-api/FullBuildMenuItem.png)
    
    ![Full build](media/workspace-api/FullBuild.png)

4. When the build is finished, reopen the mobile app designer, and verify the workspace is no longer there.

## Workspace metadata classes
You can use the workspace metadata classes to inspect and update metadata related to the mobile workspace.

### SysAppWorkspaceMetadata
This class represents the entire mobile workspace metadata. This class can be used to:

+ Update the workspace title.
+ Update the workspace description.
+ Get the pages and actions that belong to the workspace.
+ Add custom config objects that will be passed to the mobile workspace.

### SysAppPageMetadata
This class represents page metadata in a mobile workspace. This class can be used to:

+ Update the page title.
+ Update the page description.
+ Order a page. You can specify the order of the page relative to other pages that are shown on the workspace.
+ Hide the page from the workspace.
+ Get control metadata for controls in the page.

### SysAppActionMetadata
This class represents an action metadata for a mobile workspace. This class can be used to:

+ Update the action title.
+ Update the action description.
+ Order an action. You can specify the order of the action relative to other actions that are shown on the workspace and on the pages.
+ Hide the action.
+ Get control metadata for controls in the action.

### SysAppControlMetadata
This class represents control metadata for controls on a page or action. This class can be used to:

+ Update the control label.
+ Order a control. You can specify the order of the control relative to other controls in a page or action.
+ Hide a control.
+ Mark a control as mandatory.
