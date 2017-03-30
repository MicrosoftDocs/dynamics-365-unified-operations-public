---
# required metadata

title: Activate financial dimensions
description: This topic contains information about the activating financial dimension process.
author: RobinARH
manager: AnnBe
ms.date: 2016-09-13 17 - 16 - 27
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 191363
ms.assetid: dd1dd40e-6bff-47b5-bf2e-55b9a4dcde1d
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Activate financial dimensions

This topic contains information about the activating financial dimension process.

When a new financial dimension is added to the system, users are prompted with a message stating that the financial dimension is not consumable until Dimension activation is run. When Dimension activation is run, a database schema change occurs in the **DimensionAttributeValueCombination** and **DimensionAttributeValueSet** tables. The schema change adds a new column to the table for each financial dimension. During this process, a schema lock is placed on the two tables by Microsoft SQL Server so that the table can be updated. When the process is complete, the tables are no longer locked. If this process is attempted when a journal is open, then a deadlock may occur. If this happens, the user could potentially receive a metadata error from the server. Users can refresh the session to get the updated metadata. The message the user receives states:

-   You will not be able to consume the financial dimension anywhere until the process is run. This includes adding it to account structures.
-   A schema change occurs, therefore a special privilege, the Dimension activation privilege is required to run activation.
-   You should perform this during scheduled maintenance or downtime.

Adding a financial dimension is typically a very deliberate business process. If there is a multi-user environment, such as a user acceptance testing or training environment, only one person should attempt this process. A second option is available when you choose the Activate option, **Rebuild financial dimensions**. 

[![ActWiki2](./media/actwiki2.png)](./media/actwiki2.png) 

The **Rebuild financial dimensions** option is set to **No** by default, as it is a process that should only be run if unexpected results occur during the initial activation process. This will drop and re-add all financial dimensions and values to the tables.

# See also

[Set up financial dimensions (Task guide)](http://ax.help.dynamics.com/en/wiki/set-up-financial/)

[Maintenance mode](..\sysadmin\maintenance-mode.md)

