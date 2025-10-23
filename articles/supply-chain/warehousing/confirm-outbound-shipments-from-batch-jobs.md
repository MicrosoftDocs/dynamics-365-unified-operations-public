---
title: Confirm outbound shipments from batch jobs
description: Learn how to set up a batch job that confirms outbound transfer-order shipments for ready-to-ship loads with an outline on process outbound shipments.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 07/31/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: 
---

# Confirm outbound shipments from batch jobs

[!include [banner](../includes/banner.md)]

This article describes how to set up a batch job that automatically confirms outbound transfer-order shipments for ready-to-ship loads. The batch job described here only applies to transfer order shipments, not to sales orders.

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

Learn more in [Batch processing overview](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
