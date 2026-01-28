---
title: Set up dual-write security roles and permissions
description: Learn about the special security roles and permissions that are required for dual-write to work as expected, including a table that outlines security roles for users.
author: ramasri
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2023-01-03
ms.dyn365.ops.version: F&O 10.0.30 PU54
ms.collection: get-started
---

# Set up dual-write security roles and permissions

This article describes the special security roles and permissions that dual-write requires to work as expected.

## Assign security roles to Microsoft Dataverse users

Add all Microsoft Dataverse users to the **dual-write runtime user** and **dual-write app user** security roles.

## Assign security role to the default owning team

In Dataverse, each business unit has a default owning team that uses the same name as the business unit. Global tables are associated with the root business unit. Assign a security role to the default team of the root business unit that gives read permissions to all Dataverse tables that participate in dual-write. For information about how to set up the security role, see [Manage the security roles of a team](/power-platform/admin/manage-teams#manage-the-security-roles-of-a-team). 

To find the default team for the root business unit, follow these steps:

1. In a web browser, sign in to the Dataverse or customer engagement apps environment (for example, `https://[environment].dynamics.com`). Replace **\[environment\]** with your environment's name.
1. Open a new browser tab, and enter the following URL.

    `https://[environment].dynamics.com/api/data/v9.0/teams?$filter=isdefault eq true and businessunitid/_parentbusinessunitid_value eq null&$select=name`

    The result resembles the following example.

    ```
    {
        "@odata.context": "https://[environment].dynamics.com/api/data/v9.0/$metadata#teams(name,teamid)",
        "value": [
            {
                "@odata.etag": "W/\"...\"",
                "name": "[***]",
                "teamid": "...",
                "ownerid": "..."
            }
        ]
    }
    ```

The value of the **name** property is the default team of the root business unit. Use it to assign the security role.

## What if you miss the security setup for the default owning team?

When you invoke dual-write to propagate data changes from finance and operations apps to Dataverse, it uses the specific team as the owner of the record that it dual-writes in Dataverse. If you don't assign the security role that has read permissions, the Dataverse table throws an exception, and you receive an error message that resembles the following example:

> Unable to write data to table<br>
> ...<br>
> Principal team (Id=***, ..., is missing prvReadcol_*** privilege (Id=***) on OTC=***.

If the exception occurs, follow these steps to assign the correct permissions to the team so that dual-write can work as expected.

1. In a web browser, sign in to the Dataverse environment (for example, `https://[environment].dynamics.com`). Replace **\[environment\]** with your environment's name.
1. Open a new browser tab, and enter the following URL. Replace **\[ID\]** with the ID that's shown in the error message.

    `https://[environment].crm.dynamics.com/api/data/v9.0/teams?$select=name&$filter=teamid eq [ID]`

1. Record the **name** value for the team.
1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).
1. On the **Environments** page, find and select the Power Apps environment that's associated with the Dataverse environment.

    :::image type="content" source="media/PrincipalTeam-Security-Role-1.png" alt-text="Screenshot of list of environments on the Environments page.":::

1. On the **Access** tab, in the **Teams** section, select **See all**.

    :::image type="content" source="media/PrincipalTeam-Security-Role-2.png" alt-text="Screenshot of See all link in the Teams section of the Access tab.":::

1. Select the team name that matches the **name** value that you recorded in step 3.
1. On the toolbar, select **Manage Security Roles**.

    :::image type="content" source="media/PrincipalTeam-Security-Role-3.png" alt-text="Screenshot of Manage Security Roles button on the Teams page.":::

1. In the list of the security roles, select a role that has read permissions to the Dataverse table. Alternatively, you can create a custom security role that has read permissions to the Dataverse table and then select it in the list of security roles.

    :::image type="content" source="media/PrincipalTeam-Security-Role-4.png" alt-text="Screenshot of list of security roles on the Manage security roles page.":::

For more information about Dataverse security roles and privileges, see [Configure user security to resources in an environment](/power-platform/admin/database-security).

## Security roles for users and teams

| User or team | Security roles to assign |
|--------------|--------------------------|
| The owning team that's set as the default owning team on the cdm\_company record | **Dual-write runtime user**, **Dual-write app user**, and one or more built-in Dataverse security roles (such as **Salesperson** or **Sales Manager**) or custom Dataverse security roles to allow access to entities that are in scope for dual-write (for example, accounts, contacts, and orders) |
| A business user who's doing live synchronization | **Dual-write runtime user**, **Dual-write app user**, and one or more built-in Dataverse security roles (such as **Salesperson** or **Sales Manager**) or custom Dataverse security roles to allow access to entities that are in scope for dual-write (for example, accounts, contacts, and orders) |
| A maker who must update table maps | The **System customizer** or **System administrator** role in Dataverse, and the **System Administrator** role in finance and operations apps |
| The owning team for global records | **Dual-write runtime user**, **Dual-write app user**, and one or more built-in Dataverse security roles (such as **Salesperson** or **Sales Manager**) or custom Dataverse security roles to allow access to entities that are in scope (for example, products) |

> [!NOTE]
> For the global address book and party model solution, you must create a custom role to include privileges to entities such as Party, Contact for Party, Electronic Address, Postal Address, Party Postal Address, Postal Address Role, and Location. For the full list of entities, see [Party and global address book](party-gab.md).
