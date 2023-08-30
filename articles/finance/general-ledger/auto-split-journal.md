---
# required metadata

title: Autosplit of large financial journals 
description: The article describes the performance improvements by automatically splitting large financial journals into multiple journals.
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

# Autosplit of large financial journals 

[!include [banner](../includes/banner.md)]

Beginning in Dynamics 365 Finance version 10.0.36, the **Automatic split of large financial journals** feature enhances the posting performance of financial journals. The performance improvements are accomplished by automatcially splitting a financial journal into multiple journals and posting them in batch mode. Batches are split based on a line-limit defined by Microsoft. This feature works for all financial journal types except payroll disbursement.  

>[!NOTE]
>The **Automatic split of large financial journals** feature is enabled in Feature management.  

 ## Feature summary and benefits 

Customers often post financial journals that contain a large quantity of lines that can cause performance issues. This feature removes the **Lines limit** setting from the Journal name, and automatically splits a 
journal into multiple journals. The journal is split based on a 1000 line limit defined by Microsoft.   

New journals created from the split contains a reference to the original journal. Vouchers are never split across multiple journals, even if the voucher contains more than the line limit. 
The individual voucher lines always remain in the same journal. For example, if a journal contains a single voucher with 2,000 lines, all the lines of the voucher remain in one journal.  

If the number of lines within the journal is greater than the defined line limit, the posting stops with a warning. The warning informs the user to post the journal in batch mode. Posting in batch mode 
improves the efficiency of posting, allowing users to continue with their work.  

### Scenario  

For example, a general journal contains 1050 lines. Each line is a separate voucher. After the feature is enabled, a warning will display to use the **Post in batch** process .  

In the batch job configuration, **Batch processing** can't be disabled. After the batch processing is complete, two separate journals are displayed. The first journal contains the first 1000 lines (each line being a separate voucher) and the second journal contains the remaining 50 lines.  

 
