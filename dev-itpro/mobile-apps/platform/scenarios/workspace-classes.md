# Workspace class
SysAppWorkspace class can be used to configure workspaces on the server. This class is also used to publish workspaces.

## Creating a new workspace class
In order to use SysAppWorkspace for your worksapce, you need to create a new class for your workspace and extend it from SysAppWorkspace class. Your newly created workspace class can then be used to modify workspace metadata along with providing hooks for mobile app life cycle management.

Follow the steps below to create  a new workspace class for your workspace.

1. Create a new class for your workspace and extend it from SysAppWorkspace class.

    ![alt text](../../media/workspace-api/WorkspaceClass.png "Workspace class")

2. Add SysAppWorkspaceAttribute on your class and provide the AppID of your workspace.
You can find the AppId for your app from the Summary page in SysAppDesigner.

    |![alt text](../../media/workspace-api/workspaceSummary.png "Workspace summary")|
    |--|
    |![alt text](../../media/workspace-api/WorkspaceClassWithAppId.png "Workspace class with appId")|

3. (Optional) If your workspace exist as an AOT resource, then provide the AOT resource name as the 2nd parameter to SysAppWorkspaceAttribute.

    ![alt text](../../media/workspace-api/WorkspaceClassWithAOTResource.png "Workspace class with AOT Resource")

## Workspace life cycle methods
The workspace class provides the following methods that can be overridden

### getWorkspaceMetadata
This method is called to retrieve workspace metadata. Maker can override this method to update the workspace metadata. Follow the [link](#workspaceMetadata) to get more details about workspace metadata classes.

Below are some of the ways this method can be used.

1. Update the workspace, page, action and control metadata

2. Provide custom configs.

3. Hide pages, actions and controls in a workspace

4. Mark fields as mandatory.

### isWorkspaceHidden
This method can be overridden to hide or show the workspace on the mobile client. Maker can use any custom parameters to decide if the workspace needs to be hidden for a particular user.

### onBeginJob
This method is called before a job request is executed on the server. Maker can override this method to alter request parameters. Maker have access to the page or action name that the job request is for. Following are some of the ways this method can be used

1. Maker can alter the filter context for the job. For e.g. if there is a scenario that requires to always send 1 record, maker can change the filter context to it.

2. Maker can alter the job values. Job values are sent for a job that is initiated by "Actions" on the mobile client. Maker can now alter or inspect values that are being sent to start a job on the server.

### onEndJob
This method is called after a job has been executed on the server. Maker can override this method to alter the result that is sent back to mobile client. Maker have access to the page or action name that the job result is for. Following are some of the ways this method can be used.

1. Maker can alter the job result. For eg. Maker can change the values or add new set of values.

2. Maker can ignore the values that are being returned from server and instead send some other values back.

## Using workspace class for publishing workspaces from AOT resources
Workspaces can live in database as well as in AOT as resources. In order to provide visibility to workspaces stored in AOT resource you need to create a workspace class and point it to the AOT resource name that contains the workspace.

Note that workspace that are stored as AOT resource cannot be edited or deleted using the SysAppDesigner, they can only be exported.

Follow the following steps to publish a workspace that resides in an AOT resource.

1. When you are developing a workspace the workspace is stored in database. It needs to be exported from SysAppDesigner so that it can be stored as an AOT resource. The workspace will be exported as an xml file.

    ![alt text](../../media/workspace-api/ExportWorkspace.png "Export a workspace")


2. Delete the workspace from SysAppDesigner as later it will be loaded from an AOT resource

    ![alt text](../../media/workspace-api/DeleteWorkspace.png "Delete a workspace")


3. Create a new AOT resource and select the exported workspace for the resource.

    ![alt text](../../media/workspace-api/WorkspaceAsResource.png "Workspace as resource")


4. Create a new class for your workspace that extends from SysAppWorkspace. Apply the SysAppWorkspaceAttribute to the class providing the AppId and the AOT resource name which contains the resource


    ![alt text](../../media/workspace-api/NewWorkspaceClass.png "New workspace class")



5. Build the class and reopen SysAppDesigner.

6. Your workspace is now published. The workspace shows up in designer but cannot be edited or deleted.
Note that the workspace is now getting loaded from metadata.

    ![alt text](../../media/workspace-api/WorkspaceInMetadata.png "Workspace in metadata")

## Updating workspaces that have already been published
If you have your workspace as part of AOT resource, you are not able to edit it from designer. If you would like to keep on working with this workspace follow the following steps.

For this scenario we are considering a workspace called "MyWorkspace" that exist in AOT and also have a backing class called "WorkspaceInAOT"

| ![alt text](../../media/workspace-api/UpdateWorkspaceInAOT.png "Workspace in AOT")  | ![alt text](../../media/workspace-api/UpdateWorkspaceInAOTAndPublished.png "Workspace in AOT and published")|
|--|--|


1. Export the workspace using the app designer. (This will automatically create a new appID for workspaces that are stored in AOT)

2. Import the newly exported workspace using the app designer.
    a. (Optional) Change the name so that the newly added workspace can be differentiated.
    b. Copy the appID of the newly created workspace.

| ![alt text](../../media/workspace-api/UpdateWorkspaceNewWorkspace.png "New workspace in database")  | ![alt text](../../media/workspace-api/UpdateWorkspaceNewWorkspaceDetails.png "New workspace details")|
|--|--|



3. Create a new class that extends from your backing class and apply the SysAppWorkspaceAttribute with the new appID.


    ![alt text](../../media/workspace-api/UpdateWorkspaceNewWorkspaceClass.png "Workspace in metadata")

Now you can keep on working with your new workspace and the backing class. Once you are done with the changes you can merge them with the AOT based workspace.

## Delete workspaces that are in AOT resource
When mobile workspaces are stored as AOT resource, they cannot be deleted via SysAppDesigner.
Follow the following steps to delete a workspace that exist as an AOT resource.

1. Delete the AOT resource that contains the workspace.

    ![alt text](../../media/workspace-api/WorkspaceAsResourceToBeDeleted.png "Workspace to be deleted")




2. Delete the workspace class that was created for the workspace.

    ![alt text](../../media/workspace-api/WorkspaceClassToBeDeleted.png "Workspace class to be deleted")



3. Do a full model build that contained the AOT resource and the class. For my demo I will do a full build of "Application Foundation" model as my AOT resource and workspace class resided in "Application Foundation"
Un-check everything from Options tab to speed up the full build.

    |![alt text](../../media/workspace-api/FullBuildMenuItem.png "Full build menu item")|![alt text](../../media/workspace-api/FullBuild.png "Full build")|
    |--|--|


4. Once the build completed, reopen SysAppDesigner, the deleted workspace will no longer exist there.

## Workspace metadata classes
These classes can be used to inspect and update metadata related to D365 for Operations mobile workspace.

### <a id="workspaceMetadata"></a> SysAppWorkspaceMetadata
This class represents the entire mobile workspace metadata. This class can be used for

1. Update workspace title
2. Update workspace description.
3. Get pages an actions that belong to the workspace
4. Adding custom config objects that will be passed to the mobile workspace.


### SysAppPageMetadata
This class represents a page metadata for a  mobile workspace. This class can be used for

1. Update page title
2. Update page description.
3. Order a page. Set the position of the page w.r.t. other pages that are shown on the workspace.
4. Hide the page from the workspace
5. Get control metadata for controls in the page.

### SysAppActionMetadata
This class represents an action metadata for a  mobile workspace. This class can be used for

1. Update action title
2. Update action description.
3. Order an action. Set the position of the action wrt. other actions that are shown on the workspace and on pages.
4. Hide the action
5. Get control metadata for controls in the action.

### SysAppControlMetadata
This class represents control metadata for controls on a page or action. This class can be used for

1. Update control label
2. Order a control. Set the position of the control relative to other controls in a page or action
3. Hide a control
4. Mark a control as mandatory.
