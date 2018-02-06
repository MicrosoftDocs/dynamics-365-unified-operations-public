---
# required metadata

title: Set up GST reference number groups
description: This article walks you through setting up GST reference number groups for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: ShylaThompson
manager: AnnBe
ms.date: 02/06/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: shylaw
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.scope: Core, Operations
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 7.3.1
ms.search.validFrom: 2018-1-31
---


# Set up GST reference number groups

[!include[banner](../includes/banner.md)]

GST transactions are differentiated with a unique number sequence. If different number sequences are required for each warehouse or legal entity addresses, you can create a reference number sequence group and assign the reference number sequence group to the addresses.

The following steps demonstrates how to create the GST reference number group and assign to the addresses.

1.	Go to **Tax** > **Setup** > **Sales tax** > **India** > **GST reference number sequence group**.
2.	Click **New**.
3.	Enter a name and a description.
4.	On the **Details** FastTab, define number sequences for the references. Refer to the following table for additional information about each reference.

| **Source**          | **Reference**            | **Description**                                                                                                                                                                               |
|---------------------|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Accounts receivable | Bill of supply           | The **Bill of supply** number sequence will be used when customer sales that have non-GST transactions are posted.                                                                            |
| Accounts receivable | Debit/Credit note        | The **Debit/Credit note** number sequence will be used when customer debit or credit sales that have GST transactions are posted.                                                             |
| Accounts receivable | Revised invoice          | The **Revised invoice** number sequence will be used when customer revised sales invoice with reference to the existing invoice, that have GST transactions are posted.                       |
| Accounts receivable | Advanced receipt voucher | The **Advance receipt voucher** number sequence will be used when customer advance receipt transactions that have GST transactions are posted.                                                |
| Accounts receivable | Advanced refund voucher  | The **Advance refund voucher** number sequence will be used when customer advance refund transactions that have GST transactions are posted.                                                  |
| Accounts receivable | GST invoice              | The **GST invoice** number sequence will be used when customer sales that have GST transactions are posted.                                                                                   |
| Accounts receivable | Export order             | The **Export order** number sequence will be used when customs export order transactions are posted.                                                                                          |
| Accounts payable    | Debit/Credit note        | The **Debit/Credit note** number sequence will be used when vendor debit or credit purchase that have GST with reverse charge transactions are posted.                                        |
| Accounts payable    | Revised invoice          | The **Revised invoice** number sequence will be used when vendor revised purchase invoice with reference to the existing invoice, which have GST with reverse charge transactions are posted. |
| Accounts payable    | Advanced payment voucher | The **Advance payment voucher** number sequence will be used when vendor advance payment transactions that have GST transactions are posted.                                                  |
| Accounts payable    | GST invoice              | The **GST invoice** number sequence will be used when vendor purchase that have GST with reverse charge transactions are posted.   |  
