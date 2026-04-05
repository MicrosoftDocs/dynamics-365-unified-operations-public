---
title: Financial dimension activation
description: Learn about the activating financial dimension process, which involves an overview the messages users receive regarding metadata.
author: twheeloc  
ms.author: twheeloc
ms.topic: article
ms.date: 10/22/2025
ms.reviewer: twheeloc
audience: Developer
ms.assetid: dd1dd40e-6bff-47b5-bf2e-55b9a4dcde1d
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Financial dimension activation

[!include [banner](../includes/banner.md)]

>[!Warning]
> The Dimension attribute activation entity can't be used in production environments. Activating dimensions requires maintenance mode, which ensures the required schema changes are fully replicated across all AOS caches, and no open database transactions are impacted. Sandbox environments continue to support the use of the Dimension attribute activation entity. In production environments, this functionality is blocked to maintain system stability and data integrity. A service restart on the environment may be required when activating outside of maintenance mode in order to synchronize AOS caches.

This article contains information about the activating financial dimension process.

When a new financial dimension is added, users are prompted with a message stating that the financial dimension isn't consumable until **Dimension activation** is run. When **Dimension activation** is run, a database schema change occurs in the **DimensionAttributeValueCombination** and **DimensionAttributeValueSet** tables. The schema change adds a new column to the table for each financial dimension. During this process, a schema lock is placed on the two tables by Microsoft SQL Server so that the table can be updated. When the process is complete, the tables are no longer locked. If this process is attempted when a journal is open, then a deadlock may occur. If a deadlock occurs, the user could potentially receive a metadata error from the server. Users can refresh the session to get the updated metadata. The message the user receives states:

- You won't be able to consume the financial dimension anywhere until the process is run. This includes adding it to account structures.
- A schema change occurs, therefore a special privilege, the Dimension activation privilege is required to run activation.
- You should perform this during scheduled maintenance or downtime.

Adding a financial dimension is typically a deliberate business process. If there's a multi-user environment, such as a user acceptance testing or training environment, only one person should attempt this process. A second option is available when you choose the **Rebuild financial dimensions** option. 

[![Activate financial dimensions.](./media/actwiki2.png)](./media/actwiki2.png) 

The **Rebuild financial dimensions** option is set to **No** by default, as it's a process that should only be run if unexpected results occur during the initial activation process. Rebuilding will drop and readd all financial dimensions and values to the tables.

## Conditions that can prevent activation

> [!WARNING]
> If you have customizations that depend on the schema column names of dimension tables, those customizations must be removed **before** you rename or delete dimensions. Failing to do so can cause database synchronization errors after activation. After making the desired edits, you can recreate and redeploy the removed customizations.

The following conditions can cause activation to fail or time out:

- **Name conflicts** — The dimension name you're using already exists from a previous dimension that was deleted or renamed but not yet activated. Activate all pending changes to clear the conflict, or choose a different name. If the error mentions an extension column conflict on **DimensionAttributeValueCombination** or related entities, the package containing that extension must be removed before the rename can proceed.
- **Translated name conflicts** — The dimension name already exists as a translated name on another financial dimension. Choose a different name or remove the conflicting translation.
- **Change Data Capture (CDC)** — CDC is enabled on the **DimensionAttributeValueCombination** or **DimensionAttributeValueSet** tables. CDC prevents the schema changes that activation requires. Disable CDC on these tables before activating, and re-enable it afterward if needed.
- **Change tracking** — Change tracking enabled on dimension tables can cause performance issues and timeouts during activation. Disable change tracking on these tables before activating. For more information, see [Enable change tracking for entities](/dynamics365/fin-ops-core/dev-itpro/data-entities/entity-change-track).
- **Data maintenance jobs** — Background data maintenance jobs can lock dimension tables during activation. Pause these jobs before activating. For steps, see [Pausing data maintenance actions when in maintenance mode](/dynamics365/fin-ops-core/dev-itpro/sysadmin/datamaintenanceportal#pausing-data-maintenance-actions-when-in-maintenance-mode).
- **Highly variable dimensions** — Dimensions with a very large number of unique values can cause activation to time out due to data volume. For guidance, see [Highly variable dimensions](/dynamics365/finance/cost-accounting/high-var-dimensions).

## Additional resources

[Define financial dimensions](../../../finance/general-ledger/tasks/define-financial-dimensions.md)

[Maintenance mode](../sysadmin/maintenance-mode.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
