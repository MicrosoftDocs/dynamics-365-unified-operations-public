---
# required metadata

title: Post arrival journal for returned products 
description: Post arrival journal for returned products.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WMSArrivalOverview
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


# Post arrival journal for returned products 

[!include [banner](../includes/banner.md)]


To process a return, first validate the return quantity, update the quantity field in the item arrival journal. Then select a disposition code or indicate that the returned items have to be inspected. After completing these steps, you can post the item arrival journal for the return order.

1.  Click **Inventory management** \> **Periodic** \> **Arrival overview**.

2.  In the **Setup name** filter, select **Return order**.

3.  If the list of receipts is long, use the fields in the **Range** area to narrow the list.

4.  Locate the line of the return order that you want to post, select its **Select for arrival** box, and then click **Start arrival**.

5.  Click **Journals** \> **Show arrivals from receipts** to open the **Location journal** form.
    

    > [!TIP]
    > <P>To view detailed information, select a journal, and then click <STRONG>Lines</STRONG>.</P>


6.  Make any necessary updates, and then click **Post**.

After the journal is posted, the returned items are registered in inventory, and the **Return orders** form indicates that the items have arrived at the warehouse.

## See also

[Location journal (form)](https://technet.microsoft.com/library/aa584822\(v=ax.60\))

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]