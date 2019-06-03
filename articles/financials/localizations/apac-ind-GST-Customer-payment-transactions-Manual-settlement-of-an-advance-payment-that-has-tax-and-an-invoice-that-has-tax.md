---
# required metadata

title: Manual settlement of an advance payment that has tax and an invoice that has tax
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
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

# Manual settlement of an advance payment that has tax and an invoice that has tax

Tax is posted on both the advance payment and the sales invoice. On settling these transactions through the Open transaction editing form, the double tax entry gets reversed.
The following table shows the tax entries that are generated in various scenarios when an invoice that has tax and a payment that has tax are settled

| Transaction details | Example                                                 | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00 | Tax on the payment is reversed.<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00  | Tax on the payment is reversed to the extent of the invoice<br/>amount.<br/>IGST interim payable account Cr. 1,000.00<br/>IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 | Tax on the payment is reversed.<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |





