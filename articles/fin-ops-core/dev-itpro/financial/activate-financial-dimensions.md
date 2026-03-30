---
title: Financial dimension activation
description: Learn about the activating financial dimension process, which involves an overview the messages users receive regarding metadata.
author: twheeloc  
ms.author: twheeloc
ms.topic: article
ms.date: 03/27/2026
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
> You can't use the Dimension attribute activation entity in production environments. Activating dimensions requires maintenance mode, which ensures the required schema changes are fully replicated across all AOS caches, and no open database transactions are impacted. Sandbox environments continue to support the use of the Dimension attribute activation entity. In production environments, this functionality is blocked to maintain system stability and data integrity. A service restart on the environment might be required when activating outside of maintenance mode to synchronize AOS caches.

This article provides information about the activating financial dimension process.

When you add a new financial dimension, a message prompts you that the financial dimension isn't consumable until **Dimension activation** runs. When **Dimension activation** runs, a database schema change occurs in the **DimensionAttributeValueCombination** and **DimensionAttributeValueSet** tables. The schema change adds a new column to the table for each financial dimension. During this process, Microsoft SQL Server places a schema lock on the two tables so that it can update the table. When the process finishes, the tables are no longer locked. If you attempt this process when a journal is open, a deadlock might occur. If a deadlock occurs, you might receive a metadata error from the server. You can refresh the session to get the updated metadata. The message you receive states:

- You can't consume the financial dimension anywhere until the process runs. This restriction includes adding it to account structures.
- A schema change occurs, so a special privilege, the Dimension activation privilege, is required to run activation.
- You should perform this action during scheduled maintenance or downtime.

Adding a financial dimension is typically a deliberate business process. If there's a mult-user environment, such as a user acceptance testing or training environment, only one person should attempt this process. A second option is available when you choose the **Rebuild financial dimensions** option.

:::image type="content" source="./media/actwiki2.png" alt-text="Screenshot of the Activate financial dimensions page." lightbox="./media/actwiki2.png":::

The **Rebuild financial dimensions** option is set to **No** by default, as it's a process that you should only run if unexpected results occur during the initial activation process. Rebuilding drops and readds all financial dimensions and values to the tables.

## Additional resources

[Define financial dimensions](../../../finance/general-ledger/tasks/define-financial-dimensions.md)

[Maintenance mode](../sysadmin/maintenance-mode.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
