---
# required metadata

title: APAC-IND-Newsletter-10-0-05
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-05
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

# Welcome to the newsletter for version 10.0.5! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.05 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-5)

# New Features
## New Configuration 
The following configurations, which you can get from Shared Asset Library in LCS and use it in version 10.0.5, are available. You can also find all the released configuration with details here: https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/apac-ind-gst.
 
- Taxable Document.version.82.xml
- Taxable Document (India).version.82.143.xml
- Tax (India GST).version.82.143.263.xml 
 
It provides following features or fixes:
- Solve the issue of zero tax based issue for tax exempt transaction
- Support CGST&SGST for intra-state stock transfer order between warehouses with different GST registrations 
- Support VAT for Non-GST items
- Enable tax rate type
 
In most of the taxation system, there is concept of tax rate type, like standard tax rate, reduced tax rate, super reduced tax rate, etc. 
In India GST, there are following five slabs: 
| Rate       | Type             | Products                                                                                                                                                                                                             |
|------------|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     0%     |     Nil          |     Basic foods, including: fish, meat, dairy, vegetables, bread,   salt. Postal services. Books and newspapers. Accomodiation below Rs 999 per   night                                                              |
|     5%     |     Low          |     Household necessities such as edible   oil, sugar, spices, tea, and coffee (except instant) are included. Coal   , Mishti/Mithai (Indian Sweets) and Life-saving drugs are also covered under   this GST slab    |
|     12%    |     Standard1    |     This includes computers and processed food                                                                                                                                                                       |
|     18%    |     Standard2    |     Hair oil, toothpaste and soaps, capital goods and industrial     intermediaries are covered in this slab                                                                                                         |
|     28%    |     High         |     Luxury items such as small cars , consumer durables like AC and   Refrigerators, premium cars, cigarettes and aerated drinks , High-end   motorcycles  are included here.                                        |

Now you can associate the Tax Rate Type to Released Product, Procurement/Sales categories and Charge code.

![](media/Tax rate type-10.0.5.png)

Then use Tax Rate Type to determine the tax rate. It will dramatically reduce the number of record of tax setup data.

![](media/Tax rate type-II-10.0.5.png)

For Retail customers who have terminals not updated to 10.0.5, please use following configurations instead. The only difference compare to the 
above one is it does not support tax rate type. 

- Taxable Document.version.82.xml
-	Taxable Document (India).version.82.143.xml
-	Tax (India GST).version.82.143.264.xml 

## Improve the performance of GTE calculation by "Skip model mapping"

This feature was released in 10.0.2 . Now providing more details on it. If you are using Microsoft's standard configuration or you extend only the tax document,
you can skip the model mapping which will improve the performance of tax calculation and posting.

![](media/Skip model mapping-10.0.5.png)

## Support calculate/adjust tax in accounting currency
This feature was released in App AX 10.0.3 . Now providing more details on it. User can adjust actual tax amount in accounting currency for import/export
order to mitigate difference for custom duty

### How to enable : Tax -> Setup -> Tax Configuration -> Tax Setup -> Parameter

![](media/Adjust Tax as accounting currency-10.0.5.png)

![](media/Adjust Tax as accounting currency-II-10.0.5.png)

## Financial dimension linked to the inventory dimension site is not auto-populated in stock transfer receipt order line

  This feature was released in AppAX10.0.4. We are providing more details on this feature for better understanding. 
 
  When user activate the financial dimension link, the following occurs in stock transfer order :
 
- The financial dimension value that is specified for the site is default as the financial dimension value for 
  the respective site in stock transfer order .
- User can change the dimension value for the financial dimension before posting stock transfer shipment and receipt .
  However if user lock the financial dimension Link than user cannot modify the financial dimension value 
  that is associated with a site
- Defaulting of financial dimension in stock transfer orders will be based on standard functionality of 
  financial dimension is association with the site inventory dimension

## Process Flow : 

1.Click Inventory management > Setup > Posting > Dimension link.

2.In the Reference field, select the financial dimension to link to the site inventory dimension.

3.Click Sites to open the Sites form. The financial dimension that user selected in the Reference field is displayed 
  on the Financial  dimensions Fast Tab,where user can also select a financial dimension value for the dimension.

4.Select a site > On the Financial dimensions Fast Tab, select a financial dimension value. The specified financial
  dimension value is associated with the selected site.

5.Repeat this step for each site.

6.Create stock transfer order Inventory management > Outbound Orders>Transfer Order >Stock transfer order 

7.On Stock order line Click Financial dimension tab > Line details > Default financial dimension. 

## Simplified way to address Reverse charge transaction  as per govt. Clarification  – A general guidance  

 With few changes in the released standard configuration Reverse charge feature can be made simple for accounting prospective . 
 
 " As govt clarified that RCM on reverse charge transaction can be claimed in the same   month in which it is paid " refer below link : 
 
(https://twitter.com/askGST_GoI/status/897360102964944896)
 
 Based on above clarification user can make following changes in the configuration : 
 
 - Instead of posting GST tax in Interim recoverable at the time of posting purchase invoice ,
   Post GST input tax directly in "Tax Recoverable account" 

### Steps :

- Create new posting account "Tax payable reverse charge" 

![](media/Tax payable reverse charge-10.0.5.png)

![](media/Tax payable reverse charge-II-10.0.5.png)

- Identify Reverse charge liability in separate account such as " Tax Payable (Reverse charge)" which should be defined as "Ledger account" instead of "Tax account" because Reverse charge liability cannot directly settled with input tax credit . It must be paid separately first from the "Cash Ledger account" .
 
###	Steps : 

### Under Posting :
- Tax measure – Interim recoverable  
- Debit : Tax Recoverable 
- Credit : Interim Tax payable 
### Vendor payment : 
- Tax measure – Interim Recoverable account
- Debit : Interim Tax payable 
- Credit : Tax payable reverse charge 

- Settle Reverse charge liability from cash account on the last day of the month in which reverse charge liability was created. 

# Critical Fixes 

- TDS not deducted correctly when invoice is settled with prepayment .
-	Save tax document in purchase order confirmation form so tax document form can be opened after posting.
-	Same exchange rate is not picked in tax document in the BOE form and Import invoice/product receipt if the 
  date is not the same for both document. 
-	Tax information is flowing from customer history 
-	when financial dimension is defined for the ledger account which is used as offset account for vendor 
  transaction. During withholding tax settlement with TDS authority error message is appearing.
-	TDS amount showing incorrect in Vendor transaction when TDS amount is adjusted to "Zero" 
-	Open Vendor Invoice line disappears on save.
-	When Partial invoice against the purchase receipt quantity , the assessable value is not getting updated 
  and in turn GST is not getting calculated. 
-	Load on inventory amount not posting to Fixed asset account when doing fixed asset acquire through purchase order with Service item.
-	Location ID of legal entity IN is not defaulting in project timesheet.
-	Tax is not populated in Invoice journal inquiry form.
-	Shipping bill cannot post when user set Default values for summary update = 'Invoice account'
-	GST amount and Assessable value should not be rounded by Currency > Sales orders > Rounding rule.
-	The totals in the GST tax invoice (shipment) are not getting displayed correctly.
-	Vendor Tax Information missing in Purchase order line when Purchase order created from Purchase requisition.
-	Tax document not get refreshed when transaction date being updated for vendor invoice.
-	Free text invoice not posting with terms of payment as cash on delivery payment term and GST


# Upcoming critical fixes in 10.0.6 

- Accounting entry issue on Import PO invoicing (along with BOE feature) when invoice is posted with reference 
  to product receipt quantity .
-	TDS is not working for customer with TDS Threshold enabled
-	Taxable value in the GSTR1 offline report does not match ‘The invoice amount in the accounting currency’ on the 
  Invoice Journal form for an Export order. 
- Unable to view the Transaction ID in Posted Tax document transactions and  posted Tax component transactions after adding  column.
-	Base amount should not be 0 for sales order when transaction line is marked as exempt tax
-	Reversal of Invoice posted with TDS showing a wrong display issue in total invoice amount
 
