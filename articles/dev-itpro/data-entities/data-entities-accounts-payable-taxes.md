---
# required metadata

title: Data entities - Accounts payable and taxes
description: This article provides a list of the data entities that are available for Accounts payable and taxes.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 96193
ms.assetid: 9935fcf2-a497-4c19-a3a8-c1ed259a965c
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Accounts payable and taxes

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for Accounts payable and taxes.

Available data entities
-----------------------

**10.1.001 AP – AP and AR shared setup**

| Suggested sequence | Entity name            | Area             | Entity type | Dependency       | Comments                                                                                                                                  |
|--------------------|------------------------|------------------|-------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Payment day lines      | Accounts payable | Setup       | None             |                                                                                                                                           |
| 2                  | Cash discount          | Accounts payable | Setup       | None             | Define cash discounts, which can apply to either customers or vendors.                                                                    |
| 3                  | Payment schedule       | Accounts payable | Setup       | None             | Define payment schedules, which you can use to schedule installment payments from customers and to vendors.                               |
| 4                  | Payment schedule lines | Accounts payable | Setup       | Payment schedule | Define payment schedules, which you can use to schedule installment payments from customers and to vendors.                               |
| 5                  | Terms of payment       | Accounts payable | Setup       | None             | Define default payment terms that can be used for all vendors, and for related purchase agreements, purchase orders, and vendor invoices. |
| 6                  | Delivery charges group | Accounts payable | Setup       | None             | Define charges group for modes of delivery.                                                                                               |
| 7                  | Terms of delivery      | Accounts payable | Setup       | None             | Define the terms of delivery that are used by the company accounts, customers, and vendors.                                               |
| 8                  | Line of business       | Accounts payable | Setup       | None             | Define the line of business codes that you assign to vendors or customers on the Vendors page or the Customers page.                      |

**10.1.002 AP – Vendor payment setup**

| Suggested sequence | Entity name                         | Area             | Entity type | Dependency | Comments                                                                            |
|--------------------|-------------------------------------|------------------|-------------|------------|-------------------------------------------------------------------------------------|
| 9                  | Vendor payment fee                  | Accounts payable | Setup       | None       | Define payment fees that are related to vendors, such as fees for promissory notes. |
| 10                 | Vendor payment method               | Accounts payable | Setup       | None       | Define information about methods of payment for vendors.                            |
| 11                 | Vendor payment method specification | Accounts payable | Setup       | None       | Define payment specification codes for the method of payment.                       |

**10.1.003 AP – Vendor attributes**

| Suggested sequence | Entity name                  | Area             | Entity type | Dependency | Comments                                                                                                                                    |
|--------------------|------------------------------|------------------|-------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| 12                 | Price vendor groups          | Accounts payable | Setup       | None       | Define price groups that can be used to specify a set of prices that should apply to a group of vendors.                                    |
| 13                 | Total discount vendor groups | Accounts payable | Setup       | None       | Define vendor total discount groups that can be used on trade agreements.                                                                   |
| 14                 | Line discount vendor groups  | Accounts payable | Setup       | None       | Define vendor line discount groups that can be used on trade agreements.                                                                    |
| 15                 | Buyer groups                 | Accounts payable | Setup       | None       | Define buyer groups to associate vendors with employees and items.                                                                          |
| 16                 | Purchase pools               | Accounts payable | Setup       | None       | Define purchase order pools. You use purchase pools to group purchase orders, and for filtering and selection purposes.                     |
| 17                 | Destination code             | Accounts payable | Setup       | None       | Define destination codes. You can use destination codes to divide destinations into zones.                                                  |
| 18                 | Reasons                      | Accounts payable | Setup       | None       | Define financial reason codes. Reason codes help explain why some types of transactions were entered or why some field values were changed. |
| 19                 | Vendor exception groups      | Accounts payable | Setup       | None       | Define groups that can be assigned to vendors who are exempt from invoice validation rules.                                                 |
| 20                 | Business segments            | Accounts payable | Setup       | None       | Define general business segments that you can use to categorize prospects.                                                                  |
| 21                 | Business subsegments         | Accounts payable | Setup       | None       | Define precise types, or subsegments, for each business segment.                                                                            |
| 22                 | Vendor charges group         | Accounts payable | Setup       | None       | Define charges groups for vendors.                                                                                                          |
| 23                 | Modes of delivery            | Accounts payable | Setup       | None       |                                                                                                                                             |


