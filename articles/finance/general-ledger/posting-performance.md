---
# required metadata

title: General journal posting performance 
description: The article suggests ways to troubleshoot performance issues when posting general journals, including adjusting number sequence setup and limiting journal lines.
author: Livbjerg
ms.date: 05/24/2023
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

# Journal posting performance

[!include [banner](../includes/banner.md)]

This article describes issues that might cause performance issues with general journals. This includes:
 - number sequence setup 
 - number of lines per journal 
 - batch processing of journals 
 - the **Lines limit** feature

## Symptom

General journal posting seem slower than expected.

## Resolution

Dynamics 365 Finance supports journals with large numbers of lines. But the configuration of the finance module and journal posting can create situations where posting general journals seem slower than customer 
expectations.

## Number sequences and journal performance

The number sequence, and retrieval of numbers in it, can be a factor in general ledger posting performance. Particularly, the voucher number sequence itself.

In certain countries/regions or industries, a continuous number sequence for ledger vouchers is a regulatory requirement. But in many jurisdictions, continuous vouchers aren't a regulatory requirement.

When general journal posting becomes a performance bottleneck, we recommend number sequence that isn't continuous and enable preallocation for voucher number sequence.  

On the **Number Sequences Page**, you can enable preallocation when using a non-continuous number sequence. You can specify a quantity of numbers to be selected and stored in memory. 
After all the preallocated numbers have been used, new numbers are requested from the database.

For more information about preallocation of number sequences, see [Number Sequence Overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md?context=/dynamics365/context/finance).

## Run journal posting in batch

We recommend posting journals in the background as a **Batch job**. Journal posting in batch can improve performance in several ways:

- It's executed in the background, allowing the user to continue with other tasks while the journal is being processed.
- It supports parallel processing for improved performance.
- It can reduce the need for manual interaction by setting up a recurring batch job with **Late selection** of journals and transfer of errors to a separate journal.

On the **Post journals** page to post journals in batch. The fields on this page:
 - **Select** - View or modify the query that selects the journals to be posted. After the query window is closed, the selected records are displayed in the grid unless **Late selection** is selected.
 - **Late selection** - Select **Late selection** to run the query that selects journals to be posted, when the journal posting batch job starts. When **Late selection** isn't marked, the selected journals are  shown in the **Overview grid**.

> [!NOTE]
> Mark **Late selection** when using a recurring batch to select the journals to be posted.

 - **Transfer errors** - Select **Transfer errors** to allow valid journals to post and move vouchers that fail to post to a new journal. If **Transfer errors** isn't selected, the entire journal will fail to 
 post if any of the vouchers contain errors.

## Run journal posting in parallel

We recommended parallel or multithreaded execution of processes where possible. 
Some things to consider: 

- Size of the journals
- Advantages of splitting larger journals into multiple smaller journals before posting them
- Having the system split them at posting time
- Size of the vouchers 

### Size of journals

For example, you have a journal with 150,000 lines to post. If you post the lines in one journal, with none of the parallel options configured, the journal posting is executed in a single thread.

If you manually split the journal into 15 separate journals with 10,000 lines in each, the journals can be executed in parallel manually by using batch. However, manually splitting journals can be tedious work. 
Dynamics 365 Finance can, in many cases, automatically split the journal. 

### Lines limit

The **Lines limit** on a journal has to enable parallel processing when posting journals in batch. The **Lines limit** defines the minimum number of lines to move to a new journal, which are then processed in 
parallel.

Splitting a journal works best with vouchers that have a smaller number of lines. A voucher can't be split across journals. The **Original journal No.** field on a journal indicates the journal it was split from. 
The **Lines limit** can be set on a journal name and defaults to all journals created with the journal name.

> [!NOTE]
> We recommend starting the **Lines limit** at 1000 and then testing specific workloads until you find the optimal number.

> [!NOTE]
> When the **Lines Limit** feature is used, any document attachment or workflow on the original journal isn't copied to the additional journals created during posting. Users must pay attention to the **Original Journal No.** for document and workflow references.

## Voucher size

It's important to consider the average voucher size when using the **Lines limit** feature. The posting process can decide when to split the journals if the vouchers in the journal balances. If each
voucher has more lines than the **Lines limit** field, the voucher size decides which journal lines are used for the split.

| Journal lines | Voucher lines    | Lines Limit      | Parallel processing | Number of journals posted|
|---------------|------------------|------------------|---------------------|--------------------------|
|    150,000    |       ~500       |           0      |       No            |    1                     |
|    150,000    |       ~500       |      10,000      |       Yes           |    15                    |
|    150,000    |    ~50,000       |      10,000      |       Yes           |    3                     |
|    150,000    |    150,000       |      10,000      |       No            |    1                     |
