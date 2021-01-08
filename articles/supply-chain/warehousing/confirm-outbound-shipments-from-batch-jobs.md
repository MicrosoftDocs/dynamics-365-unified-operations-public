---
# required metadata

title: Confirm outbound shipments from batch jobs
description: This topic describes how to set up a batch job that automatically confirms outbound transfer-order shipments for ready-to-ship loads.
author: perlynne
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Confirm outbound shipments from batch jobs

[!include [banner](../includes/banner.md)]

This topic describes how to set up a batch job that automatically confirms outbound transfer-order shipments for ready-to-ship loads. The batch job described here only applies to transfer order shipments, not to sales orders.

## Enable the Confirm outbound shipments from batch jobs feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. The feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Confirm outbound shipments from batch jobs*

## Process outbound shipments

To set up a scheduled batch job to run the outbound shipment confirmation for loads that are ready to ship:

1. Go to **Warehouse management \> Periodic tasks \> Process outbound shipments**.
1. The **Confirm shipment** dialog box opens. On the **Records to include** FastTab, select **Filter**.
1. The query editor dialog box opens. On the **Range** tab, add a row with the following values:
    - **Table** - *Loads*
    - **Derived table** - *Loads*
    - **Field** - *Load status*
    - **Criteria** - *Loaded*
1. Select **OK** to return to the **Confirm shipment** dialog box.
1. On the **Run in the background** FastTab, set **Batch processing** to **Yes**.
1. On the **Run in the background** FastTab, select **Recurrence**.
1. The **Define recurrence** dialog box opens. Set the run schedule as needed for your business.
1. Select **OK** to return to the **Confirm shipment** dialog box.
1. Select **OK** on the **Confirm shipment** dialog box to add the batch job to the batch queue.

For more information, see [Batch processing overview](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).
