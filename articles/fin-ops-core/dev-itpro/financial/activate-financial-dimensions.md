---
title: Financial dimension activation
description: Learn about the activating financial dimension process, which involves an overview the messages users receive regarding metadata.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/10/2024
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: dd1dd40e-6bff-47b5-bf2e-55b9a4dcde1d
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Financial dimension activation

[!include [banner](../includes/banner.md)]

This article contains information about the activating financial dimension process.

When a new financial dimension is added to the system, users are prompted with a message stating that the financial dimension is not consumable until Dimension activation is run. When Dimension activation is run, a database schema change occurs in the **DimensionAttributeValueCombination** and **DimensionAttributeValueSet** tables. The schema change adds a new column to the table for each financial dimension. During this process, a schema lock is placed on the two tables by Microsoft SQL Server so that the table can be updated. When the process is complete, the tables are no longer locked. If this process is attempted when a journal is open, then a deadlock may occur. If a deadlock occurs, the user could potentially receive a metadata error from the server. Users can refresh the session to get the updated metadata. The message the user receives states:

- You will not be able to consume the financial dimension anywhere until the process is run. This includes adding it to account structures.
- A schema change occurs, therefore a special privilege, the Dimension activation privilege is required to run activation.
- You should perform this during scheduled maintenance or downtime.

Adding a financial dimension is typically a deliberate business process. If there is a multi-user environment, such as a user acceptance testing or training environment, only one person should attempt this process. A second option is available when you choose the Activate option, **Rebuild financial dimensions**. 

[![Activate financial dimensions.](./media/actwiki2.png)](./media/actwiki2.png) 

The **Rebuild financial dimensions** option is set to **No** by default, as it is a process that should only be run if unexpected results occur during the initial activation process. Rebuilding will drop and readd all financial dimensions and values to the tables.

## Additional resources

[Define financial dimensions](../../../finance/general-ledger/tasks/define-financial-dimensions.md)

[Maintenance mode](../sysadmin/maintenance-mode.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
