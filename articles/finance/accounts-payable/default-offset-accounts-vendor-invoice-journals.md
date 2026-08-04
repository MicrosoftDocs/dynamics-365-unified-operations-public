---
title: Default offset accounts for vendor invoice and invoice approval journals
description: Learn about default offset accounts for vendor invoice and invoice approval journals, including a table to help decide where you should assign default accounts.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/30/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerJournalTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 553933ca-928d-4031-bb8c-f9cff458320b
---

# Default offset accounts for vendor invoice and invoice approval journals

[!include [banner](../includes/banner.md)]

Use default offset accounts on the following vendor invoice journal pages:

- Invoice journal
- Invoice approval journal

Use the following table to help decide where to assign default accounts for invoice journals.

| Set up default accounts here | Where default accounts are provided | How this option affects processing | When you should use this option |
|---|---|---|---|
| **Vendor group** – Set up default offset accounts for vendor groups on the **Default account setup** page, which you can open from the **Vendor groups** page. | <ul><li>Vendor account</li><li>Journal entries for vendor accounts in the vendor group, if default accounts aren't specified for vendor accounts</li></ul> | The default offset accounts for vendor groups appear as default offset accounts for vendors on the **Default account setup** page. You can open this page from the **All vendors** list page. | Use this option if you typically pay for the same types of things from the same vendor groups over time. |
| **Vendor account** – Set up default accounts for vendor accounts on the **Default account setup** page, which you can open from the **Vendors** page. | Journal entries for the vendor account | The default offset accounts for vendor accounts appear as default offset accounts for journal entries for the vendor account. | Use this option if you typically pay for the same types of things from the same vendors over time. |
| **Journal names** – Set up default offset accounts for journals on the **Journal names** page. Select the **Fixed offset account** option. Note that you can't specify default offset accounts on journal names if the journal type of the journal names is **Invoice register** or **Approval**. | <ul><li>Journal header that uses the journal name</li><li>Journal entries in journals that use the journal name</li></ul> | If you select the **Fixed offset account** option on the **Journal names** page, the offset account for the journal name overrides the default offset account for the vendor or vendor group. | Use this option to set up journals for specific costs and expenses that are charged to specific accounts, regardless of the vendor or the vendor group that the vendor belongs to. |
| **Journal names** – Set up default offset accounts for journals on the **Journal names** page. Clear the **Fixed offset account** option. Note that you can't specify default offset accounts on journal names if the journal type of the journal names is **Invoice register** or **Approval**. | <ul><li>Journal header</li><li>Journal entries in journals that use the journal name</li></ul> | These default entries are used on journal header pages, and the offset account on the journal header page is used as a default entry on the journal voucher pages. The system uses default accounts from the **Journal names** page only if default accounts aren't set up for the vendor account. | Use this option to set up default accounts that are used when a default vendor offset account isn't assigned. |
| **Journal header** – Set up a default offset account for a journal as a default entry on the journal voucher pages. You can't specify default offset accounts on the journal header if the journal type of the journal names is **Invoice register** or **Approval**. | Journal entries in the journal | The default offset account for a journal is the default entry on the journal voucher pages. | Use this option to speed up data entry if most entries in a journal use the same offset account. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
