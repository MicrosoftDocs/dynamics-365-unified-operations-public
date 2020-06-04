---
# required metadata

title: APAC-IND-Newsletter-10-0-07
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-07
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

# Welcome to the newsletter for version 10.0.7! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.07 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-7)

# New Features
## Create tax component with pre-defined rules 

It enables the user to create a new component with pre-defined rules which support GST behaviors including non-deductible, 
reverse charge for purchase and sales. With this feature, users do not need to create tax component from scratch, 
like add tax measures, configure tax calculation formula, configure tax posting profile, etc. 

You can enable the feature in feature management workspace, feature name is "Enable creating tax component with pre-defined rules"

 ![](media/GST-Tax- component-Pre-defined-rule-1-10-0-07.PNG)
 
 With the feature enabled, there are several controls enabled in the dialog box, you can use them to control the behavior 
 of the tax component. Refer (https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tax-engine-create-tax-component)
 for details.
 
 ![](media/GST-Tax- component-Pre-defined-rule-1-10-0-07.PNG)
 
# Critical Fixes 

- Multiple copies using print management not working for Sales Invoice Report 
-	Invoice address is not defaulting in customer tax information in Time-sheet 
-	Data Importing of customer Free text invoice not updating for Indian legal entity. Actually data is not displayed on 
  the interface for legal entity that below to country/Region IND. 
-	Transaction posted through tax journal not showing in vendor open transaction for settlement 
-	Sales tax settlement may have an update conflict when same "TaxsalesTaxpaymentHistory" detail gets updated multiple times. 
-	Incorrect Withholding tax (TDS/TCS) posting in reporting currency when exchange rate is changed at the time of payment 
  with settle transaction function for foreign vendor transaction. 
- Incorrect calculation of GST for Credit Note 
-	Line imported using the "VendorInvoiceLine"  entity are not visible in the pending vendor invoice form in India entity. 
-	The Field business verticals for the GST registration numbers form should be editable at any time and this field should
  not be greyed out. 


# Upcoming critical fixes in 10.0.8 

- Tax amount showing in Purchase order totals and Purchase Invoice total even the transaction is posted
  with 100%  Reverse charge basis. 
-	TDS transactions are not updated in withholding tax transaction (TDS/TCS)  report when settled Prepayment with Invoice. 
-	Assessable value is not getting updated after removing charge code form the PO Invoice line. 
-	Change of vendor in Purchase Requisition in not refreshing the vendor tax information in the tax information form 
-	Incorrect FOB (Free on Board) and CIF (Cost , insurance and freight)  calculation in export sales order . 
-	Assessable value is not updated correctly in vendor invoice form when Post changes are incorporated in "Excel import file" 
  and published into Dynamics 365
