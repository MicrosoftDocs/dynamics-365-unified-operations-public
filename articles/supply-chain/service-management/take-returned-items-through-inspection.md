---
title: Take returned items through inspection
TOCTitle: Take returned items through inspection
ms:assetid: ecbd5142-15cb-44ba-92ee-856c8308536f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg243257(v=AX.60)
ms:contentKeyID: 36059897
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg230920(v=ax.60)/toc.json
---

# Take returned items through inspection 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

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

[Quarantine order (form)](https://technet.microsoft.com/en-us/library/aa554073\(v=ax.60\))

[Items in quarantine report (InventQuarantineOrder)](items-in-quarantine-report-inventquarantineorder.md)

[About quarantine orders](about-quarantine-orders.md)

[Specify how to dispose of returned items](specify-how-to-dispose-of-returned-items.md)

[Authorize customer returns](authorize-customer-returns.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

