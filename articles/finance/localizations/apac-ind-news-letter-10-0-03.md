---
# required metadata

title: APAC-IND-Newsletter-10-0-03
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-03
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

# Welcome to the newsletter for version 10.0.3! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.03 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-3)

# New Features
## The document of GST solution is updated 
(https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/apac-ind-gst)

## GSTR report performance improvement
GSTR report generating overall time reduced 30%  by replacing line by line data fetch with dataset operation.
 
## Enable to delete the selected (multiple) tax lookup condition record
Besides delete one single record and delete all records, delete select records is now supported to improve operation efficiency

![](media/Deleted multiple tax lookup-10.0.3.png)

## Enable tax calculation based on accounting currency for import/export order
Refer the [what's new of 10.0.3 ] (https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/whats-new-changed-10-0-3#calculate-tax-in-accounting-currency-for-importexport-order)

![](media/Tax calculation on accounting currency-10.0.3.png	)

## Please use Tax transaction inquiry for TDS/TCS instead of Post withholding tax

# Critical Fixes 

- Create an export order , there are both BCD and SWS, when it's get posted, there is only posting of BCD. 
  Following configuration is needed to solve the issue.
-	Taxable Document.version.81.xml
-	Taxable Document (India).version.81.138.xml
-	Tax (India GST).version.81.138.248.xml
-	GST related accounts are posted without financial dimensions in project invoice proposal
-	Subtotal amount value wrong in adjustment form in settle and post sales tax
-	Adjusted withholding tax origin amount not reflecting in the posted withholding tax enquiry form
-	Project adjust Transactions not working properly 
-	Invoice amount is showing incorrect in Invoice journal report (when posted through invoice journal with TDS)
-	Tax column not updated with tax value in Invoice journal report
-	Delivery address does not autoflow on the tax information form for the SO lines
-	HSN or SAC Code is not editable in tax Information sales return order after delivery 
- Cannot post FTI & confirm PO because of one or more accounting distributions is either over-distributed
-	Assessable value not getting updated in sales order after price group(personalized field) is updated
-	Charges on header level don’t calculate sales tax amount for India entity
-	Invoice number does not come in posted withholding tax inquiry after posting withholding tax adjustment journal


# Upcoming critical fixes in 10.0.4 

- GSTR-2 mismatch in figures when invoice journal is posted with multi-line transaction 
-	Standard sales tax does not get calculated in account payable
-	Proforma invoices consumes number from invoice number sequence. 
