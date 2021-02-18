---
# required metadata

title: TDS calculation on invoices
description: This topic provides a reference for transactions that the Tax Deducted at Source (TDS) is calculated on at the invoice-level.
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# TDS calculation on invoices

[!include [banner](../includes/banner.md)]

This topic provides a reference for transactions that the Tax Deducted at Source (TDS) is calculated on at the invoice-level.

| Serial number | Transaction type                                 | Transaction amount | Form name and locator                                        | Account type and offset account type                         |
| ------------- | ------------------------------------------------ | ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1.            | Purchase made from vendor / recording expenses   | Debit  Or  Credit  | General journals form(General ledger >  Journal entries > General journals), Invoice approval journal form (Accounts payable > Invoices > Invoice approval), Invoice journal form (Accounts payable >  Invoices > Invoice journal) | Ledger (Dr.)  Vendor (Cr.).  Withholding tax is calculated for the Vendor-Ledger  combination only when the Ledger account has the posting type **Purchase**  **cash**. |
| 2.            | Purchase made from customer / recording expenses | Debit  Or  Credit  | General journals form(General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal) | Ledger (Dr.)  Customer (Cr.)                                 |
| 3.            | Purchase of fixed asset from vendor              | Debit  Or  Credit  | General journals form(General ledger >  Journal entries > General journals), Invoice register journal form (Accounts payable > Invoices > Invoice register), Invoice journal form (Accounts payable >  Invoices > Invoice journal) | Fixed assets (Dr.)  Vendor (Cr.)                             |
| 4.            | Purchase of fixed asset from customer            | Debit  Or  Credit  | General journals form(General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal) | Fixed assets (Dr.)  Customer (Cr.)                           |
| 5.            | Purchase invoice  (TDS payable)                  |                    | Purchase order form (Accounts payable > Purchase orders > All purchase orders) |                                                              |
| 6.            | Sales invoice  (TDS receivable)                  |                    | Sales order form (Accounts receivable > Orders > All sales orders), Free text invoice form (Accounts receivable > Invoices > All free text invoices) |                                                              |
