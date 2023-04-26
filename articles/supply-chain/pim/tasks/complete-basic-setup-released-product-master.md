---
title: Complete basic setup of a released product master
description: This article shows how to complete the minimum setup that is required before the product master can be used in BOM versions.  
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtended, InventTableInventoryDimensionGroups, InventItemOrderSetup   
ms.topic: how-to
ms.date: 11/10/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Complete basic setup of a released product master

[!include [banner](../../includes/banner.md)]

This article shows how to complete the minimum setup that is required before the product master can be used in BOM versions.

This is the third procedure [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. You should do all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

1. Go to **Product information management \> Products \> Released products**.
2. In the list, find and select the desired record. Select the product master that you have released in the second procedure. This product master is created with the dimension-based configuration technology.  
3. On the Action Pane, select **Product**.
4. Select **Dimension groups** to open the drop dialog.
5. In the **Storage dimension group** field, select the drop-down button to open the lookup.
6. In the list, find and select the desired record. The storage dimension group determines which storage dimensions are used for product transaction. Select **Site** for this procedure.  
7. In the **Tracking dimension group** field, select the drop-down button to open the lookup.
8. In the list, find and select the desired record. The tracking dimension group determines which tracking dimensions are used for product transaction. Select **None** for this procedure.  
9. Select **OK**.
10. Select **Edit**.
11. In the **Item model group** field, select the drop-down button to open the lookup.
12. In the list, find and select the desired record. Item model groups contain settings that determine how items are controlled and handled on item receipts and issues. They also determine how item consumption is calculated. Select **FIFO** for this procedure.  
13. Expand the **Manage costs** section.
14. In the **Item group** field, select the drop-down button to open the lookup.
15. In the list, find and select the desired record. Item groups are used to manage inventory by dividing inventory items into groups. Select **CarAudio** for this procedure.  
16. On the Action Pane, select **Plan**.
17. Select **Default order settings**.
18. In the **Default order type field**, select an option. Select **Production** to specify that the default supply option for this product master is to produce it.  
19. Select **Save**.
20. Close the page.
21. Close the **Released product details** form.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]