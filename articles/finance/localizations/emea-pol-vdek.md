---
title: VAT declaration with registers (JPK-V7, VDEK)
description: This article provides information about the VAT declaration with registers (also known as a JPK-V7, VDEK) in Poland.
author: liza-golub
ms.date: 07/19/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Poland
ms.author: egolub
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
---

# VAT declaration with registers (JPK-V7, VDEK)

[!include [banner](../includes/banner.md)]

This article provides information about the value-added tax (VAT) declaration with registers (also known as a JPK-V7, VDEK) in Poland.

As of October 1, 2020, businesses in Poland are responsible for reporting VAT in an electronic document that consists of a Jednolity Plik Kontrolny VAT (JPK_VAT) together with the declaration (Jednolity Plik Kontrolny VDEK). The requested electronic document includes the following information:

- Both VAT records (a set of information about purchases and sales that is produced from the entrepreneur's VAT records for a given period) – VAT registers
- A VAT declaration (VAT-7 declaration)

As of Microsoft Dynamics 365 Finance version **10.0.29**, the JPK-V7M feature supports filing a VAT return for [multiple VAT registrations](emea-multiple-vat-registration-numbers.md).

Depending on the periodicity of its obligation for VAT return reporting, a VAT-registered company in Poland can report JPK-V7 in one of the following formats:

- **JPK-V7M** – For taxpayers who are required to submit both the VAT registers part and the declaration part monthly. Taxpayers are obligated to complete all JPK-V7M elements in the XML file. These elements include `Naglówek`, `Podmiot1`, `Deklaracja`, and `Ewidencja`.
- **JPK-V7K** – For taxpayers who are required to submit the VAT registers part monthly and the declaration part quarterly. For the first two months of the quarter, taxpayers should fill in the following JPK-V7K elements in the XML file: `Naglówek`, `Podmiot1`, and `Ewidencja`. For the third month of the quarter, all JPK-V7K elements in the XML file should be filled in. These elements include `Naglówek`, `Podmiot1`, `Deklaracja`, and `Ewidencja`. The `Deklaracja` element applies to data for the whole quarter, whereas the `Ewidencja` element applies to data only for the last month of the quarter. The **JPK-V7K** schema is supported as of Microsoft Dynamics 365 Finance version **10.0.36**.

## Prerequisites

Before you can prepare Finance to report a JPK-V7, your business processes and the system must meet the following conditions:

- On the **Sales tax authorities** page (**Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax authorities**), for the tax authority that is associated with tax codes that are used in tax transactions that must be considered by the JPK-V7M report, the **Report layout** field must be set to **Default**. For more information about how to set up sales tax authorities, see [Set up sales tax authorities](../general-ledger/tasks/set-up-sales-tax-authorities.md).
- When tax transactions that must be considered by the JPK-V7 report are posted, the **Date of VAT register** field must be set.
- On the **Sales tax codes** page (**Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax codes**), for the sales tax codes that are used in tax transactions that must be considered by the JPK-V7 report, the **Type of tax** field must be set to **Standard VAT** or **Reduced VAT**.
- On the **Sales tax codes** page, for the sales tax codes that are used in tax transactions that must be considered by the JPK-V7 report, the sales tax reporting codes that are used in the Electronic reporting (ER) format of the report must be appropriately defined.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
