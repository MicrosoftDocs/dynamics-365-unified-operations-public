---
# required metadata

title: Batch attributes
description: This article provides information about batch attributes. Batch attributes are characteristics of raw materials and finished products that make up inventory batches. The article also explains how to assign batch attributes, and how you can search on them when you reserve batches.
author: johanhoffmann
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PdsBatchAttrib, PdsBatchAttribAssociate, PdsBatchAttribByAttribGroup, PdsBatchAttribByItem, PdsBatchAttribByitemCustomer, PdsBatchAttribGroup, WHSBatchAttribReserve
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 41de0250-4a96-412e-a412-aa06615b6b1d
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Batch attributes

[!include [banner](../includes/banner.md)]

This article provides information about batch attributes. Batch attributes are characteristics of raw materials and finished products that make up inventory batches. The article also explains how to assign batch attributes, and how you can search on them when you reserve batches.

Batch attributes are characteristics of raw materials and finished products that make up inventory batches. Batch attributes can vary, depending on factors such as environmental conditions, the quality of the raw materials that are used to produce the batch, or the outcome of the finished product. The number and types of batch attributes that are used can vary widely from one industry to another. Here are two examples that show how to use batch attributes:

-   In the cheese industry, milk, which is one of the raw materials that are used to produce the cheese, can have attributes such as fat content and percentage weight. The cheese that is produced from the milk can have other attributes, such as moisture and age.
-   In the steel industry, the iron that is produced might have attributes such as the percentages of magnesium content, silver content, and zinc content.

To better manage the number and types of attributes, you can use batch attribute groups. In this way, you don't have to add each attribute individually.

## Assign batch attributes
You can assign batch attributes to individual products that are held in inventory batches, or you can assign them to products that are associated with specific customers. Before you can assign a batch attribute at the customer level, you must assign it at the product level. The product must have the batch dimension set to **Active** in the tracking dimension group. To assign a batch attribute to an individual product, use the product-specific page. If the attribute is specific to a product for a customer, use the customer-specific page. When you add an attribute to a product, you also define other parameters. Here are some examples:

-   The minimum and maximum ranges for an attribute of the **Integer** or **Fraction** type.
-   The tolerance actions for an attribute of the **Integer** or **Fraction** type. If the value of the attribute falls outside the minimum and maximum range, the action can be either a warning message or an error message.
-   The target value for the attribute. This value is the optimal value of the attribute, and it applies to all attribute types.

You can access the pages for products that you select on the **Released products** page in Product information management. After you assign batch attributes to a product, you can add specific values to the attributes on the **Inventory batch attributes** page.

## Reserve batches
You can search on batch attributes when you do batch reservations for a sales order to fulfill a customer's order, or when you pick and reserve batches for a production order. The search helps locate an inventory batch that contains the product that has the batch attribute that you want. After you locate the batch or batches, you can reserve the product to the originating inventory transaction line.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]