---
title: Troubleshoot issues from upgrades of finance and operations apps
description: Learn about troubleshooting information that can help you fix issues that are related to upgrades of finance and operations apps.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: troubleshooting-general
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-06
---

# Troubleshoot issues from upgrades of finance and operations apps

[!include [banner](../../includes/banner.md)]

This article provides troubleshooting information for dual-write integration between finance and operations apps and Dataverse. Specifically, it provides information that can help you fix issues that are related to upgrades of finance and operations apps.

> [!IMPORTANT]
> To resolve some of the problems in this article, you need either the system admin role or Microsoft Entra tenant admin credentials. The section for each problem explains whether a specific role or credentials are required.

## Database synchronization errors

**Required role to fix the problem:** System admin

You might receive an error message that resembles the following example when you try to use the **DualWriteProjectConfiguration** table to update a finance and operations app to Platform update 30.

```console
Infolog diagnostic message: 'Cannot select a row in Dual write project sync (DualWriteProjectConfiguration). The SQL database has issued an error.' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'Object Server Database Synchronizer: ' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: '[Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Invalid column name 'ISDELETE'.' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'SELECT T1.PROJECTNAME,T1.EXTERNALENTITYNAME,T1.INTERNALENTITYNAME,T1.EXTERNALENVIRONMENTURL,T1.STATUS,T1.ENABLEBATCHLOOKUP,T1.PARTITIONMAP,T1.QUERYFILTEREXPRESSION,T1.INTEGRATIONKEY,T1.ISDELETE,T1.ISDEBUGMODE,T1.RECVERSION,T1.PARTITION,T1.RECID FROM DUALWRITEPROJECTCONFIGURATION T1 WHERE (PARTITION=5637144576)' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'session 1043 (Admin)' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN.' on category 'Error'.
10/28/2019 15:18:20: Application configuration sync failed.
Microsoft.Dynamics.AX.Framework.Database.TableSyncException: Custom action threw exception(s), please investigate before synchronizing again: 'InfoException:Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN."
```

To fix the problem, follow these steps:

1. Sign in to the virtual machine (VM) for the finance and operations app.
1. Open Visual Studio as an admin, and open the Application Object Tree (AOT).
1. Search for **DualWriteProjectConfiguration**.
1. In the AOT, right-click **DualWriteProjectConfiguration**, and select **Add to new project**. Select **OK** to create the new project that uses default options.
1. In Solution Explorer, right-click **Project properties**, and set **Synchronize Database on Build** to **True**.
1. Build the project, and confirm that the build is successful.
1. On the **Dynamics 365** menu, select **Synchronize database**.
1. Select **Synchronize** to do a full database synchronization.
1. After the full database synchronization is successful, rerun the database synchronization step in Microsoft Dynamics Lifecycle Services (LCS) and use the manual upgrade scripts as applicable, so that you can proceed with the update.

## Missing table columns issue on maps

**Required role to fix the problem:** System admin

On the **Dual-write** page, you might receive an error message that resembles the following example:

*Missing source field \<field name\> in the schema.*

:::image type="content" source="media/error_missing_field.png" alt-text="Screenshot of the missing source column error message.":::

To fix the issue, first follow these steps to make sure that the columns are in the table:

1. Sign in to your finance and operations apps environment.
1. Go to **Workspaces \> Data management**, select the **Framework parameters** tile, and then, on the **Entity settings** tab, select **Refresh entity list** to refresh the entities.
1. Go to **Workspaces \> Data management**, select the **Data entities** tab, and make sure that the entity is listed.
1. Open the **Table mapping** page from the **Dual-write** page in the finance and operations app.
1. Select **Refresh tables** to automatically fill the columns in the table mappings.

If the issue still isn't fixed, follow these steps:

> [!IMPORTANT]
> These steps guide you through the process of deleting a table and then adding it again. To avoid problems, be sure to follow the steps exactly.

1. In the finance and operations app, go to **Workspaces \> Data management**, and select the **Data entities** tile.
1. Find the table that's missing the attribute. Select **Modify target mapping** in the toolbar.
1. On the **Map staging to target** pane, select **Generate mapping**.
1. Open the **Table mapping** page from the **Dual-write** page in the finance and operations app.
1. If the attribute isn't auto-populated on the map, add it manually by selecting **Add attribute** and then **Save**.
1. Select the map and select **Run**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
