---
# required metadata

title: Set up order processing options
description: This topic provides information about how to process orders for call centers using Microsoft Dynamics 365 for Operations - Retail. 
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 78973
ms.assetid: 09fca083-ac0d-4f30-baf2-bb00a626be12
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up order processing options

[!include[banner](includes/banner.md)]


This topic provides information about how to process orders for call centers using Microsoft Dynamics 365 for Operations - Retail. 

Retail and commerce in Dynamics 365 for Operations supports multiple retail channels, such as online stores, brick-and-mortar stores, and call centers. In call centers, workers take customer orders over the phone and create sales orders. This topic describes how to create a call center and configure call center options. Each call center can have its own users, payment methods, price groups, financial dimensions, and modes of delivery. You can configure these options when you create the call center. **Important:** Before the call center workflows can be used when the current Dynamics AX user creates sales orders, the user must be assigned to the call center as a call center user. You can use the **Call center** page to enable or disable groups of features that are unique to call centers. The following groups of features can be enabled:

-   **Order completion** – This group includes features that are related to payments and order completion on the **Sales order** page.
-   **Directed selling** – This group includes features that are related to source codes, scripts, and catalog requests.

When you enable these features in the call center settings, they are available on the **Sales order** page for users who are associated with the call center. Most of these features require additional setup before they can be used. Images and scripts are enabled as part of the directed selling setting for the specific call center. If these feature are enabled, the scripts and product images are displayed in the FactBox pane of the **Sales order** page. The default image that is set for a product is shown. Scripts can be configured for an item, catalog, customer, or item in the context of a catalog. Call center orders can show additional details about how the price for a specific order line was derived. For example, the orders show which discounts were applied. You enable this functionality at **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters** &gt; **Prices** &gt; **Price details**. You can access the **Price details** page from the **Sales order line** drop-down list. You can use order event tracking for auditing purposes, to review the actions that are taken on an order during the order’s life cycle, or to track the actions of a specific user. For example, you can record the action every time that a user creates a sales order, puts a hold on an order, overrides a charge, or updates an order line. You can set up order events to track actions for specific users, groups of users, or all users during a specific period. You can view the actions that were taken on a document by opening the **Order events** page from the Action Pane on the page for that document. You can configure order events at **Sales and marketing** &gt; **Setup** &gt; **Events** &gt; **Order events**. When a customer's order can't be shipped on time, a company can automatically send notification email messages to the customer to explain the order status and give the customer an opportunity to cancel the order. If the delay extends beyond a specified threshold, the order can be canceled automatically. Up to three email messages can be sent at specified intervals:

1.  **First cancellation notice** – The customer can cancel the order.
2.  **Second cancellation notice** – The customer can cancel the order.
3.  **Final cancellation notice** – The system cancels the order, and the customer is informed of the cancellation.

You can exempt individual customers and products from the automatic notification and cancellation process. A margin alert is triggered when you add an item to an order. The alert contains important information about the item, such as the price margin and item profitability. You can use this information to decide whether a price override is appropriate when you add an item to the sales order. For example, you set up thresholds for the trade margins, to specify that a threshold of 40 percent or more above cost is acceptable for an item, but a threshold of 20 to 39 percent above cost is questionable. In this case, any item that has a threshold between 20 and 39 percent triggers a warning. Any item that has a threshold of less than 20 percent above cost can’t be sold, and the item price can’t be adjusted. You can configure margin alerts at **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters** &gt; **Margin alerts**. When you set up the sales tax assignment based on default rules, you can determine a matching priority for address elements. For example, you can specify that matching a sales tax group by ZIP Code or postal code has a higher priority than matching a sales tax group by state. As you enter new customer address records, the sales tax group is automatically assigned, based on how the customer’s address matches with the default rules and priority matching that you defined. You can configure this functionality on the **General ledger parameters** page.



