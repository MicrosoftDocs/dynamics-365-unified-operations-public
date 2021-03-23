---
# required metadata

title: Workers responsible for quality
description: This topic describes how to configure workers responsible for approving nonconformances.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Workers responsible for approving nonconformances

[!include [banner](../includes/banner.md)]

This topic describes how to configure workers responsible for approving nonconformances.

Nonconformances must be approved before users can start entering details such as corrections or operations. For a user to be able to approve a nonconformance, their user ID must be linked to a worker record. You can also optionally configure workers responsible for quality and allow a worker to approve work on behalf of another worker.

## Enable a user for nonconformance processing

For a user to be able to approve or reject nonconformances, their user record must be linked to a worker record. This allows the approval fields to auto populate and for the timesheet to default the current user. To use the document notes, the user must also have document handling activated in the user options. To make these settings:

1. Go to **System administration > Users > Users**.
1. Find and open the user you want to enable.
1. Set **Person** to the name of the worker related to the current user record. 
1. On the Action Pane, select **User options** to open the **Options** page for the current user record.
1. Open the **Preferences** tab.
1. Set **Enable document handling** to *Yes*.
1. Close the pages.

## Define workers responsible for quality

1. Go to **Inventory management > Setup > Quality control > Workers responsible for quality**.
2. Select **New** in the Action Pane.
3. In the **Worker** field, select the worker that enters quality data.
4. In the **Worker responsible** field, select the worker that the selected worker enters work on behalf of. This worker will default into **Worker** fields when creating and updating nonconformances.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality charges](quality-charges.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](quality-diagnostic-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]