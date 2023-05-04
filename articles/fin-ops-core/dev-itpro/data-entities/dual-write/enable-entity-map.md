---
title: Enable table maps for dual-write
description: This article describes how the table maps work for dual-write.
author: nhelgren
ms.date: 02/21/2023
ms.topic: article
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Enable table maps for dual-write

[!include [banner](../../includes/banner.md)]



When you enable a table map for dual-write, it begins at the **Not running** status. The table map then goes through an initialization phase, where it does an initial write by copying pre-existing data on tables on both sides. When the table is completely enabled, it changes the status of the table map to **Running**.

![Enabling table maps.](media/enabling-entity-map.png)

While the status is **Running**, you can pause a table. All changes are then queued until you resume. When you resume, the table enters "catch-up mode" and plays back all the queued changes.

The following illustration shows an example of a table that is paused.

![Paused table.](media/stop-pause-entity.png)

| Status | Description | Available actions |
|---|---|---|
| Not running | The table hasn't yet been enabled for dual-write. Every table begins at the **Not running** status. | Run |
| Initializing | The initial write is occurring. | None |
| Running | The table is enabled for dual-write. | Stop, Pause |
| Paused | The table is in a paused state, and all new requests are queued. | Run |
| Resuming | The table is catching up on rows that were queued while the table was paused. | None |

During the initialization phase, any pre-existing data that you have is copied as part of the initial write phase.

![Copying pre-existing data.](media/initial-write-phase.png)

Entities have several dependent tables. For example, Customer-Contact tables have customer groups and currencies as dependent tables.

![Dependent tables.](media/dependent-or-related-entities.png)

Because these are relational apps that have relational data, if you don't enable the dependent tables, you might encounter errors later. To help prevent these errors, before you enable a table map, you're provided with a list of the related tables that we recommend that you enable.

## <a id="enable-table-map"></a>Example: Enabling the Customers V3—Contacts table map

When you select a table map (for example, **Customers V3—Contacts**) and select **Run**, a dialog box appears before the table map is enabled. This dialog box lists all the dependent tables. You can select the **Show related table map(s)** option to show all the related table maps. To enable the selected table map and all its related tables, select **Run** in the dialog box.

> [!NOTE]
> The behavior is similar when you pause a table. In that case, you have the option to pause all the related tables too.

![Listing all the dependent tables.](media/related-entity-maps.png)

During data synchronization, if records that have the same keys are found on both sides, and the keys have competing attribute values, a merge conflict occurs. In this case, you must select a **Master for initial sync** value for every entity map in the list to specify the master data that should be used to resolve conflicts. By default, Dataverse is used. 

> [!NOTE]
> The **Master for initial sync** value is used only to resolve conflicts. It doesn't control the direction that data should move in. 

If you don't want to copy pre-existing data, skip the initial synchronization by clearing the **Initial Sync** checkbox. Alternatively, remove one or more of the related tables by canceling the selection of them. You can also drag the table maps to change the order that they'll be synced in.

After you've finished making your selections in the dialog box, and you select **Run**, the table map and all its related tables go through the initial write phase. You're redirected to the table map list page. If any errors occur, you can view the details on the **Initial sync details** tab. This tab shows details about all the errors that occur while pre-existing data is copied. After you fix the underlying errors, you can rerun the execution and monitor the outcome. Alternatively, if you no longer want to sync the pre-existing data, or if you experience recurring issues because of underlying data, you can skip the initial write phase. Instead, you can turn on live writes by selecting **Skip initial sync**.

![Skipping initial writes.](media/skip-initial-writes.png)

## <a id="criteria-for-linking"></a>Criteria for linking tables

To enable table maps for dual-write, you must define an alternative key in Dataverse. The key that's defined in the finance and operations app must match the value of the alternative key in Dataverse.

For example, in a finance and operations app, **CustomerAccount** is the key for the Account table.

![Key for the Account table in a finance and operations app.](media/define-alternative-key.png)

In Dataverse, **accountnumber** is defined as the key for the Account table.

![Account table defined in Dataverse.](media/define-account-entity.png)

In the Customers V3 table map, you can see that **CustomerAccount** is mapped to **accountnumber**.

![Mapping in the table map.](media/mapped-to-entity-map.png)

## Next steps

[Customize table and column mappings](customizing-mappings.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
