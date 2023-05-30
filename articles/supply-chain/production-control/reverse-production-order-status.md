---
# required metadata

title: Reverse the production order status
description: This article describes how to reverse production order status. 
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProdParmStatusDecrease, ProdSetupStatusDecrease
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: b1e0df43-b388-4326-8fb7-501f30c89776
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Reverse the production order status

[!include [banner](../includes/banner.md)]

This article describes how to reverse production order status. 

If you reverse the status of a production order, the order and all operations that are associated with the routes revert to a previous step in the production life cycle. For example, a production order has a status of **Scheduled**, and you change the status back to **Created**. In this case, the system must first change the status to **Estimated**, which is the status that immediately precedes **Scheduled**. It can then change the status to the status that you want, **Created**. **Note:** If your order has reached the **Report as finished** status, you can still reverse it to an earlier status. However, you must re-run estimation and operations scheduling, job scheduling, or both types of scheduling, to update the information on the order. This step is required, because any reservations of remaining item consumption and operations resource consumption must also be reset. The rest of this article explains what occurs when you reverse the status of a production order in the following ways:

-   From **Estimated** to **Created**
-   From **Scheduled** to **Estimated**
-   From **Released** to **Scheduled**
-   From **Started** to **Released**

## From Estimated to Created
When you reverse the status of a production order from **Estimated** to **Created**, the item consumption that was calculated for the items in the bill of materials (BOM) is removed. Inventory transactions on the production line are deleted, and the **Remain status** field on the production order's BOM lines is reset to **Ended**. When the **Derived purchases** and **Derived production** options are selected, any underlying purchase orders or production orders are deleted. If you estimated the costs of the production order, or if you manually reserved items so that they could be used in production, those transactions are removed.

## From Scheduled to Estimated
When you reverse the status of a production order from **Scheduled** to **Estimated**, the scheduled start and end dates and times are removed. Capacity reservations that were made during scheduling are removed, and jobs that were created during job scheduling are deleted. All information that is recorded about operation scheduling and job scheduling on the **Production order details** page is reset.

## From Released to Scheduled
When you reverse the status of a production order from **Released** to **Scheduled**, the only change that occurs is the value in the status field.

## From Started to Released
When you reverse the status of a production order from **Started** to **Released**, all items that were reported as finished are reverted. If material has been picked, or if inbound and outbound deliveries have been made to production, those settings are reversed. The **Remain status** field on the production order’s BOM lines is changed from **Ended** to **Material consumption**. If time has been registered, or if quantities have been reported as finished for the operations in the production route, those settings are reversed. The **Remain status** field is changed from **Ended** to **Route consumption** in the production route. The settings for all items that are posted as in process or work in process are reversed. On the **Production order details** page, fields that show a quantity that was started or reported as finished are reset. The dates for those transactions are also reset.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]