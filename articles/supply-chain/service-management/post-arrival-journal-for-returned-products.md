---
title: Post arrival journal for returned products
TOCTitle: Post arrival journal for returned products
ms:assetid: 52920dea-88b6-476d-817f-3aa0c6572bd9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg212789(v=AX.60)
ms:contentKeyID: 36057288
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg230920(v=ax.60)/toc.json
---

# Post arrival journal for returned products 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

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

[Location journal (form)](https://technet.microsoft.com/en-us/library/aa584822\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

