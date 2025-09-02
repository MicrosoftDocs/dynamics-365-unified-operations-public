---
title: Implementation details of JPK_KR_PD reporting
description: Learn about implementation details for the JPK_KR_PD report in legal entities in Poland.
author: liza-golub
ms.author: egolub
ms.topic: reference
ms.custom: 
  - bap-template
ms.date: 03/07/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---
# Implementation details of JPK_KR_PD reporting

[!INCLUDE[banner](../../includes/banner.md)]

This article provides implementation details for JPK_KR_PD reporting.

## The journal entry number (D_1)

The **Dziennik** section of the JPK_KR_PD report corresponds to the Journal (General Ledger Journal) and includes detailed records of all accounting entries. It provides a list of transactions recorded in the accounting books for a given period (General Journal Accounting Entries). The **D_1** field of the **Dziennik** section represents the journal entry number that's assigned continuously in the financial year.

It's recommended you use the **Journalize transactions** periodic task before you report the JPK_KR_PD. Learn about the **Journalize transactions** periodic task in [Journalize posted journal entries](../../general-ledger/tasks/journalize-posted-journal-entries.md).

When **Journalize transactions** periodic task was executed for detailed records of accounting entries, the **D_1** field represents the number from journalized journal. If the **Journalize transactions** periodic task wasn't executed for some records of accounting entries, the **Voucher** value is reported in **D_1** field of this record.

## Date of the economic transaction (D_6)

In the JPK_KR_PD report, the **D_6** field in the Dziennik (Journal) section represents the date of the economic transaction referred to in art. 23 sec. 2 point 1 of the Accounting Act, placed on the accounting document by its issuer, in accordance with the requirement specified in art. 21 sec. 1 point 4 of the Accounting Act.

For the records of accounting entries that correspond to sales operations, this field represents the **Sales date** value in the case it was filled in, and in the case when the **Sales date** is not used, the **Document date** or **Accounting date**.

For the records of accounting entries that correspond to purchase operations, this field represents the **Date of vendor VAT register** value in the case it was filled in, and in the case when the **Date of vendor VAT register** is not used, the **Document date** or **Accounting date**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
