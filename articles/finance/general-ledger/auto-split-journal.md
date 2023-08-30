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

A new feature was introduced in Dynamics 365 Finance version 10.0.36 enhances the posting performance of financial journals. The performance improvements are accomplished automatically by splitting a financial 
journal into multiple journals and posting them in batch mode, based on the line-limit defined by Microsoft. This feature works for all financial journal types except payroll disbursement.  

The feature Automatic split of large financial journals must be enabled in the Feature management workspace.  

 

## Feature summary and benefits 

Customers often post financial journals that contain a large quantity of lines, causing performance issues. This feature removes the Lines limit setting from the Journal name, and instead automatically splits a 
journal into multiple journals based on a line limit defined by Microsoft. The default line limit is 1000 lines.  

Each new journal created from the split contains a reference to the original, parent journal. A voucher will never be split across multiple journals, even if the voucher contains more than the line limit. 
The lines of an individual voucher must always remain in the same journal. For example, if a journal contains a single voucher with 2,000 lines, all the lines of the voucher remain in the journal and not be 
split into multiple journals.  

In addition, if the number of lines within the journal is greater than the defined line limit, the posting stops with a warning, informing the user to post the journal in batch mode. Posting in batch mode 
improves the efficiency of posting, allowing users to continue with their work.  

When testing this feature internally, we found that customers COULD experience up to a 71% improvement when posting a simple General journal with 10,000 lines, with each line being a separate voucher. Your 
results may vary depending on the composition of the voucher (includes taxes, settlement, Customer/vendors updates, etc.).  

### Scenario  

Let’s assume that a general journal is entered, and it contains 1050 lines. Each line is a separate voucher. When this feature is enabled, the user will now observe a warning and will be forced to use the 
‘Post in batch’ process.  


Within the batch job configuration, the user can't disable the Batch processing option. Once the batch processing is complete, the user sees two separate journals. The first journal contains the first 
1000 lines (each line being a separate voucher) and the second journal contains the remaining 50 lines.  

 
