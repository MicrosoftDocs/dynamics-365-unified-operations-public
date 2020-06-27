---

title: System requirements and prerequisites
description: This topic describes the system requirements and prerequisites that must be in place before you can enable dual-write for Finance and Operations apps.
author: sabinn-msft
manager: AnnBe
ms.date: 03/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-douklo
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sabinn
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# System requirements and prerequisites

[!include [banner](../../includes/banner.md)]



## Verify requirements and grant access

Before you enable dual-write, follow these steps to make sure that you meet the minimum system requirements and to grant access to the apps that must connect to each other. The dual-write health check validates the prerequisites as you complete the dual-write wizard to link a Finance and Operations app environment to a Common Data Service environment.

You must set **Enable Dynamics 365 apps** to **Yes** when you set up the environment, as shown in the following image. Alternatively, you can choose a model-driven app for Dynamics 365 environment that comes with Common Data Service and already has **Enable Dynamics 365 apps** set to **Yes**.

:::image type="content" source="media/add_database.png" alt-text="Enable apps switch" lightbox="media/add_database_expanded.png":::

1. Validate the platform update and app version.

    Make sure that your Finance and Operations app environment is running Platform update 33 (app version 10.0.9) or later.

    **Related health check result:**

    *App version is up to date*

    *Dual Write is supported on Finance and Operations app environments with Platform Update PU 33 (App version 10.0.9) or above*

2. Install the dual-write core solution.

    The dual-write core solution contains metadata for your entity maps and must be installed in your environments.

    1. In Power Apps, in the left pane, select **Solutions**.
    2. Select **Open AppSource**.
    3. Select the **Dual Write Core** solution.
    4. Follow the prompts to import the solution.

    ![Installing the dual-write core solution](media/dual-write-core-solution.png)

    **Related health check result:**

    *The dual-write core solution was found*

    *The dual-write core solution contains metadata for your entity maps and must be installed in the environment*

3. Grant Common Data Service access so that it can connect to a Finance and Operations app.

    1. Open your instance of the Finance and Operations app, search and navigate to Azure Active Directory applications.

    2. Select **New** to add a new client ID record: **6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452**. This record is the application ID for an app that will be used to connect from Common Data Service to the Finance and Operations app.
    3. Repeat the previous two steps to add another client ID record: **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b**.

    When you've finished, follow these steps to refresh the list of entities:

    1. Go to **Workspaces \> Data management**, select the **Data entities** tile, and make sure that the entity list is filled in.
    2. Go to **Workspaces \> Data management**, and select the **Framework parameters** tile. Then, on the **Entities** tab (`https://<BaseFinanceandOperationsappsURL>/?cmp=USMF&mi=DM_DataManagementWorkspaceMenuItem&TableName=DMFDefinitionGroupEntity`), select **Refresh entities list**.

    **Related health check result:**<br>
    *The Common Data Service can connect to the Finance and Operations app*<br>
    *Before you can enable dual-write, you must grant access to the apps to connect to each other<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with id 6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452 exists<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with id 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists*

4. Grant a Finance and Operations app access so that it can connect to Common Data Service.

    1. In Power Apps, select the **Settings** button (gear symbol) in the upper-right corner, go to **Advanced settings \> Security**, and then select **Users**.

        ![Users](media/selecting-users.png)

    2. Use the drop-down menu to change the view from **Enabled Users** to **Application Users**.

        ![Switching to the Application users view](media/selecting-application-users.png)

    3. Create a new user, and then, on the **User** menu, select **Application User**.

        ![Switching to Application user](media/create-new-user.png)

    4. In the **Application ID** field, enter **00000015-0000-0000-c000-000000000000**. This application ID is for a Finance and Operations app and will enable the app to connect to Common Data Service. When you've finished, follow the prompts to fill in the other fields, and then save the user account.

        ![Entering the application ID](media/add-application-id.png)

    5. Provide a primary email address.
    6. Select **Manage Roles**, and then, in the **Manage User Roles** dialog box, select the **System Administrator** check box to provide system admin rights to the selected application user.

        ![Assigning the System Administrator role](media/manage-user-roles.png)

    7. Go to **Dynamics 365 \> Settings \> Security**, select **Teams**, and then change the view to **All Owner Teams**.
    8. Select **default team for the root Business Unit**, select **Manage Roles**, and then, in the **Manage Team Roles** dialog box, select a preconfigured **Security Role** to grant a **Read** privilege with a **User** scope for each entity integrated through dual-write. 
    
      For instructions on how to create a Security Role, see [Create or configure a custom security role](https://docs.microsoft.com/power-platform/admin/database-security#create-or-configure-a-custom-security-role).
      
      > [!NOTE]
      > The root business unit’s default team will become the default owner for all records integrated through dual-write.
      > Because that team must be assigned a security role, this means that all users in the root business unit will inherit the security role.
      > This means that at the very least, **users from that business unit will have read access to all the records that are owned by that team**. If this isn’t the desired behavior, make sure that users are not a member of the root business unit.

    9. Repeat the previous five steps for application ID **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b**.

        ![Assigning the application ID](media/assign-application-id.png)

    **Related health check result:**<br>
    *The Finance and Operations app can connect to the Common Data Service*<br>
    *Before you can enable dual-write, you must grant access to the apps to connect to each other<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with id 00000015-0000-0000-c000-000000000000 exists<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with id 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists*

5. Provide app consent in the tenant.
   For dual-write core solution version 1.0.16.0 or above, this step is no longer needed.
        
    **Related health check result:**<br>
    *Apps in tenant*<br>
    *The required dual-write applications need to be installed in the tenant.<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b*

6. Make sure that the dual-write plug-ins are enabled.

    This step isn't usually required, because the plug-ins should be enabled as part of the process of installing the dual-write core solution. However, if the health check fails, follow these steps to manually enable the dual-write plug-ins:

    1. Download the [Plug-in Registration Tool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool).

        In the Plugin Registration Tool, there should be two plug-in assemblies that are associated with dual-write: **DualWriteRegistration.Plugins** and **DualWriteRuntime.Plugins**. These assemblies have plug-in steps that must be enabled, in order, before dual-write can be used. To view the plug-in steps, expand a plug-in assembly and its plug-in types. All the steps that belong to the dual-write plug-in assemblies should be enabled.

    2. To enable a step, select and hold the step (or right-click it), and then select **Enable**. If no **Enable** option is available, only a **Disable** option, the step has already been enabled and doesn't have to be changed.

        ![Using the Plug-in Registration Tool](media/plugin-registration-tool.png)

    > [!NOTE]
    > If the dual-write plug-in assemblies can't be found, import the latest version of the dual-write core solution.

    **Related health check result:**<br>
    *The dual-write registration and runtime plugins are enabled*<br>
    *To ensure listening into CRUD operations on the Common Data Service, the dual-write plugins need to be enabled*

7. Install the **Dual-write application orchestration solution** maps solution.

    In Power Apps, in the left pane, select **Solutions**. Select **Open AppSource**, and search for the solution that is named **Dual-write application orchestration solution**. Select the solution, and follow the prompts to import it. After installation, you'll find several new solutions listed under **Solutions**. For more information, see [Solutions overview](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview). 
 
    While the dual-write core solution contains metadata for your entity maps, the dual-write application orchestration solution covers these additional master data scenarios:
    
    + Customers, products, and vendors.
    + End-to-end process flows like prospect to cash.
    + On-demand functions like pricing.
    + Reference data for ledger, tax, payment terms, and schedules. 
    
    Dual-write will continue to expand in the future to support more scenarios including party, project, and hands-on inventory. The framework is extensible and accommodates customer-centric business data exchange through a few additional clicks.
    
    > [!NOTE]
    > You must select **Apply Solution** as part of the next steps, when you use the dual-write wizard to link your environments. 

8. Uninstall the Prospect to Cash (P2C) solution.

    The P2C solution doesn't work concurrently with dual-write. Therefore, don't install the P2C solution. If it's already installed, you must uninstall it before you enable dual-write.

9. Provide the supported tenant configuration.

    Make sure that the Finance and Operations app and Common Data Service are installed under the same tenant. Cross-tenant scenarios aren't currently supported.

    > [!NOTE]
    > For dual-write core solution versions lower than 1.0.16.0, see the following section for modifications and additional steps. 

**For dual-write core solution lower than version 1.0.16.0 only**

1. In step Step 3b above, create a new client ID record: **33976c19-1db5-4c02-810e-c243db79efde** (versus 6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452).
2. Add app consent in the tenant:

    1. Open the following URL, and sign in by using your admin credentials. You should be prompted for consent.

        [https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent](https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent)

    2. Select **Accept**.

        By selecting **Accept**, you indicate that you're providing consent to install the app that has application ID **33976c19-1db5-4c02-810e-c243db79efde** in your tenant. Common Data Service requires this app to communicate with the Finance and Operations app.

    
    **Related health check result:**<br>
    *Apps in tenant*<br>
    *The required dual-write applications need to be installed in the tenant.<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 33976c19-1db5-4c02-810e-c243db79efde<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b*

## Next steps

[Use the dual-write wizard to link your environments](link-your-environment.md)
