---
# required metadata

title: Post and print a packing slip with transportation delivery details for Italy
description: This topic explains how to set up transportation delivery details and post a packing slip for Italy.
author: ShylaThompson
ms.date: 04/06/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Post and print a packing slip with transportation delivery details for Italy

[!include[banner](../includes/banner.md)]

When you ship goods to customers, the shipment must contain a transportation delivery document (TDD). The TDD provides information about the customer and various parties that are involved in the shipment, such as the shipping contractor, the owner of the goods, and the shipment loader. Before you can print a packing slip that includes transportation delivery details, you must set up the transportation delivery details.

## Set up transportation delivery details

To print the TDD and shipping information on a packing slip, you must set up the transportation delivery details on the **Accounts receivable parameters** and **Form setup** pages.

1. On the **Accounts receivable parameters** page, on the **Shipments** tab, in the **Carrier name** field, select the name of the carrier for the customer shipment.
2. Set the **Use transportation document information on packing slip** option to **Yes** to show the transportation delivery details on the packing slip when it's posted.
3. Close the page to save your changes.
4. Select **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
5. On the **Packing slip** tab, select the **Shipping details** check box to print shipping information on the packing slip. The shipping information includes the carrier details.
6. Select the **Transportation document** check box to print the transportation document information on the packing slip.

    > [!NOTE]
    > The **Transportation document** check box is available only if the **Use transportation document information on packing slip** option is set to **Yes** on the **Accounts receivable parameters** page.

7. Close the page to save your changes.

## Post and print a packing slip that includes transportation delivery details

You can post and print a packing slip that includes a TDD for a customer shipment. The TDD contains the following details:

- The name and primary address of the shipping contractor
- The name and primary address of the shipment loader
- The name and primary address of the owner of the goods
- Any additional declarations, notes, or instructions
- The name of the person who created the packing slip (that is, the compiler)

If the details of the contractor, loader, owner, and compiler aren't set on the **Packing slip posting** page, the name and address of the legal entity are printed on the packing slip instead.

1. Select **Sales and marketing** &gt; **Common** &gt; **Sales orders** &gt; **All sales orders**.
2. Select an open sales order, and then, on the Action Pane, on the **Pick and pack** tab, select **Packing slip** to open the **Packing slip posting** dialog box.
3. On the **Parameters** FastTab, in the **Quantity** field, select **All**.
4. Set the **Posting** option to **Yes** to post the packing slip.
5. Set the **Print packing slip** option to **Yes** to print the packing slip when it's posted.
6. In the **Carrier name** field, select the name of the carrier.
7. In the **Compiler** field, apply the filter to sort the compiler names, and then select the name of the person who created the packing slip.
8. In the **Contractor**, **Loader**, and **Owner** fields, select the type of party to filter the transportation party, and then select the name of each party.
9. In the **Additional declarations**, **Additional notes**, and **Additional instructions** fields, enter any additional information that should be printed on the packing slip.
10. Select **OK** to post and print a packing slip that includes the transportation document information.
11. Close the page to save your changes.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]