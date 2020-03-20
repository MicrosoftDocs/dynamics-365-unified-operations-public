---

title: "System requirements and prerequisites"
description: Describes the system requirements and prerequisites for enabling dual-write in Finance and Operations apps.
author: sabinn-msft

ms.technology: 
ms.topic: conceptual
ms.date: 03/20/2020
ms.author: v-douklo

LocalizationGroup: 
---

# System requirements and prerequisites

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

## Check requirements and grant access

Before you enable dual-write, follow the steps below to ensure you meet the minimum system requirements and to grant access to the apps that need to connect to each other. The dual-write _health check_ validates the required prerequisites below as you step through the dual-write wizard to link to the Common Data Service environment.

1. Check the platform update and app version.

    Ensure your Finance and Operations app environment is at least platform update 33 (App version 10.0.9) or above.

    Related health check:

    `App version is up to date`

    `Dual Write is supported on Finance and Operations app environments with Platform Update PU 33 (App version 10.0.9) or above`

2. Install the dual-write core solution.

   The dual-write core solution contains metadata for your entity maps and must be installed in your environments.

   To install the dual-write core solution:
   
   1. In Power Apps, select **Solutions** in the left-hand pane.
   1. Select **Open AppSource**.
   1. Choose the **Dual Write Core** solution.
   1. Follow the prompts to import the solution. 

       <kbd>![Installing the dual-write core solution](media/dual-write-core-solution.png)

    Related health check:

    `The dual-write core solution was found`

    `The dual-write core solution contains metadata for your entity maps and must be installed in the environment`

3. Grant access to the Common Data Service to connect to a Finance and Operations app.

    Follow the steps below to grant access for the Common Data Service to connect to a Finance and Operations app.

    1. Launch your Finance and Operations app instance with this URL `https://<<BaseAXURL>>/?cmp=DAT&mi=SysAADClientTable` (substitute <BaseAXURL> with your instance).

    1. Select **New** to add a new Client ID record: **33976c19-1db5-4c02-810e-c243db79efde**. This record is the Application ID for an app that would be used to connect from Common Data Service to Finance and Operations.

    1. Repeat the above steps for another client ID record: **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b**

       <kbd>![Adding another client ID record](media/another-client-id-record.png)

    **Refresh entities**

    1. From the left-hand pane, go to **Data Management/Data entities** and make sure the entity list is populated.

    1. Also, go to **Data Management > Framework parameter > Entities tab > Refresh entities list** `(https://<<BaseAXURL>>/?cmp=USMF&mi=DM_DataManagementWorkspaceMenuItem&TableName=DMFDefinitionGroupEntity)` and make sure to refresh the entity list.
       
    Related health check:

    `The Common Data Service can connect to the Finance and Operations app`

    `Before you can enable dual-write, you must grant access to the apps to connect to each other`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App id 33976c19-1db5-4c02-810e-c243db79efde exists`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App id 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App user with id 33976c19-1db5-4c02-810e-c243db79efde exists`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App user with id 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists`

4. Grant access to a Finance and Operations app to connect to the Common Data Service.

    Follow the steps below to grant access for a Finance and Operations app to connect to the Common Data Service:

    1. From Power Apps, select the gear on the top-right corner, navigate to **Advanced settings > Security**, and then select **Users**.

       <kbd>![Selecting users in advanced settings](media/selecting-users.png)

    2. In **Enabled Users**, select **Application Users**. 

       <kbd>![Switching to application users](media/selecting-application-users.png)

    3. Create a new user and select **Application User** in the **User** drop down box.

       <kbd>![Switching to application users](media/create-new-user.png)

    4. Add the value **00000015-0000-0000-c000-000000000000** to **Application ID**, follow the prompts to fill the additional fields, and then save the user account. This application ID is for a Finance and Operations app and will allow the app to connect to the Common Data Service.

       <kbd>![Add application ID](media/add-application-id.png)

    5. Provide a primary email address.

    6. Select **Manager Roles** and choose **System Administrator** to provide system administrator rights to the selected application user. 

       <kbd>![Manage user roles](media/manage-user-roles.png)

    7. From **Dynamics 365 > Settings > Security**, select **Teams**, and change the view to **All Teams**.

    8. Select the root business unit/organization, select the **Manage Roles** tab, and assign to it the required "system administrator" role.

       <kbd>![Assign the system administration role](media/assign-system-admin-role.png)

    9. Repeat steps d through h for the **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b** application ID, and follow the prompts to fill additional fields and save the user account.

       <kbd>![Assign the application ID](media/assign-application-id.png)

    1. Provide system administrator rights to the application user using **Manage Roles**.

    Related health check:

    `The Finance and Operations app can connect to the Common Data Service`

    `Before you can enable dual-write, you must grant access to the apps to connect to each other`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App user with id 00000015-0000-0000-c000-000000000000 exists`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App user with id 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists`

5. Provide app consent in the tenant.

    Follow these steps to make sure you provide the required app consent.

    1. Launch the following URL with your admin credentials, which should prompt you for consent.

       [https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent](https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent)

    1. Select **Accept**.

       Selecting accept means you're providing the consent to install the app (with `id =33976c19-1db5-4c02-810e-c243db79efde`) in your tenant. This app is required for Common Data Service to talk to the Finance and Operations app.

    1. Repeat the previous two steps for application ID **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b**, and follow the prompts.

    Related health check:

    `Apps in tenant`

    `The required dual-write applications need to be installed in the tenant.`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App ID: 33976c19-1db5-4c02-810e-c243db79efde`<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`App ID: 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b`

6. Ensure dual-write plugins are enabled.

    The dual-write plugins should be enabled as part of the dual-write core solution installation. However, if this check fails, follow the steps below to enable dual-write plugins.

    >[!Note]
    >The steps below are typically not required, and plugins should be available and enabled as part of installing the dual-write core solution.

    1. Download the [Plug-in Registration Tool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool). 
   
       In the Plugin Registration Tool, there should be two plugin assemblies associated with dual-write: **DualWriteRegistration.Plugins** and **DualWriteRuntime.Plugins**. These assemblies have plugin steps that must be enabled in order for successful use of dual-write. To view the plugin steps, you can expand the plugin assembly and its plugin types. All the steps belonging to the dual-write assemblies should be enabled. 

    2. To enable a step, select and hold (or right-click) the step, and then select **Enable** (note that if there's no option for **Enable**, but instead an option for **Disable**, then the step is already enabled and does not need to be changed).

       <kbd>![Using the plugin registration tool](media/plugin-registration-tool.png)

    If the dual-write plugin assemblies cannot be found, import the latest version of the Dual Write Core solution.

    Related health check:

    `The dual-write registration and runtime plugins are enabled`

    `To ensure listening into CRUD operations on the Common Data Service, the dual-write plugins need to be enabled`

7. Uninstall the Prospect to Cash solution.

    The "Prospect to Cash" solution or P2C doesn't work simultaneously with dual-write. So, don't install "Prospect to Cash" solution. If you have the P2C solution installed, you'll need to uninstall it before enabling dual-write.

8. Provide the supported tenant configuration.

    Ensure that the Finance and Operations app and Common Data Service are installed under the same tenant. We currently do not support cross tenant scenarios.

9. Install the dual-write entity maps solution.

    1. Like the instructions of installing the dual-write core package, in Power Apps, select **Solutions** in the left-hand pane, open **AppSource**, and search for the solution named **Common Data Service Add-in for Finance and Operations package**. Select the solution and follow the prompts to import the solution.

    1. On the dual-write UI in the Finance and Operations app, select **Apply Solution** in the top menu of the dual-write page to apply the entity maps that you just downloaded and installed. Once you apply the solution, you'll see the default entity maps published.

       <kbd>![Applying the entity maps](media/apply-entity-maps.png) 

That's it&mdash;you successfully imported and applied a Microsoft published dual-write entity map solution to your environment.

![Dual write imported and applied](media/dual-write-imported-applied.png) 

## Next steps

[How-to use the dual-write wizard to link your environments](link-your-environment.md)

