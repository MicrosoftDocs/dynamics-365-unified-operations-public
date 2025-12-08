---
title: Pay a vendor transaction by endorsing a customer bill of exchange
description: Learn how to pay a vendor transaction by endorsing a customer bill of exchange in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseToVendor, DimensionLookup, LedgerTransVoucher
ms.custom: 
  - bap-template
---

# Pay a vendor transaction by endorsing a customer bill of exchange

[!include [banner](../../includes/banner.md)]

This article explains how to pay a vendor transaction by endorsing a customer bill of exchange in Japan with Microsoft Dynamics 365 Finance.

The following procedure uses the demo data company JPMF.

Before you can complete this procedure, you must have at least one bill of exchange with a status of "Drawn".

To endorse a customer bill of exchange to a vendor, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments \> Bill of exchange \> Endorse bills of exchange**.
1. In the list, find and select a bill of exchange that has a status of "Drawn".  
1. Select **Endorse to vendor** to open the drop dialog.
1. In the **Date of endorsement** field, enter a date. The date can't be later than the due date of the bill of exchange.  
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select the record "JPMF-000001".  
1. In the **Description** field, enter a value.
1. In the **BusinessUnit** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select the record "003".  
1. Select **Endorse to vendor**.
1. Select **Inquiry**.
1. Select **Voucher**.
1. Verify that an accounting voucher is generated for the endorsement.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
