---
title: Customs declaration numbers
description: Learn how to set up and track customs declaration numbers for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/18/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-03-01
---

# Customs declaration numbers

[!include [banner](../../includes/banner.md)]

This article explains how to set up and track customs declaration numbers for Russia in Microsoft Dynamics 365 Finance.

You can track customs declarations (CDs) from the time when goods arrive at the customs terminal through the time when they are shipped to the end customer.

The customs declaration number is one of the inventory dimensions that is manually entered when goods are received. For example, you enter it when you register the invoice with the facture from the vendor and then provide the appropriate field expenditure documents, such as the facture for a sales order, to the customer. In this way, the customer can trace the customs declaration number. The specified customs declaration number is also shown in the purchase book.

To do customs declaration accounting, you must activate the corresponding tracking dimension in the item's tracking dimension group.

The receipt and sale of goods can be done in various ways. For example, goods can be received through purchase orders from the vendor, and they can be sold to the customer.

When goods are received, their customs declaration numbers are manually entered. When goods are sold, their customs declaration numbers are automatically determined, based on the item lot. The customs declaration number that was used when the goods were purchased is shown on the documents that are created when the goods are sold.

## Set up customs declaration numbers in tracking dimensions

To set up customs declaration numbers in tracking dimensions, follow these steps.

1. In Dynamics 365 Finance, go to **Product information management** \> **Setup** \> **Dimension and variant groups** \> **Tracking dimension groups**.
1. Select **New** to create a dimension group.
1. In the **Name** field, enter the name of the dimension group.
1. In the **Description** field, enter a description.
1. On the **Tracking dimensions** FastTab, in the row for **GTD number**, select the **Active** checkbox.
1. Select **Save**.

    ![A screenshot of a cell phone Description automatically generated.](../media/1%20Tracking%20dimension%20groups.jpg)

## Create a customs declaration number

Before you can register customs declaration numbers for newly received goods, you must enter them in a corresponding database. You must also enter item names, and the country or region of origin.

To create a customs declaration number, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Inquiries and reports** \> **Tracking dimensions** \> **Custom decl. numbers**.
1. Select **New** to create a customs declaration number.
1. In the **GTD number** field, enter the customs declaration number.
1. In the **Item number** field, select the item number.

    > [!NOTE]
    > The item should have the tracking dimension group that you created earlier, where the **GTD number** tracking dimension is activated.

1. In the **Country/region** field, select the country or region.
1. Select **Save**.

    ![State custom declaration numbers page.](../media/2%20State%20custom%20declaration%20numbers.jpg)

## Specify the customs declaration number in a purchase order

To specify the customs declaration number in a purchase order, follow these steps.

1.  In Dynamics 365 Finance, create a purchase order, and on the purchase order line, select the item number.

    > [!NOTE]
    > The item should have the tracking dimension group that you created earlier, where the **GTD number** tracking dimension is activated.

1. On the **Line details** FastTab, on the **Product** tab, in the **Tracking dimensions** section, in the **GTD number** field, select the customs declaration number that you created earlier.

    ![Purchase orders page Line details FastTab.](../media/3%20All%20purchase%20orders.jpg)

1. Set other purchase order parameters, and create a facture in the usual way. Column 11 of the facture shows the information about the customs declaration number.

    ![Invoice facture for a purchase order.](../media/4%20Invoice-facture.jpg)

## View the customs declaration number in the purchase book

To view the customs declaration number in the purchase book, follow these steps.

1. In Dynamics 365 Finance, after the **Incoming VAT processing** procedure is completed, on the **Purchase books journal** page, on the Action Pane, select **Update** to update the purchase book.
1. On the Action Pane, select **Lines**, and select the invoice that you just created. On the **General** tab, the **Custom decl. numbers** field shows the information about the facture and the customs declaration number.

    ![Purchase book lines General tab.](../media/5%20Purchase%20book%20lines.jpg)

## Ship goods that have customs declaration numbers

To ship goods that have customs declaration numbers, follow these steps.

1. In Dynamics 365 Finance, create a sales order, and on the sales order line, select the same item number that you used in the previous procedures in this article.
1. On the **Line details** FastTab, on the **Setup** tab, in the **Reservation** field, select **Automatic**, so that the item is automatically reserved from existing receipts when you create a sales order line.
1. On the **Product** tab, in the **Tracking dimensions** section, in the **GTD number** field, select the customs declaration number that you created earlier.

    ![Sales order page Line details FastTab.](../media/6%20Sales%20order.jpg)

1. Set other sales order parameters, and create a facture in the usual way. Column 11 of the facture shows the information about the customs declaration number.

    ![Invoice facture for a sales order.](../media/7%20Invoice-facture.jpg)




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
