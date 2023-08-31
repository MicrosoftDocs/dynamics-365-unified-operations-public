---
# required metadata

title: Automatic split of large financial journals
description: The article describes the performance improvements from automatically splitting large financial journals into multiple journals.
author: Livbjerg
ms.date: 08/30/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: JLivbjerg
ms.search.validFrom: 2023-5-1
ms.dyn365.ops.version: 10.0.28

---

# Automatic split of large financial journals

[!include [banner](../includes/banner.md)]

As of Microsoft Dynamics 365 Finance version 10.0.36, the **Automatic split of large financial journals** feature improves the posting performance of financial journals. The performance improvements are achieved by automatically splitting a financial journal into multiple journals and posting them in batch mode. Batches are split based on a line limit that's defined by Microsoft. This feature works for all types of financial journals except payroll disbursement journals.

> [!NOTE]
> The **Automatic split of large financial journals** feature is enabled in Feature management.

## Feature summary and benefits

Customers often post financial journals that contain a large number of lines. This situation can cause performance issues. The **Automatic split of large financial journals** feature removes the **Lines limit** setting from the journal name and automatically splits a journal into multiple journals. The journal is split based on a limit of 1,000 lines that's defined by Microsoft. New journals that are created from the split contain a reference to the original journal.

Vouchers are never split across multiple journals, even if the voucher contains more than the line limit. The individual voucher lines always remain in the same journal. For example, if a journal contains a single voucher that has 2,000 lines, all the lines of the voucher remain in one journal.

If the number of lines in the journal exceeds the defined line limit, the posting stops, and a warning informs the user that they should post the journal in batch mode. Posting in batch mode improves the efficiency of posting and lets users continue their work.

### Scenario

For example, a general journal contains 1,050 lines. Each line is a separate voucher. After the feature is enabled, a warning informs the user that they should use the **Post in batch** process.

In the batch job configuration, **Batch processing** can't be disabled. After the batch processing is completed, two separate journals are shown. The first journal contains the first 1,000 lines (each of which is a separate voucher), and the second journal contains the remaining 50 lines.
