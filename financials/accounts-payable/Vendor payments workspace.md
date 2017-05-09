---
# required metadata

title: Vendor payments workspace
description: The Vendor payments workspace shows you information related to processing vendor payments. There are two views on this 
workspace, including My work and Analytics. My work shows summary tiles, vendor transaction lists and related vendor information. 
The Analytics view utilizes Power BI capabilities to display visuals related to vendor payments.
author: twheeloc
manager: AnnBe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.dyn365.intro: 
ms.dyn365.version:
---

# Vendor payments workspace

[!include[banner](../includes/banner.md)]

# My Work

## Summary tiles

The **Summary** tiles give an overview of the state of your payment information. You can see payment journals that are not yet posted, 
invoices that are past due, all vendors, and vendors that are on hold. From the summary section, you can create a new pay run. 
This information is for the company that you are logged into.

## Vendor transactions tabular lists

In the **Vendor transaction tabular lists** section, a listing of the invoices past due and payments not settled are displayed. 
From the Invoices past due list, navigation to the settlement history for the selected invoice is provided. From the Payments not 
settled list, you can view the settlement history and settle the invoice using the actions located above the list.

Centralized payment clerks are provided with a filter at the top of the Vendor transaction lists that allows the selection of a 
company. The company is filtered to only those companies that are defined within the centralized payment organizational hierarchy 
that the centralized payment clerk has rights to view.

The **Find transactions** capability allows you to search for a vendor transaction.

## Related information

You can view the **Vendor aging** report and the **Payment summary by date** report by using the links provided in the Related 
information section of the workspace.

## Analytics
The Analytics page provides key metrics, such as vendor invoices that are past due and vendor invoices that are due in the future. 
It contains 9 report pages consisting of an overview page and 8 details pages providing details of accounts payable payment metrics.

The following table contains the visualization information.

| Report page                       | Visualization                                                                     |
|-----------------------------------|-----------------------------------------------------------------------------------|
| Vendor payments overview          | Invoices past due 
                                      Invoices due today 
                                      Discounts taken to discounts lost 
                                      Invoices due in future by cash discount date 
                                      Invoices due in future by due date 
                                      Invoices paid late to invoices paid on time 
                                      Payment workflow assignment 
                                      Vendor to customer balance 
                                      Open invoices with payment hold                                                  |
| Invoices past due                 | Invoices due today 
                                      Invoices due today details 
                                      Invoices due today per company 
                                      Invoices due today per vendor group                                              |
| Discounts taken to discounts lost | Discounts taken to discount lost 
                                      Discounts taken to discount lost details 
                                      Discounts taken to discount lost per company 
                                      Discounts taken to discount lost per vendor group                                |
| Invoices due in future            | Invoices due in future 
                                      Invoices due in future details 
                                      Invoices due in future per company 
                                      Invoices due in future per vendor group 
                                      Invoices due in future by cash discount date 
                                      Invoices due in future by due date                                               |
| Invoices paid late                | Invoices paid after due date 
                                      Invoices paid after due date details 
                                      Invoices paid after due date per company 
                                      Invoices paid after due date per vendor group 
                                      Invoices paid late versus invoices paid on time                                  |
| Payment workflow                  | Vendor payment workflow instances 
                                      Vendor payment workflow instances per approver 
                                      Vendor payment workflow instances per company 
                                      Average days in workflow by approver                                             |
| Vendor to customer balance        | Vendor to customer balance 
                                      Vendor to customer balance per company 
                                      Vendor to customer balance details                                               |
| Invoices with payment hold        | Invoices with payment hold 
                                      Invoices with payment hold details 
                                      Invoices with payment hold per company 
                                      Invoices with payment hold per vendor group                                      |

