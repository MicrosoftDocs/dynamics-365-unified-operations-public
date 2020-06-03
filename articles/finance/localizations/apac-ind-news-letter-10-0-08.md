---
# required metadata

title: APAC-IND-Newsletter-10-0-08
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-08
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

# Welcome to the newsletter for version 10.0.8! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.08 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-8)

# New Features
## Enable users to change tax rate type in purchase invoice 
In India, the invoice received from the supplier may have different tax rates from the purchase order. 
Now it is supported by tax rate type (please refer to the newsletter of 10.0.5).
 
You can enable the feature in feature management workspace, feature name is "(India) Enable changing tax rate type in purchase invoice "

![](media/Change rate tax type-10.0.8.png)
 
With the feature enabled, you can update the tax rate type in the tax information of purchase invoice, 
so you can apply different tax rate.

![](media/Change rate tax type-II-10.0.8.png)

## Data consistency check

Now you can check/fix some data inconsistency issue regards GTE, go System administration->Periodic tasks->Database->Consistency check.
We highly recommend you to run this in your environment.

![](media/Data consistency check-10.0.8.png)

## GST number sequence issue

Recently, we’ve observed several customers encountered posting failure due to missing/incorrect setup of GST number sequence. 
The error message like “Posting results for journal batch number ### Error: Number sequence group: "###", 
transaction type: "Debit/Credit note" has not been set up for the GST reference number sequence group of tax information "###".” 
In order to resolve the issue, please follow (https://docs.microsoft.com/en-us/dynamics365/finance/localizations/apac-ind-gst-define-gstin-numbers-number-sequences)  
and (https://docs.microsoft.com/en-us/dynamics365/finance/localizations/apac-ind-gst-reference-groups)
to setup the GST number sequence correctly.

# Critical Fixes 

- Tax amount showing in Purchase Order totals and Purchase Invoice totals even the Reverse charge mechanical is applied 100%.
- In Purchase Order after defining the tax information, we are not able to see the tax account lines in view distribution form. 
-	TDS transaction not updated in withholding tax transaction reports when settled invoice with prepayment. 
-	Assessable value not getting updated after removing charge code from the Purchase Order invoice line. 
-	Charge of vendor in Purchase requisition is not refreshing the vendor information in tax information .
-	Incorrect FOB and CIF calculation in export sales order . 
-	Assessable value is not updated correctly in vendor invoice form when excel file  imported through data entity.


# Upcoming critical fixes in 10.0.9 

- Free text invoice print not working for Non-GST Invoices. 
-	Tax is not getting calculated when we import the data through data entity file. 
-	While generating Free Text invoice from Indian company, system throw error . 
-	System is generating normal Sales order invoice instead of GST tax invoice when tax value become zero. 
-	GSTR-2 column "Is Reverse charge applicable" value is updating wrong. 
-	Tax code lookup filter option unavailable in tax configuration .
-	GTE set off hierarchy version not get the latest version. 
-	Journal voucher description transaction issue for GST transaction 
-	Tax settlement - Change in hierarchy  of tax settlement components as per govt. notification.
