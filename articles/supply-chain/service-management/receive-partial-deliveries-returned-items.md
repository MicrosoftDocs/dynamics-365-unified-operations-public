---
# required metadata

title: Receive partial deliveries of returned items   
description: Partial deliveries are defined in terms of return order lines, not return order shipments.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Receive partial deliveries of returned items    

[!include [banner](../includes/banner.md)]


Partial deliveries are defined in terms of return order lines, not return order shipments.

This means that if you receive the full quantity that is indicated on one return order line, but you receive nothing from the other lines in the return order, the delivery is not a partial delivery. However, if a return order line requires 10 units of a particular item to be returned, but you receive only four, it is a partial delivery.

If a return shipment contains less than the full quantity of a return order line, you can set the shipment aside and wait for the rest of the returned quantity to arrive, or you can register and post the partial quantity.

## Register and post a partial quantity

1.  After you select a return order for arrival on the **Arrival overview - Warehouse: %1, Dock: %2, Journal name: %3** form, click **Start arrival** to create the arrival journal, and then click **Journals** \> **Show arrivals from receipts** to open the **Location journal** form.

2.  Select the line of the journal that you want to work with, and then click **Lines** to open the **Journal lines, locations** form.

3.  Select the line of the item number for which only a partial quantity has arrived, and then click **Functions** \> **Split** to open the **Split** form.

4.  In the **Split quantity** field, enter the quantity for the total number of items that have been received, and then click **OK**.

5.  On the **Journal lines, locations** form, select the line for the quantity of items that has arrived, and then click **Post**. You can post the line for the additional quantity after the items have arrived.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]