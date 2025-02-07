--- 
title: Create a product master
description: Learn how to create a product master for the predefined variants, including a step-by-step process using the USMF demo data company. 
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac     
ms.search.form: EcoResProductListPage, EcoResProductCreate, EcoResProductDetails, EcoResProductInventoryDimensionGroups
---

# Create a product master

[!include [banner](../../includes/banner.md)]

Create a product master for the predefined variants. The demo data company used to create this procedure is USMF. This procedure is intended for the product designer.

## Create a new product master

1. Go to **Product information management > Products > Product masters**.
2. Select **New**.
3. In the **Product number** field, type a value. The number must be unique. A number sequence can be set for the **Product number** field. In this case, the user doesn't have to enter a value.
4. In the **Product name** field, type a value. Enter a descriptive product name. The value defaults to the search name, but this can be changed by the user.
5. In the **Product dimension group** field, select the drop-down button to open the lookup. The product dimension group determines which of the 4 product dimensions that can be used to create product variants. This example uses a group with color and size.
6. In the list, find and select the desired record.
7. In the list, select the link in the selected row. The default **Configuration technology** is 'Predefined variant'. This will be used for this example.
8. Select **OK**.

## Select product dimension groups

1. In the **Color group** field, select the drop-down button to open the lookup.
2. In the list, find and select the desired record.
3. In the list, select the link in the selected row.
4. In the **Size group** field, select the drop-down button to open the lookup.
5. In the list, find and select the desired record.
6. In the list, select the link in the selected row.

## Add dimension groups

1. On the Action Pane, select **Product**.
2. Select **Dimension groups** to open the drop dialog.
3. In the **Storage dimension group** field, select the drop-down button to open the lookup. The storage dimensions help you control how items are stored and taken from inventory. For example, a storage dimension can include Site and Warehouse.
4. In the list, find and select the desired record.
5. In the list, select the link in the selected row.
6. In the **Tracking dimension group** field, select the drop-down button to open the lookup. The tracking dimension group determines which tracking dimensions you can add to a product. For example, the batch number and serial number are used to track inventory items.
7. In the list, find and select the desired record.
8. In the list, select the link in the selected row.
9. Select **OK**.
10. Select **Save**.
11. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
