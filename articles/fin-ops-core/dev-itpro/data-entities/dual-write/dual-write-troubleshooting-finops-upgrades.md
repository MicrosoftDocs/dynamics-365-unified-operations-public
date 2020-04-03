---
# required metadata

title: Troubleshoot issues related to upgrades of Finance and Operations apps
description: This topic provides troubleshooting information that can help you fix issues that are related to upgrades of Finance and Operations apps.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Troubleshoot issues related to upgrades of Finance and Operations apps

[!include [banner](../../includes/banner.md)]



This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service. Specifically, it provides information that can help you fix issues that are related to upgrades of Finance and Operations apps.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## Database synchronization errors

**Required role to fix the issue:** System admin

You might receive an error message that resembles the following example when you try to use the **DualWriteProjectConfiguration** entity to update a Finance and Operations app to Platform update 30.

```console
Infolog diagnostic message: 'Cannot select a record in Dual write project sync (DualWriteProjectConfiguration). The SQL database has issued an error.' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'Object Server Database Synchronizer: ' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: '[Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Invalid column name 'ISDELETE'.' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'SELECT T1.PROJECTNAME,T1.EXTERNALENTITYNAME,T1.INTERNALENTITYNAME,T1.EXTERNALENVIRONMENTURL,T1.STATUS,T1.ENABLEBATCHLOOKUP,T1.PARTITIONMAP,T1.QUERYFILTEREXPRESSION,T1.INTEGRATIONKEY,T1.ISDELETE,T1.ISDEBUGMODE,T1.RECVERSION,T1.PARTITION,T1.RECID FROM DUALWRITEPROJECTCONFIGURATION T1 WHERE (PARTITION=5637144576)' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'session 1043 (Admin)' on category 'Error'. 10/28/2019 15:18:20: Infolog diagnostic message: 'Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN.' on category 'Error'.
10/28/2019 15:18:20: Application configuration sync failed.
Microsoft.Dynamics.AX.Framework.Database.TableSyncException: Custom action threw exception(s), please investigate before synchronizing again: 'InfoException:Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN."
```

To fix the issue, follow these steps.

1. Sign in to the virtual machine (VM) for the Finance and Operations app.
2. Open Visual Studio as an admin, and open the Application Object Tree (AOT).
3. Search for **DualWriteProjectConfiguration**.
4. In the AOT, right-click **DualWriteProjectConfiguration**, and select **Add to new project**. Select **OK** to create the new project that uses default options.
5. In Solution Explorer, right-click **Project properties**, and set **Synchronize Database on Build** to **True**.
6. Build the project, and confirm that the build is successful.
7. On the **Dynamics 365** menu, select **Synchronize database**.
8. Select **Synchronize** to do a full database synchronization.
9. After the full database synchronization is successful, rerun the database synchronization step in Microsoft Dynamics Lifecycle Services (LCS) and use the manual upgrade scripts as applicable, so that you can proceed with the update.

## Missing entity fields issue on maps

**Required role to fix the issue:** System admin

On the **Dual-write** page, you might receive an error message that resembles the following example:

*Missing source field \<field name\> in the schema.*

![Example of the missing source field error message](media/error_missing_field.png)

To fix the issue, first follow these steps to make sure that the fields are in the entity.

1. Sign in to the VM for the Finance and Operations app.
2. Go to **Workspaces \> Data management**, select the **Framework parameters** tile, and then, on the **Entity settings** tab, select **Refresh entity list** to refresh the entities.
3. Go to **Workspaces \> Data management**, select the **Data entities** tab, and make sure that the entity is listed. If the entity isn't listed, sign in to the VM for the Finance and Operations app, and make sure the entity is available.
4. Open the **Entity mapping** page from the **Dual-write** page in the Finance and Operations app.
5. Select **Refresh entity list** to automatically fill the fields in the entity mappings.

If the issue still isn't fixed, follow these steps.

> [!IMPORTANT]
> These steps guide you through the process of deleting an entity and then adding it again. To avoid issues, be sure to follow the steps exactly.

1. In the Finance and Operations app, go to **Workspaces \> Data management**, and select the **Data entities** tile.
2. Find the entity that is missing the field. Make a note of the target entity, staging table, entity name, and other column values.
3. If any of your processing groups depend on this entity, take appropriate action for the processing groups before you delete the entity.
4. Delete the entity that is missing the field.
5. Select **New**, and add the entity back. Specify the values that you made a note of in step 2.
6. Open the **Entity mapping** page from the **Dual-write** page in the Finance and Operations app.
7. Select **Refresh entity list** to automatically fill the fields in the entity mappings.
