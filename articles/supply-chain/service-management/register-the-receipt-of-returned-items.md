---
# required metadata

title: Register the receipt of returned items
description: You can register the receipt of returned items using the Arrival overview form or the Registration form.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WMSArrivalOverview, InventTransRegister
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


# Register the receipt of returned items 

[!include [banner](../includes/banner.md)]


There are two methods for registering the receipt of returned items. The first method is a warehouse receiving process that uses the **Arrival overview** form. The second uses the **Registration** form.

## Register the receipt of returned items in the Arrival overview form

You can use the **Arrival overview** form to identify a return shipment by its Return Material Authorization (RMA) number. If a journal name is defined on the **Setup** tab, and journal lines that correspond to the lines selected on the **Arrival overview** form exist, a new journal header is created when you click **Start arrival**.

1.  Click **Inventory management** \> **Periodic** \> **Arrival overview**.

2.  In the **Setup name** field, select **Return order**, and then click **Update**.
    

    > [!TIP]
    > <P>You can use the <STRONG>Range</STRONG> fields to narrow the search results. You can type or select the RMA number in the <STRONG>RMA number</STRONG> field for an exact result. To define and save a set of filters that will restrict which incoming arrivals are displayed, click the <STRONG>Setup</STRONG> tab. The available filters include types, warehouses, and docks.</P>

    

    > [!WARNING]
    > <P>Return orders cannot be mixed with other arrival types in the <STRONG>Arrival overview</STRONG> form. Therefore, the reference will always be sales order, but no sales order ID will be specified on the journal header.</P>



3.  In the **Receipts** grid, locate the line that matches the item being returned, and then select the check box in the **Select for arrival** column.

4.  To exclude certain lines from the return receipt, such as items from the original order that were not included in the return shipment, clear the associated **Select for arrival** check boxes in the **Lines** table in the lower part of the form.

5.  Click the **Start arrival** button to create an arrival journal.
    

    > [!NOTE]
    > <P>You can select multiple return orders and include them all in a single arrival process. Each return order line will be copied into a corresponding item arrival journal line.</P>

    

    > [!NOTE]
    > <P>You can also manually create an arrival journal by using the <STRONG>Item arrival</STRONG> form. 



6.  Click **Inventory management** \> **Journals** \> **Item arrival** \> **Item arrival**.

7.  Select the arrival journal that you just created and then click **Lines** to open the **Journal lines, locations** form.

8.  On the **General** tab, adjust the number in the **Quantity** field, if it is required, and then assign a disposition code in the **Disposition code** field.
    
    Alternatively, you can select the **Quarantine management** check box to have the returned items sent through an inspection process in the context of a quarantine order.
    

    > [!NOTE]
    > <P>If you send the returned items through quarantine, you cannot specify a disposition code.</P>



9.  Click the **Validate** button.

10. If there are no errors in the validation process, click **Post**.

## Register the receipt of returned items in the Registration form

As an alternative to using the **Arrival overview** form, you can use the **Registration** form to register the arrival of returned items.

1.  Click **Sales and marketing** \> **Common** \> **Return orders** \> **All return orders**. Create a new return order or open the return order from the list. On the **Lines** FastTab, select the return order line. Click **Update line**, and then click **Registration**.

2.  Assign a disposition code in the **Disposition code** field, and then click **OK**.
    

    > [!NOTE]
    > <P>It is not possible to send the item for inspection as a quarantine order using the <STRONG>Registration</STRONG> form.</P>



3.  In the **Transactions** grid, select the transaction to be registered.

4.  In the **Register now** grid, click **Add**. Repeat the previous two steps until all of the returned items appear in the **Register now** grid.

5.  Click **Post all**.

## See also

[Arrival overview (form)](https://technet.microsoft.com/library/hh227654\(v=ax.60\))

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]