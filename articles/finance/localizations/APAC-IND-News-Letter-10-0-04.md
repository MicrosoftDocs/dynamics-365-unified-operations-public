---
# required metadata

title: APAC-IND-Newsletter-10-0-04
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-04
author: prabhatb
manager: Wangcheng
ms.date: 05/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
[!include [banner](../includes/banner.md)]

# Welcome to the newsletter for version 10.0.4! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.04 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-4)

# New Features
## Define GST reference number sequence group

User can define separated GST reference number sequence group for Free Text Invoice, Stock transfer receipt and Stock transfer shipment. 
 
 ![](media/GST Reference number sequence-10.0.4.png)
 
 ## Financial dimension linked to the inventory dimension site will be auto-populated in stock transfer receipt order line
 

# Critical Fixes 

- Total transaction value in GSTR2 is incorrect for multi-line invoice journal with both debit and credit ledger line
-	Performing Settle and Post Sales tax are not hitting Vendor account
-	Tax is not getting calculated in return order
-	GST Registration ID is not updated after changing the delivery address in purchase order
-	Project adjust transactions is not working properly
-	Financial dimensions are not updated for GST ledger after posting project invoices
-	Proforma Invoices consumes number from invoice number sequence


# Upcoming critical fixes in 10.0.5 

- TDS not deducted correctly when invoice is settled with prepayment
-	Calculated GST is not getting posted to Expense Account in case of SAC code selected with ITC category as “Others”
-	Charge Allocation in sales lines proportionally as per GST regulation change
-	Save tax document in purchase order confirmation so tax document form can be opened after posting
-	IGST not calculating on SEZ purchase
-	Partial invoice against the purchase receipt quantity, assessable value is not getting updated and GST is not getting calculated 
-	Load on inventory amount not posting to Fixed asset account when doing fixed asset acquire through purchase order
