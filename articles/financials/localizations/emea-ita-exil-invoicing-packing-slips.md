---
# required metadata

title: Sorting sales invoice lines by packing slip
description: This topic provides information about how to set up and print accompanying invoices that contain required packing slips details.
author: ilkond
manager: AnnBe
ms.date: 10/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-29
ms.dyn365.ops.version: 10.0.8

---

# Sorting sales invoice lines by packing slip

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In Italy, companies often need to issue what is called, "accompanying invoices" which are a combination of an ordinary invoice and a DDT (transposrt document or packing slip).

## Prerequisites

- The primary address of the legal entity must be in **Italy**.
- In **Feature management**, verify that the feature **Sales invoice lines sorting by packing slips** is enabled. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md)
- On the **Print management setup** page (**Accounts receivable** /> **Setup** /> **Forms** /> **Form setup** /> **General** FastTab /> **Print management**), set the reference to **SalesInvoice.Report_IT** layout for Customer invoice (Original).

![Invoicing of packing slips setup](media/emea-ita-exil-invoice-packing-slip-pic2.jpg)

> [!NOTE]
> With the feature **Sales invoice lines sorting by packing slips** enabled, the parameter, **Print packing slip specifications** will be ignored as it is considered to be not enabled. To view this, go to **Accounts receivable > Setup > Forms > Form setup > Invoice** (FastTab).
> ![Print packing slip specifications](media/emea-ita-exil-invoice-packing-slip-pic3.jpg)

## Accompanying invoices printing
After you have enabled and set up the feature, the invoice report printout will contain invoice lines that are grouped and sorted by packing slip.

![Invoicing of packing slips](media/emea-ita-exil-invoice-packing-slip-pic.jpg)

> [!NOTE]
> The new layout is applicable only to invoices that are based on sales orders. The functionality does not apply to free-text invoices, because they don't use packing slips.

