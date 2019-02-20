---
# required metadata

title: Create and encumber a general budget reservation
description: This topic provides information about creating and encumbering a general budget reservations for public sector in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Create and encumber a general budget reservation

[!include [banner](../includes/banner.md)]

After you set up your system to use general budget reservations, you can create reservation documents. General budget reservations are available to the documents that are required for the purchasing method you choose. These methods include purchase order, purchase requisition, and vendor invoice.

To create a general budget reservation, use the following steps.

1.  Go to **Budgeting \> General budget reservations**.

2.  Click **New**.

3.  In the **Creation** slider enter all necessary fields.

    -   Reservation type decides which type of document will relieve this General budget reservation (Purchase requisition, Purchase order or Vendor invoice).

    -   Selecting a Purchase requisition in this dialogue relieves an upstream Purchase requisition. Reservation type must be Purchase order or Vendor invoice relieved in this case.

4.  Click **OK**.

5.  In the details page, fill in the fields as necessary in the General budget reservation header.

6.  Under **General budget reservation** lines, click **Add line**. Enter the information for the first line of your reservation. Repeat this step until you have entered all lines.

    -   If a purchase requisition applies to the budget reservation and wasn’t referenced earlier in the creation dialogue, on the Line details section, you can select the purchase requisition line that the selected line in the budget reservation references. Items and services on the selected requisition line, including procurement category, are passed to the general budget reservation line. This is true for both procurement catalog items and non-catalog items.

    -   Any child amounts on a referenced purchase requisition, such as discounts, charges, or taxes, will not be reflected on the general budget reservation line.

7.  If you use project accounting, on the Line details section, click the Project tab, and then fill out the fields as necessary.

    -   If you use project accounting, on the General budget reservation lines section, click Committed costs. The Committed costs page opens, displaying the committed costs related to the selected line.

8.  When you are finished filling out the header and line values, either **Submit to workflow** or click **Post** (dependent on your setup).
