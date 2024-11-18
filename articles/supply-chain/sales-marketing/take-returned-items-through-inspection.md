---
title: Take returned items through inspection   
description: Learn how to take returned items through inspection, including a step-by-step process for returning items through inspection.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 05/07/2018
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: InventQuarantineOrder
---

# Take returned items through inspection

[!include [banner](../includes/banner.md)]

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Quarantine orders**.

1. Locate the order line that corresponds to the returned item that you are inspecting.

    > [!NOTE]
    > A quarantine order can be associated with just a single item number. If 10 items that have different item numbers are returned in a single shipment and sent to quarantine, 10 individual quarantine orders are created.

1. After examining the item, make a selection in the **Disposition code** field to indicate what should be done with the item and how to handle the related financial transaction. Examples include returning the item to stock and refunding the customer, scrapping the item and sending a replacement to the customer, or returning the item to the customer without credit.

    > [!NOTE]
    > If multiple returned items in a single item number batch cannot be assigned the same disposition code, you must split the quarantine order (**Functions** \> **Split**) to assign a different disposition code to each sub-batch.

1. When you are finished with the inspection, select **Report as finished** to release the returned items and create an item arrival journal entry. The person or department that receives the items then processes the journal for the items to be returned to inventory.

    –or–

    End the quarantine order, and move the items back into inventory directly by using one of the **Inventory** functions.

1. Close the form to save your changes.

## Related information

- [Specify how to dispose of returned items](specify-how-to-dispose-of-returned-items.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]