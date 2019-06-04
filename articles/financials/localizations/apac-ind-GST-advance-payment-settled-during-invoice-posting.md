---
# required metadata

title: Advance payment settled during invoice posting
description: This topic provides information about tax that is posted on a customer advance payment when the payment is settled and the customer invoice is posted.
author: EricWang
manager: RichardLuan
ms.date: 06/03/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Advance payment that is settled during invoice posting


The following tables shows the tax entries that are generated for the invoice when an advance payment is settled in various scenarios.

| Transaction details | Example                                                 | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00 | - Tax on the invoice is posted.<br/>- Tax on the payment is reversed to prevent a double entry in the related voucher.<br/>- IGST payable account Cr. 2,000.00.<br/>**Related voucher:**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00. |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00  | - Tax on the invoice is posted.<br/>- Tax on the payment is reversed to the extent of the invoice amount in the related voucher.<br/>- IGST payable account Cr. 1,000.00<br/>**Related voucher:**<br/>IGST interim payable account Cr. 1,000.00<br/>IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 | - Tax on the invoice is posted.<br/>- Tax on the payment is reversed to the extent of the payment amount in the related voucher.<br/>- IGST payable account Cr. 4,000.00<br/>**Related voucher:**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |





