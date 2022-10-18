---
# required metadata

title: Take returned items through inspection   
description: Take returned items through inspection.
author: sorenva
ms.date: 05/07/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventQuarantineOrder
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


# Take returned items through inspection 

[!include [banner](../includes/banner.md)]


1.  Click **Inventory management** \> **Periodic** \> **Quality management** \> **Quarantine orders**.

2.  Locate the order line that corresponds to the returned item that you are inspecting.

    > [!NOTE]
    > <P>A quarantine order can be associated with just a single item number. If 10 items that have different item numbers are returned in a single shipment and sent to quarantine, 10 individual quarantine orders are created.</P>

3.  After examining the item, make a selection in the **Disposition code** field to indicate what should be done with the item and how to handle the related financial transaction. Examples include returning the item to stock and refunding the customer, scrapping the item and sending a replacement to the customer, or returning the item to the customer without credit.
    
    > [!NOTE]
    > <P>If multiple returned items in a single item number batch cannot be assigned the same disposition code, you must split the quarantine order (<STRONG>Functions</STRONG> &gt; <STRONG>Split</STRONG>) to assign a different disposition code to each sub-batch.</P>


4.  When you are finished with the inspection, click **Report as finished** to release the returned items and create an item arrival journal entry. The person or department that receives the items then processes the journal for the items to be returned to inventory.
    
    –or–
    
    End the quarantine order, and move the items back into inventory directly by using one of the **Inventory** functions.

5.  Close the form to save your changes.

## See also

[Specify how to dispose of returned items](specify-how-to-dispose-of-returned-items.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]