---
# required metadata

title: Stock transfers for India
description:  This topic describes the stock transfer functionality that is available for India in Microsoft Dynamics 365 for Finance and Operations.
author: EvgenyPopovMBS
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventTransferOrders, ReqParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0

---

# Stock transfers for India

[!include [banner](../includes/banner.md)]

You can use transfer orders to process inventory transfers between warehouses. In india, when an item is shipped from a warehouse and is in transit to another warehouse, its value should be posted to a **Goods in transit** account. In addition, India Goods and Services Tax (GST) should be calculated and posted for the transfer, if the shipping and receiving branches of the organization have different tax registration numbers. After the item is registered at the receiving warehouse, the item value should be written off from the **Goods in transit** account and posted to the inventory account. Thus, the inventory account and the **Goods in transit** account form the total inventory balance. The GST value that was posted for the transfer shipment should be reversed upon the transfer receipt. If an item is shipped at a higher price than the cost price of the item, the difference between the cost price and the transfer price, along with the GST amount, is added to an **Interim transit** account, which also should be nullified when the transfer receipt is registered. If some items appear to be missing or damaged upon registering them in the receiving warehouse, the scrap quantity can be registered. The value of the scrapped items will be posted to inventory loss with the reduction of the inventory value and the reversal of the tax credit. 

The **Stock transfer** functionality that is available for India supports the above process.

## Set up stock transfers

### Configure transfer pricing

You can configure the prices that will be used when processing stock transfers for an item. The **Transfer price** page can be opened from the **Released product details** page.

### Configure stock transfer posting

You can configure the posting accounts for stock transfers on the **Transfer order** tab of the **Posting** page in the **Inventory management** module.

### Configure master planning parameters

You can define a default transfer order type and a default price type for transfer orders that are created when firming planned orders in the **Master planning** module. On the **Master planning parameters** page, tab **Standard update**, select **Transfer type** and **Price type** in the **Firm - Transfer** group.

## Create and post a stock transfer order

1.  Open **Inventory management > Outbound orders > Transfer order** and create a new transfer order.

2.  In the **From warehouse** field, select the supply warehouse that the items are dispatched from.

3.  In the **To warehouse** field, select the receiving warehouse that the items are delivered to.

4.  In the **Transfer type** field, select **Stock transfer** to apply taxes to the transfer of items.
    

    > [!NOTE]
    > If you select **Transfer order** in the **Transfer type** field, the transfer order will be posted based on the standard transfer order process.

5.  On the **Transfer order lines** tab, create a new line.

6.  In the **Item number** field, select the item to transfer.

7.  In the **Transfer quantity** field, enter the quantity of the items to transfer.

8.  In the **Unit** field, modify the default unit of measurement, if required.

9.  In the **Price type** field, select the price type for the transaction, from the following options:
    
    - **Cost price** – The cost price, or the on-hand price, of the item is used for the transaction.
    - **Transfer price** – The transfer price that is set up for the item is used for the transaction.
    
    > [!NOTE]
    > If the **Price type** is set to **Transfer price**, the quantity of the items that are defined for the combination of item and dimension in the **Transfer price** form is displayed in the **Transfer quantity** field, but it can be modified.

10.  In the **Unit price** field, enter the cost price or the transfer price for one unit of the item.

11. On the **Financial dimensions** tab, select the values of the financial dimensions for the transfer order. 

    > [!NOTE]
    > If the link between the **Site** inventory dimension and a financial dimension is configured and activated on the **Dimension link** page, the value of the financial dimension that is linked to **Site** is populated from the site that the **From warehouse** belongs to.

12.  Click the **Tax information** tab to set up taxes for the transaction, and enter details. You can change the default information that is displayed in the fields.

13. Click **Ship > Ship transfer order** to open the **Shipment** page and post a transfer order shipment.

14. Click **Receive > Receive** to open the **Receive** page and post a transfer order receipt.
