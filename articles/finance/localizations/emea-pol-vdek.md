---
title: VAT declaration with registers (JPK-V7M, VDEK)
description: This article provides information about the VAT declaration with registers (also known as a JPK-V7M, VDEK) in Poland.
author: AdamTrukawka
ms.date: 07/19/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Poland
ms.author: atrukawk
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
---

# VAT declaration with registers (JPK-V7M, VDEK)

[!include [banner](../includes/banner.md)]

This article provides information about the value-added tax (VAT) declaration with registers (also known as a JPK-V7M, VDEK) in Poland.

As of October 1, 2020, businesses in Poland are responsible for reporting VAT in an electronic document that consists of a Jednolity Plik Kontrolny VAT (JPK_VAT) together with the declaration (Jednolity Plik Kontrolny VDEK). The requested electronic document includes the following information:

- Both VAT records (a set of information about purchases and sales that is produced from the entrepreneur's VAT records for a given period)
- A VAT declaration (VAT-7 declaration)

As of Microsoft Dynamics 365 Finance version **10.0.29**, the JPK-V7M feature supports filing a VAT return for [multiple VAT registrations](emea-multiple-vat-registration-numbers.md).

## Prerequisites

Before you can prepare Finance to report a JPK-V7M, your business processes and the system must meet the following conditions:

- On the **Sales tax authorities** page (**Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax authorities**), for the tax authority that is associated with tax codes that are used in tax transactions that must be considered by the JPK-V7M report, the **Report layout** field must be set to **Default**. For more information about how to set up sales tax authorities, see [Set up sales tax authorities](../general-ledger/tasks/set-up-sales-tax-authorities.md).
- When tax transactions that must be considered by the JPK-V7M report are posted, the **Date of VAT register** field must be set.
- On the **Sales tax codes** page (**Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax codes**), for the sales tax codes that are used in tax transactions that must be considered by the JPK-V7M report, the **Type of tax** field must be set to **Standard VAT** or **Reduced VAT**.
- On the **Sales tax codes** page, for the sales tax codes that are used in tax transactions that must be considered by the JPK-V7M report, the sales tax reporting codes that are used in the Electronic reporting (ER) format of the report must be appropriately defined.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
