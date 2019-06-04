---
# required metadata

title: Manually settling an advance payment and invoice that include tax
description:  This topic provides information about the tax entries that are generated in various scenarios when an invoice and a payment that include tax are settled.
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
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Manually settling an advance payment and invoice that include tax

Tax is posted on both the advance payment and the sales invoice. When these transactions are settled on the **Open transaction editing** page, the double tax entry is reversed.

The following table shows the tax entries that are generated in various scenarios when an invoice and a payment that have tax are settled.

| Transaction details | Example                                                 | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00 | - Tax on the payment is reversed.<br/>- IGST interim payable account Cr. 2,000.00<br/>- IGST payable account Dr. 2,000.00 |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00  | - Tax on the payment is reversed to the extent of the invoice amount.<br/>- IGST interim payable account Cr. 1,000.00<br/>- IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 | - Tax on the payment is reversed.<br/>- IGST interim payable account Cr. 2,000.00<br/>- IGST payable account Dr. 2,000.00 |





