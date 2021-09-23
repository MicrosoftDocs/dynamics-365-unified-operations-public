---
# required metadata

title: What's new or changed for India GST in 10.0.09 (April 2020)
description: This topic describes new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.09.
author: prabhatb
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# What's new or changed for India GST in 10.0.09 (April 2020) 

[!include [banner](../includes/banner.md)]

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.09 for India GST localization.

## New features
### Charge allocation in sales order  
You can now include charge allocations on all sales order lines. To enable this feature, go to the **Feature management** workspace and enable the feature, **Charges allocation on a sales order**.

![Action Pane.](media/GST-charge-allocation-1-10-0-09.PNG )

On the sales order header, you can select **Assessable value** on the charge line. Based on this selection, the distributed charge value is added to line item taxable value. The taxes are then calculated accordingly.

### Default a customer business address on tax information 

This feature will default a customer's business address on the **Tax information** tab of a sales transaction, and the company address
on the **Tax information** tab of a direct delivery purchase order. To enable this feature, go to the **Feature management** workspace, and enable the feature, **Defaulting of customer business address in the tax information tab**.

![Feature management - Defaulting of customer business address in the tax information tab.](media/GST-customer-business-address-2-10-00-09.png )

By using direct delivery functionality, you can create deliveries directly from vendors to customers, reducing delivery time and order administration. During direct delivery, when a purchase order is created, the customer delivery address defaults from the **Sales order** page. However from the GST prospective, the customer's business address should default in tax information. 

### New GSTR return offline tool (trial version) for India in Dynamics 365 Finance 

Under a new GSTR return process, GST ANX-1 (Annexure of supplies) and GST ANX-2 (Annexure of Inward Supplies) will be filed as part of FORM GST RET-1 (Normal) returns. You can generate multiple GSTR returns.

![Report configurations.](media/GST-new-GSTR-offline-tool-3-10-0-09.PNG )
For more information about the GSTR Return offline tool report, see the KB article, [New GSTR Return offline tool (Trial Version Prototype) for India in Dynamics 365 Finance](https://support.microsoft.com/help/4549665). 

### GTE debug mode
Sometimes tax can't be calculated or posted properly after you extend the GST configuration. If you change the data model,
there may be discrepancies between the inputs from Dynamics 365 Finance and the GTE. If you update posting profiles, 
you might encounter posting imbalance issues. It can be time consuming to troubleshoot these issues.

With debug mode enabled, the system will generate a log file that contains the discrepancies between the input fields from Dynamics 365 Finance and the GTE, and the posting profile. 

1. In the internet address bar, change **&debug=vs%2CconfirmExit&** to your Dynamics 365 Finance AOS URL and press Enter to open a new session.

![Dynamics 365 Finance AOS URL.](media/GST-debug-mode-4-1-10-0-09.PNG )

2. Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup** and mark the **Check model mapping discrepancies** parameter.

![Tax parameters setup.](media/GST-debug-mode-4-2-10-0-09.PNG )

3. Calculate the tax for the transaction, and then select **Save** to save the **GTETroubleshotingLog.txt** file.

4. Submit the file to Microsoft for investigation.
 
## Critical fixes 

- Business address is not updated automatically by the system in the **Tax information** field when a sales order is created.
-	When generating a free text invoice from a legal entity, the following error occurs, "Something went wrong while 
  generating the request". 
-	During data import through data entity files, tax is not calculated. 
-	The system generates a typical sales order invoice instead of the GST tax invoice when the tax value becomes zero. 
-	GSTR-2 **Is reverse charge applicable** value is incorrect. 
-	Fixed assets value is not updated with the **Load on inventory amount** when import order invoice with service item. 
-	GTE set off hierarchy version does not get the latest version. 
-	Journal voucher description truncation issue for GST transaction. 
-	Stock transfer order shipment voucher is not showing in the **GSTR-2** report.
-	With direct delivery for a purchase order, the customer's address is included in the customer's tax information. 
-	GSTIN registration numbers and TDS registration numbers are not shared with the other legal entities when data is imported from the **Data management** module even after sharing is enabled. 
-	GST tax amount is deducted twice from the sale of assets net amount when **Price inclusive tax** is enabled.
-	When a vendor invoice is settled, the following error occurs, "Object reference not set to an instance of an object". 
-	HSN/SAC numbers are not populating from the purchase order to the purchase order invoice when the selected purchase order 
  uses a plus (+) sign. (This sign is used for booking consolidated invoices.) 
-	All posting profiles are listed in the GTE troubleshooting file when debug mode is enabled. 
-	Transfer order posting isn't picking up the IGST account.


## Upcoming fixes in 10.0.10 

- Import order-over-delivery setup is respected at the invoice registration stage. 
-	Enable date time tracking for the **Tax run time lookup condition** table.
-	Transaction type not showing when the **Tax Journal** is posted. 
-	Recurring invoices can't be generated and an error occurs. 
-	Tax calculation is incorrect when a customer discount is posted in the **General** journal. 
-	**Adjusted amount origin** field shows the wrong value. 
-	Difference between sales tax payment and the actual transaction posted to the tax authority.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]