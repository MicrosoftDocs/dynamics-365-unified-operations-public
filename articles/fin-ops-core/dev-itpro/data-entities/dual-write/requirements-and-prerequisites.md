---
title: System requirements and prerequisites
description: Learn about the system requirements and prerequisites that must be in place before you can enable Dual-write for finance and operations apps.
author: ericcolvinmorgan
ms.author: ericmorgan
ms.topic: conceptual
ms.date: 02/23/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2024-01-31
ms.dyn365.ops.version: AX 7.0.0
---

<!-- markdownlint-disable MD033 -->
<!-- markdownlint-disable MD025 -->
# System requirements and prerequisites troubleshooting

[!include [banner](../../includes/banner.md)]

## Verify requirements and grant access

In general, if performing [Dual-write setup from Lifecycle Services](lcs-setup.md) the automation built into that process should handle the setup steps documented on this page. If you're receiving errors like the following, these errors indicate failures occurred during the Lifecycle Services provisioning process:

| Error code | Error message |
| --- | --- |
| DW9003 | Failed to connect to CRM. Ensure that the service principal has the correct permissions to access CRM.|
| DW9003 | Failed to connect to AX. Ensure that the service principal has the correct permissions to access AX. |

This guide should assist you in recovering from these errors. In addition, this guide provides the steps taken to manually set up an environment for Dual-write.

Before Dual-write enablement, reference [system requirements for Dual-write](dual-write-system-req.md) to make sure that you meet the minimum system requirements. Access must also be granted to the apps that must connect to each other. If you're attempting to reset an environment, the Dual-write health check validates the below prerequisites as you complete the Dual-write reset wizard.

1. Grant Dataverse access so that it can connect to finance and operations apps.

    1. Open your instance of the finance and operations app, search, and navigate to Microsoft Entra ID applications.
    2. Select **New** to add a new client ID row: **6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452**. This row is the application ID for an app that is used to connect from Dataverse to the finance and operations app.
    3. On the new row for the client, select an application user that is enabled and has the appropriate privileges for Dual-write data management.
    4. Repeat the previous three steps to add another client ID row: **2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b**.

    When granted, follow these steps to refresh the list of tables:

    1. Go to **Workspaces** \> **Data management**, select the **Data entities** tile, and make sure that the entity list is filled in.
    2. Go to **Workspaces** \> **Data management**, and select the **Framework parameters** tile. Then, on the **Entity settings** tab (`https://<BaseFinanceandOperationsappsURL>/?cmp=USMF&mi=DM_DataManagementWorkspaceMenuItem&TableName=DMFDefinitionGroupEntity`), select **Refresh entity list**.

    **Related health check result:**<br>
    *The Dataverse can connect to the finance and operations app*<br>
    *Before you can enable Dual-write, you must grant access to the apps to connect to each other<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with ID 6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452 exists<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with ID 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists*

2. Grant finance and operations apps access so that it can connect to Dataverse. Follow the steps in [Create an application user](/power-platform/admin/manage-application-users#create-an-application-user), using the following information for applications IDs and security roles.

    + **Applications**: Add users to the following applications. The application users must be assigned to a security role that has **Create**, **Read**, **Write**, and **Delete** permissions on all tables in Microsoft Dataverse configured for Dual-write.

        + 00000015-0000-0000-c000-000000000000
        + 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b

        > [!NOTE]
        > Application ID **00000015-0000-0000-c000-000000000000** is not a requirement in Cloud Hosted Environments (CHEs) managed by customers. This application ID is only required in Microsoft managed environments.  

    + **Security roles**: Select a preconfigured **Security Role** to grant a **Read** privilege with a **User** scope for each table integrated through Dual-write.

        >[!NOTE]
        > Company and currency exchange tables are global in nature and all Dual-write users require read access to these 2 tables.
        > All Dual-write users will need to be added to the **Dual-Write App User** security role.
        > In order to allow non-administrator users to create rows in a Dual-write enabled table, they will need to be assigned the **Dual-Write Runtime User** security role.

        For instructions on how to create a Security Role, see [Create or configure a custom security role](/power-platform/admin/database-security#create-or-configure-a-custom-security-role).

        > [!NOTE]
        > The root business unit's default team will become the default owner for all rows integrated through Dual-write.
        > Because that team must be assigned a security role, this means that all users in the root business unit will inherit the security role.
        > This means that at the very least, **users from that business unit will have read access to all the rows that are owned by that team**. If this isn’t the desired behavior, make sure that users are not a member of the root business unit.

    **Related health check result:**<br>
    *The finance and operations app can connect to the Dataverse*<br>
    *Before you can enable Dual-write, you must grant access to the apps to connect to each other<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with ID 00000015-0000-0000-c000-000000000000 exists<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App user with ID 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b exists*

    > [!NOTE]
    > When a record is created in finance and operations apps, the **Owner** field will be set when the data is written to Dataverse, even if the matched record exists in Dataverse. Because Dual-write uses the app user that has the ID **00000015-0000-0000-c000-000000000000** to communicate with Dataverse, the **Modified by** field will be set to the app user.

3. Provide app consent in the tenant.
   For Dual-write core solution version 1.0.16.0 or later, this step is no longer needed.

    **Related health check result:**<br>
    *Apps in tenant*<br>
    *The required Dual-write applications need to be installed in the tenant.<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 6f7d0213-62b1-43a8-b7f4-ff2bb8b7b452<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App ID: 2e49aa60-1bd3-43b6-8ab6-03ada3d9f08b*

4. Install **Dual-write application solutions**.

    In the navigation pane in Power Apps, select **Solutions**. Select **Open AppSource**, and search for packages namely [Dual-write Application Core solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwappcore?tab=Overview)), [Dual-write Human Resources solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.hcm_dualwrite?tab=Overview), [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm?tab=Overview), [Dual-write Finance solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwfne?tab=Overview), [Dual-write Notes solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwnotessln?tab=Overview), [Dual-write Asset Management solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwassetmanagement?tab=Overview), and [Dual-write party and global address book solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwgabsln?tab=Overview). These solutions cover primary data scenarios like:

    + Customers, products, and vendors.
    + End-to-end process flows like quote to cash.
    + On-demand functions like pricing, inventory, ATP dates.
    + Reference data for ledger, tax, payment terms, and schedules etc.

    Follow the [separated solutions guide](separated-solutions.md) to find the solution you're looking for. Select the solution and follow the prompts to import it.

    The Dual-write framework is extensible and accommodates customer-centric business data exchange through a few more select.

    > [!NOTE]
    > You must select **Apply Solution** as part of the next steps when you use the Dual-write wizard to link your environments.
    > It may take a few minutes for the solution packages to be created in Power Apps solutions section. Wait for it to appear before moving to the next step.

5. Uninstall the Prospect to Cash (P2C) solution.

    The P2C solution doesn't work concurrently with Dual-write ([see documented limitations](dual-write-system-req.md)) and needs to be uninstalled before enabling Dual-write.

6. Provide the supported tenant configuration.

    Make sure that the finance and operations app and Dataverse are installed under the same tenant. Cross-tenant scenarios aren't currently supported.

## Next steps

[Enable table maps for Dual-write](enable-entity-map.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
