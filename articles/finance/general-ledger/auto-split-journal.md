---
title: Automatic split of large financial journals
description: Learn about the performance improvements from automatically splitting large financial journals into multiple journals, including a feature summary and benefits.
author: Livbjerg
ms.author: JLivbjerg
ms.topic: article
ms.date: 06/07/2024
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

As of Microsoft Dynamics 365 Finance version 10.0.36, the **Automatic split of large financial journals** feature improves the posting performance of financial journals. The performance improvements are achieved by automatically splitting a financial journal into multiple journals and posting them in batch mode. Batches are split based on a line limit that's defined by Microsoft. This feature works for all types of financial journals except payroll disbursement journals.

Part of this new feature is **Parent journal and related journals**. All journals that are created from the automatic split of one large journal are related to each other through the parent journal number that's stored in each of them. All these journals are considered *related journals*, and the original journal is considered the *parent journal*. Users can include the **Parent journal number** field in the list to view the parent journal and its related journals. Storage of this mapping has benefits during a **Reversal of journal** scenario.  

> [!NOTE]
> The **Automatic split of large financial journals** feature is enabled in Feature management.

## Feature summary and benefits

Customers often post financial journals that contain a large number of lines. This situation can cause performance issues. 

In previous versions, each journal had a **Line Limit** parameter that defines the limit for lines per journal. By default, the line limit is blank and if the customer doesn't set any value or set a very large number as limit, there would be posting performance issues for large journals. To address this limitation, the **Automatic split of large journals** feature was introduced. After this feature is active, it hides line-limit parameters from individual journals, and it becomes a global parameter effective for all journals. The default value for the **Autosplit** parameter is 1000, which is recommended by Microsoft. 


The **Automatic split of large financial journals** feature removes the **Lines limit** setting from the journal name and automatically splits a journal into multiple journals. The journal is split based on a limit of 1,000 lines that's defined by Microsoft. New journals that are created due to the auto-split contain a reference to the original journal which is also considered as parent journal and other split journals are considered related journals.

Vouchers are never split across multiple journals, even if the voucher contains more than the line limit. The individual voucher lines always remain in the same journal. For example, if a journal contains a single voucher that has 2,000 lines, all the lines of the voucher remain in one journal.

If the number of lines in the journal exceeds the defined line limit, the posting stops, and a warning informs the user to post the journal in batch mode. Posting in batch mode improves the efficiency of posting and lets users continue their work.


>[!Note:]
> One exception to the auto-split feature is with simulate posting. When simulate posting is performed, it skips the check for automatic split limit and runs the posting simulation on all lines considering it as one journal. The simulate posting works on the entire journal but it will be a synchronous process, if journal has a large number of lines, the user's UI interaction will be blocked until the operation is over.


### Scenario

For example, a general journal contains 1,050 lines. Each line is a separate voucher. After the feature is enabled, a warning informs the user that they should use the **Post in batch** process.

In the batch job configuration, **Batch processing** can't be disabled. After the batch processing is completed, two separate journals are shown. The first journal contains the first 1,000 lines (each of which is a separate voucher), and the second journal contains the remaining 50 lines.
