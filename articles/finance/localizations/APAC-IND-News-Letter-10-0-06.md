---
# required metadata

title: APAC-IND-Newsletter-10-0-06
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-06
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

# Welcome to the newsletter for version 10.0.6! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.06 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-6)

# New Features
## Validate non-existing and duplicate records when importing tax setup 
During the process of importing tax setup, system will validate the data correctness for the master data like HSN, SAC, etc., 
and the data duplication. Duplicate data means the lookup records which result in the same tax rate, load on inventory %, etc. 
It can be turned on in feature management workspace.

![](media/Validating Non-Existing10.0.6.png)

## Tax information enabled for “Procurement Category”

![](media/Procurement Category-10.0.6.png)
 
## Enable multi-batch processing for GSTR reports

1.Turn on the multi-batch processing feature

Workspaces > Feature management, and turn on the Enable multi-batch processing for GSTR reports feature

2.Generate a GSTR report

Tax > Inquiries and reports > Sales tax reports > GER export to GSTR CSV.

3.Get CSV files

Organization administration > Electronic reporting > Electronic reporting jobs. 
Select the comma-separated values (CSV) files that you want.
For example, select GER export to GSTR CSV__Merged. This file is generated as a merged file. 

![](media/Enabled Multiple batch processing-10.0.6.pngg)

### Document link : 

(https://docs.microsoft.com/en-us/dynamics365/finance/localizations/apac-ind-gst-multi-batch-processing-gstr-return)

# Critical Fixes 

-	Unable to view the transaction ID in posted tax document transaction and posted tax component transaction after adding column.   
-	Accounting entry issue on import Purchase order invoicing when invoice is posted with reference to product receipt Quantity scenarios.
-	Indian legal entity customer invoicing takes too long time.   
-	Base amount should not be "Zero" for sales order when exempt check box is marked   
-	CGST & SGST should be applicable for intra-state transfer order in case the GST registration number are different in two warehouses .
-	TDS is not working for customer with TDS threshold enabled.   
-	Reversal of invoice Journal posted with TDS display incorrect total invoice amount .  
-	Withholding Tax (TDS) threshold not working correctly in normal TDS deduction scenario    
-	Wrong TDS calculation in open vendor invoice screen   
-	Incorrect calculation of GST for Credit note   

# Upcoming critical fixes in 10.0.7 

- Multiple copies print using Print management not working for Sales Invoice report  
-	Importing Customer free text invoice not updating for India legal entity  
-	Data not coming in Tax Transaction inquiry for TDS if TDS settlement period character length is more than 10 characters  
-	Transaction posted through Tax journal not showing in vendor open transaction for settlement  
-	System is not considering threshold defined in Withholding Tax  
-	Incorrect calculation of GST for Credit note  
-	Wrong TDS Calculation in Open Vendor invoice screen  
-	The field ‘Business verticals’ for the GST registration number in the " Enterprise Tax Registration Numbers "  
  form should be editable and not greyed out  
