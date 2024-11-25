---
title: Pay a vendor transaction by endorsing a customer bill of exchange
description: Learn about paying a vendor transaction by endorsing a customer bill of exchange, including a step-by-step process using the JPMF demo data company.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 08/29/2018
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseToVendor, DimensionLookup, LedgerTransVoucher
ms.dyn365.ops.version: Version 7.0.0
---

# Pay a vendor transaction by endorsing a customer bill of exchange

[!include [banner](../../includes/banner.md)]

This task walks you through paying a vendor transaction by endorsing a customer bill of exchange.



Before you can complete this task, you must have at least one bill of exchange with a status of "Drawn".



This task was created using the demo data company JPMF.


## Endorse a customer bill of exchange to a vendor
1. Go to Accounts receivable > Payments > Bill of exchange > Endorse bills of exchange.
2. In the list, find and select the desired record.
    * Select a bill of exchange that has a status of "Drawn".  
3. Click Endorse to vendor to open the drop dialog.
4. In the Date of endorsement field, enter a date.
    * The date cannot be later than the due date of the bill of exchange.  
5. In the Vendor account field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
    * For example: select the record 'JPMF-000001'.  
7. In the Description field, type a value.
8. In the BusinessUnit field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
    * For example: select the record '003'.  
10. Click Endorse to vendor.
11. Click Inquiry.
12. Click Voucher.
    * Verify that an accounting voucher is generated for the endorsement.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
