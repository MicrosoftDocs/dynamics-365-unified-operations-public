---
# required metadata

title: Post and print a packing slip with transportation delivery details for Italy
description: Learn how to set up transportation deliverty details and post a packing slip for Italy.
author: ShylaThompson
manager: AnnBe
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
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

When you ship goods to customers, the shipment must contain a transportation delivery document (TDD). The TDD provides information about the customer, contractor, owner, and loader involved in the shipment. To print a packing slip with transportation delivery details, you must first set up transportation delivery details. 

## Set up transportation delivery details

To print the transportation document and shipping information on a packing slip, you must set up the transportation delivery details in the Accounts receivable parameters and Form setup pages.

1. Go to the Accounts receivable parameters page. 
2. Click Shipments, and then in the Carrier name field, select the name of the carrier for the customer shipment. 
3. Set the option Use transportation document information on packing slip to Yes to display the transportation details on the packing slip when it is posted. 
4. Close the page to save your changes. 
5. Click Accounts receivable > Setup > Forms > Form setup. 
6. Click the Packing slip link, and then select the Shipping details check box to print shipping information, including the carrier details, on the packing slip. 
7. Select the Transportation document check box to print the transportation document details on the packing slip. 
  > [!NOTE]
  > This check box is available only if the Use transportation document information on packing slip check box is selected on the Accounts receivable parameters page. 
8. Close the page to save your changes. 

## Post and print a packing slip with transportation delivery details

You can post and print a packing slip with a TDD for a customer shipment. The TDD will contain the following details: 
- The name and primary address of the shipping contractor. 
- The name and primary address of the shipment loader. 
- The name and primary address of the owner of the goods. 
- Any additional declarations, notes, or instructions. 
- The name of the individual who created the packing slip. 

If the details of the contractor, loader, owner, and compiler are not set on the Packing slip posting page , the name and address of the legal entity are printed on the packing slip. 

1. Click Sales and marketing > Common > Sales orders > All sales orders. 
2. Select an open sales order, and then click Pick and pack > Packing slip to open the Packing slip posting page. 
3. On the Parameters tab, in the Quantity field, select All. 
4. Set the option Posting to Yes to post the packing slip. 
5. Set the option Print packing slip to Yes to print the packing slip when it is posted. 
6. In the Carrier name field select the name of the carrier. 
7. In the Compiler field, apply the filter to sort the compiler names, and then select the name of the person who created the packing slip. 
8. In the Contractor, Loader, and Owner fields, select the type of party as Carrier, Legal entities, Customer, or Vendor to filter the transportation party, and then select the name for each party. 
9. In the Additional declarations, Additional notes, and Additional instructions fields, enter any additional information to be printed on the packing slip. 
10. Click OK to post and print the packing slip with the transportation document information. 
11. Close the page to save your changes. 
