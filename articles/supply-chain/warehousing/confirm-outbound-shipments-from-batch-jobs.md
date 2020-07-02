---
# required metadata

title: Confirm outbound shipments from batch jobs
description: This topic describes how to set up a batch job that automatically confirms outbound transfer-order shipments for ready-to-ship loads. The batch job described here only applies to transfer order shipments, not to sales orders.
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

Before you can use this feature, it must be enabled on your system. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Confirm outbound shipments from batch jobs*

## Process outbound shipments

To set up a scheduled batch job to run the outbound shipment confirmation for loads that are ready to ship:

1. Go to **Warehouse management \> Periodic tasks \> Process outbound shipments**.
1. Select **Filter**.
1. Select the **Range** section and insert a range for the table **Loads** and field **Load status**. Set the **Criteria** to **Loaded**.
1. Select **OK** to return to the main dialog.
1. Enable **Batch processing** under the **Run in background section**.
1. Select **Recurrence** and set the batch job to process based on the interval needed for your business.
1. Select **OK** to return to the main dialog.
1. Select **OK** in the main dialog to add the batch job to the batch queue.

For more information, see [Batch processing overview](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).
