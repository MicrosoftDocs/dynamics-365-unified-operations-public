---
# required metadata

title: Indis GST Whitepaper
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
author: EricWang
manager: RichardLuan
ms.date: 05/31/2019
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

## Advance payment that is settled during invoice posting

This section provides information about tax posted on the customer advance payment and selected for the settlement, while posting the customer invoice.
The following tables shows the tax entries that are generated for the invoice when an advance payment is settled in various scenarios.

| Transaction details | Example                                                 | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00 | Tax on the invoice is posted.<br/>Tax on the payment is reversed to prevent a double entry in the related voucher.<br/>IGST payable account Cr. 2,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00  | Tax on the invoice is posted.<br/>Tax on the payment is reversed to the extent of the invoice<br/>amount in the related voucher.<br/>IGST payable account Cr. 1,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 1,000.00<br/>IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 | Tax on the invoice is posted.<br/>Tax on the payment is reversed to the extent of the payment<br/>amount in the related voucher<br/>IGST payable account Cr. 4,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |





