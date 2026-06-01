---
title: Complete basic setup of a released product master
description: Learn how to complete the minimum setup that is required before the product master can be used in BOM versions, including a step-by-step process.  
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 5/20/2026
ms.custom: bap-template
ms.reviewer: kamaybac  
ms.search.form: EcoResProductDetailsExtended, InventTableInventoryDimensionGroups, InventItemOrderSetup 
---

# Complete basic setup of a released product master

[!include [banner](../../includes/banner.md)]

This article shows how to complete the minimum setup that is required before you can use the product master in BOM versions.

This procedure is the third [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. Complete all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified in this article, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

1. Go to **Product information management > Products > Released products**.
1. In the list, find and select the desired record. Select the product master that you released in the second procedure. This product master is created by using the dimension-based configuration technology.  
1. On the Action Pane, select **Product**.
1. Select **Dimension groups** to open the drop dialog.
1. In the **Storage dimension group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. The storage dimension group determines which storage dimensions are used for product transaction. Select **Site** for this procedure.  
1. In the **Tracking dimension group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. The tracking dimension group determines which tracking dimensions are used for product transaction. Select **None** for this procedure.  
1. Select **OK**.
1. Select **Edit**.
1. In the **Item model group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. Item model groups contain settings that determine how items are controlled and handled on item receipts and issues. They also determine how item consumption is calculated. Select **FIFO** for this procedure.  
1. Expand the **Manage costs** section.
1. In the **Item group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. Item groups are used to manage inventory by dividing inventory items into groups. Select **CarAudio** for this procedure.  
1. On the Action Pane, select **Plan**.
1. Select **Default order settings**.
1. In the **Default order type field**, select an option. Select **Production** to specify that the default supply option for this product master is to produce it.  
1. Select **Save**.
1. Close the page.
1. Close the **Released product details** form.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
