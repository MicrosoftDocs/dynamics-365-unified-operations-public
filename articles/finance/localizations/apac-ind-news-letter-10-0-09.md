---
# required metadata

title: What's new and changed for APAC India GST Localization in 10.0.09 (April 2020)
description: This topic describes new and changed functionality for APAC India GST features released in Dynamics 365 Finance version 10.0.09.
author: prabhatb
manager: Wangcheng
ms.date: 06/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
[!include [banner](../includes/banner.md)]

# What's new and changed for APAC India GST Localization in 10.0.09 (April 2020) 

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.09 for APAC India GST localization.

## New features
### Charge allocation in sales order  
You can now include charge allocations on all sales order lines. To enable this feature, go to the **Feature management** workspace and enable the feature, **Charges allocation on a sales order**.

On the sales order header, you can select **Assessable value** on charge line. Based on this selection, the distributed charge value is added to line item taxable value. The taxes are then calculated accordingly.

### Default a customer business address on tax information 

This feature will default a customer's business address on the **Tax information** tab of a sales transaction, and the company address
on the **Tax information** tab of a direct delivery purchase order. To enable this feature, go tothe **Feature management** workspace, and enable the feature, **Defaulting of customer business address in the tax information tab**.

By using direct delivery functionality, you can create deliveries directly from vendors to customers, reducing delivery time and order administration. During direct delivery, when a purchase order is created, the customer delivery address defaults from the **Sales order** page. However from the GST prospective, the customer's business address should default in tax information. 

### New GSTR return offline tool (Trial Version Prototype) for India in Dynamics 365 Finance 

Under a new GSTR return process, GST ANX-1 (Annexure of supplies) and GST ANX-2 (Annexure of Inward Supplies) will be filed as part of FORM GST RET-1 (Normal) returns. You can generate several GSTR returns.

![](media/GST-new-GSTR-offline-tool-3-10-0-09.PNG)

For more information about the GSTR Return offline tool report, see the KB article, [New GSTR Return offline tool (Trial Version Prototype) for India in Dynamics 365 Finance](https://support.microsoft.com/help/4549665). 

### GTE debug mode
Sometimes tax can't be calculated or posted properly after you extend the GST configuration. If you change the data model,
there may be discrepancies between the inputs from Dynamics 365 Finance and the GTE. If you update posting profiles, 
you might encounter posting imbalance issues. It can be time consuming to troubleshoot these issues.

With debug mode enabled, the system will dump a log file that contains the discrepancies between the input fields from Dynamics 365 Finance and the GTE, and the posting profile. 

1. Append &debug=vs%2CconfirmExit& to D365 AOS URL and press Enter to open a new session.

![](media/GST-debug-mode-4-1-10-0-09.PNG)

2. Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup** and mark the **Check model mapping discrepancies** parameter.
3. Calculate the tax for the transaction , and then select **Save** to save the **GTETroubleshotingLog.txt**.
4. Provide the file to Microsoft for investigation.
 
## Critical fixes 

- Business address is not updated automatically by system in tax information field while crating Sales order .
-	While generating "Free text invoice" from legal entity system throw error " Something went wrong while generating the request" 
-	Tax is not getting calculated when we import the data through data entity files. 
-	System is generating normal sales order invoice instead of GST tax invoice when tax value become zero. 
-	GSTR-2 - "Is reverse charge applicable value is wrong 
-	Fixed Assets value not updated with load on inventory amount when import order invoice with service item. 
-	GTE set off hierarchy version not get the latest version 
-	Journal voucher description truncation issue for GST transaction. 
-	Stock transfer order shipment voucher is not showing in GSTR-2 Report 
-	Direct Delivery Purchase order , customer address getting flow in tax information 
-	GSTIN registration numbers are TDS  registration number are not sharing with the other legal entities while 
  importing from the data management module even after sharing option enable . 
-	GST tax amount is deducted twice from the sale of assets net amount when price inclusive tax option enabled.
-	System is throwing error " Object reference not set to an instance of an object" while settling the vendor invoice transactions. 
-	In Purchase order invoice HSN/SAC numbers are not populating from PO when selecting PO using "+" sign 
  (Used for booking consolidated invoices) 
-	List all posting profile in GTE trouble shooting file when enabled debug mode. 
-	Transfer order posting not picking up IGST account .


## Upcoming critical fixes in 10.0.10 

- Import order-over-delivery setup respected at invoice registration stage 
-	Enable date time tracking for tax run time lookup condition table 
-	Transaction type not showing in case of Tax Journal posting 
-	Unable to generate recurring invoice as getting the error message " The menu item with name customer recurrence 
  invoice service operation could not be opened" . 
-	Tax calculation is wrong when post customer discount through general Journal 
-	Adjusted amount origin field showing wrong value. 
-	Difference between sales tax payment and actual transaction posted to tax authority .
