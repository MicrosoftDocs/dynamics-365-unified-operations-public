---
# required metadata

title: Cash discounts
description: Cash discounts are setup and shared for Accounts payable and Accounts receivable.  The cash discount available can be defined on the customer invoice or vendor invoice, and will be taken if the invoice is paid within the cash discount date. 
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 21 - 10 - 56
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CashDisc
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 3741
ms.assetid: c25f9d85-2702-46aa-8e61-0b4886e069b3
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Cash discounts

Cash discounts are setup and shared for Accounts payable and Accounts receivable.  The cash discount available can be defined on the customer invoice or vendor invoice, and will be taken if the invoice is paid within the cash discount date. 

Cash discounts
--------------

Cash discounts for both customers or vendors can be created in the Cash discounts page. You can also define, by using the Next discount code field, a series of cash discounts that succeed each other as previous cash discount dates expire. For more information, see “Example: Series of cash discounts” later in this topic. If the invoice, credit transaction (either a payment or a credit note), or both are entered in a currency other than the accounting currency of the legal entity, the cash discount is calculated using the exchange rate based on the date of the payment or credit note. If the invoice and credit document are entered in different legal entities, and if the accounting currencies for the legal entities differ, the exchange rate is taken from the legal entity of the invoice, as of the date of the credit document. For more information, see “Example: Exchange rates for cash discounts” later in this topic.
Defaulting order of cash discount main account
----------------------------------------------

If an invoice is settled in time to obtain a cash discount, the cash discount is automatically posted to a cash discount main account according to the following defaulting priority:
1.  The main account specified in the Alternative cash discount account field on the customer Settle open transactions page or the vendor Settle open transactions page.
2.  The main account specified in the Customer cash discount field or the Vendor cash discount field of the ledger posting group that is assigned to the sales tax code of the invoice. Set up ledger posting groups on the Ledger posting groups page and assign them to sales tax codes in the Sales tax codes page.
3.  The main posting account on the Cash discounts page in either the Main account for customer discounts field or the Main account for vendor discounts field for the cash discount code that is on the settled invoice.
4.  The main account for cash discounts, as defined in the Accounts for automatic transactions page.

## Example: Series of cash discounts
Set up three cash discount codes as follows:
-   Code 5D10% – A cash discount of 10% when the amount is paid within 5 days.
-   Code 10D5% – A cash discount of 5% when the amount is paid within 10 days.
-   Code 14D2% – A cash discount of 2% when the amount is paid within 14 days.

In the Next discount code field:
-   For the 5D10% code, select 10D5%.
-   For the 10D5% code, select 14D2%.
-   For the 14D2% code, leave the Next discount code field blank.

The three cash discounts succeed each other as the payment date exceeds the previous cash discount date on the invoice. Only one cash discount is granted when the invoice is paid, based on which cash discount date is meet in the sequence of cash discounts.

## Example: Exchange rates for cash discounts
Your legal entity’s accounting currency is EUR and the following exchange rates are specified for USD:
-   February 1 = 110
-   March 1 = 80

An invoice for 1000 USD with cash discount terms of 20D2% is posted on February 15. The accounting currency amount of the invoice is 1100 EUR. A payment for 980 USD is settled with the invoice on March 1. The cash discount amount is 20 USD. The accounting currency amount of the payment is 784 EUR. The accounting currency amount of the cash discount is calculated by using the exchange rate as of March 1: 20 \* 80 / 100 = 16 EUR.
| **Note**                                                                                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If the Calculate cash discounts for partial payments option is selected in the Accounts receivable parameters or Accounts payable parameters pages, the exchange rate that is in effect on the date of each partial payment is used. |

 
=

 

