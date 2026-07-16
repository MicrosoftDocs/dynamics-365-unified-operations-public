---
title: Automatic split of large financial journals
description: Learn about the performance improvements from automatically splitting large financial journals into multiple journals, including a feature summary and benefits.
author: Livbjerg
ms.author: JLivbjerg
ms.topic: article
ms.date: 06/24/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-5-1
ms.search.form: 
ms.dyn365.ops.version: 10.0.28
---

# Automatic split of large financial journals

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Finance, the **Automatic split of large financial journals** feature improves the posting performance of financial journals. The performance improvements are achieved by automatically splitting a financial journal into multiple journals and posting them in batch mode. Batches are split based on a line limit that's defined by Microsoft. This feature works for all types of financial journals except payroll disbursement and fixed assets journals.

Part of this feature is **Parent journal and related journals**. All journals that are created from the automatic split of one large journal are related to each other through the parent journal number that's stored in each of them. All these journals are considered *related journals*, and the original journal is considered the *parent journal*. Users can include the **Parent journal number** field in the list to view the parent journal and its related journals. Storage of this mapping has benefits during a **Reversal of journal** scenario.  

> [!NOTE]
> Enable the **Automatic split of large financial journals** feature in Feature management.

## Feature summary and benefits

Customers often post financial journals that contain a large number of lines. This situation can cause performance problems.

In previous versions, each journal had a **Line limit** parameter that defined the limit for lines per journal. By default, the line limit was blank, and if the customer didn't set any value or set a large number as the limit, there were posting performance issues for large journals. To address this limitation, the **Automatic split of large journals** feature was introduced. After this feature is active, it hides the **Line limit** parameter from individual journals. Instead, **Line limit** becomes a global parameter that's effective for all journals. The default value for the **Autosplit** parameter is **1000**. Microsoft recommends that you use this value.

The **Automatic split of large financial journals** feature removes the **Lines limit** setting from the journal name and automatically splits a journal into multiple journals. The journal is split based on a limit of 1,000 lines that's defined by Microsoft. New journals that the automatic split creates contain a reference to the original journal. This journal is the parent journal, and other split journals are related journals.

Vouchers are never split across multiple journals, even if the voucher contains more than the line limit. The individual voucher lines always remain in the same journal. For example, if a journal contains a single voucher that has 2,000 lines, all the lines of the voucher remain in one journal.

If the number of lines in the journal exceeds the defined line limit, posting stops, and a warning instructs the user to post the journal in batch mode. Posting in batch mode improves posting efficiency and lets users continue their work.

> [!NOTE]
> One exception to the **Automatic split of large financial journals** feature involves simulated posting. When this operation is performed, it skips the check for an automatic split limit. Instead, it runs the posting simulation on all lines, treating them as one journal. Simulated posting works on the whole journal but is a synchronous process. If the journal has a large number of lines, the user's UI interaction is blocked until the operation is completed.

### Scenario

For example, a general journal contains 1,050 lines. Each line is a separate voucher. When you enable this feature, a warning prompts you to use the **Post in batch** process.

In the batch job configuration, you can't disable **Batch processing**. After the batch processing finishes, two separate journals appear. The first journal contains the first 1,000 lines (each line is a separate voucher), and the second journal contains the remaining 50 lines.

### Reversals

For information about how to reverse journals that the system automatically split, see [Reverse journal entries](reverse-journal-posting.md#reverse-related-journals-with-journals-that-were-automatically-split).
