# Localizing workspaces on server
Workspace classes can be used in multiple ways to provide localization support to workspaces.

## Using config objects to pass localized labels
Config objects can be added to the workspace metadata when it is requested by the mobile app. These config object can later be used to provide localization support.

Consider the following scenario where a workspace requires localized labels for the pageLink control that was added via the business logic.

 ![alt text](media/workspace-api/ConfigObjectsPage.png "Workspace that needs to be localized")

In the business logic for the app we have called the addLink api to add a link to Rentals page for the current customer. Note that we are providing "Rentals" as the label.

![alt text](media/workspace-api/ConfigObjectsBusinessLogicOriginal.png "Original business logic")

As you can see above the problem is we don’t have a localized label for the link and it will always show up as "Rentals"


Below are the steps to show how config objects can be utilized to provide localized labels.

1. Create a config class that contains the fields for the labels. For our requirement I am adding 1 field on the class that will contain the label for the pageLink control. The config class needs to be a data contract class

    ![alt text](media/workspace-api/ConfigClass.png "Config class")

2. This config class will be utilized by a workspace class for the workspace. Workspace class requires appId of the workspace. You can easily get appId from the App designer form as shown below.

    ![alt text](media/workspace-api/ConfigWorkspaceSummary.png "Workspace summary")


3. Below is how the workspace class looks like with the appId set on the attribute. It also contains method to set a config object that contains value for the label

    ![alt text](media/workspace-api/ConfigWorkspace.png "Workspace class")


4. In the mobile app, you will get the config object in appInit call as shown below

    ![alt text](media/workspace-api/ConfigClientSide.png "Config object in mobile app")

5. The config object can now be utilized and passed further to addLink api instead of the hard coded label in the business logic file

  ![alt text](media/workspace-api/ConfigObjectsBusinessLogicFinal.png "Update business logic")


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


