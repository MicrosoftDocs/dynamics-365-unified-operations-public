---
# required metadata

title: Financial journal posting performance 
description: The article suggests ways to troubleshoot performance issues when you post financial journals. For example, you can adjust the number sequence setup and limit journal lines.
author: Livbjerg
ms.date: 02/24/2024
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

# Financial journal posting performance

[!include [banner](../includes/banner.md)]

The article suggests ways to troubleshoot performance issues when you post financial journals. These issues might be caused by the following factors:

- The number sequence setup
- The number of lines per journal
- Batch processing of journals
- The **Lines limit** feature

## Symptom

Financial journal posting seems slower than you expect.

## Resolution

Microsoft Dynamics 365 Finance supports journals that have a large number of lines. However, the configuration of the **Finance** module and journal posting can create situations where financial journal posting seems slower than customers expect.

### Number sequences and journal performance

The number sequence, and the retrieval of numbers in it, can affect the performance of general ledger posting. In particular, the voucher number sequence itself can be a factor.

In some countries/regions or industries, a continuous number sequence for ledger vouchers is a regulatory requirement. However, in many jurisdictions, continuous voucher numbers aren't a regulatory requirement.

When financial journal posting becomes a performance bottleneck, we recommend that you use a noncontinuous number sequence and enable preallocation for the voucher number sequence.

On the **Number sequences** page, you can enable preallocation when a noncontinuous number sequence is used. You can specify how many numbers should be requested from the database and stored in memory. After all the preallocated numbers are used, new numbers are requested from the database.

For more information about preallocation of number sequences, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md?context=/dynamics365/context/finance).

### Run journal posting in batch mode

We recommend that you post journals in the background as a batch job. Journal posting in batch mode uses a [top picking pattern](../../fin-ops-core/dev-itpro/perf-test/batch-para-multi-thread.md) and can improve performance in several ways:

- Because it runs in the background, users can continue to work on other tasks while the journal is being processed.
- It supports parallel processing.
- If it's set up as a recurring batch job that uses late selection of journals and transfer of errors to a separate journal, it can reduce the need for manual interaction.

Use the following buttons and fields on the **Post journals** page to set up journal posting in batch mode:

- **Select** – View or modify the query that selects the journals to post. After the query dialog box is closed, the selected records appear in the **Overview** grid, unless the **Late selection** option is selected.
- **Late selection** – Select this option to run the query that selects the journals to post when the batch job for journal posting begins. If this option isn't selected, the selected journals appear in the **Overview** grid.

    > [!NOTE]
    > Select **Late selection** if you're using a recurring batch job to select the journals to post.

- **Transfer errors** – Select this option to enable valid journals to post and move vouchers that fail to be posted to a new journal. If this option isn't selected, the whole journal will fail to be posted if any of the vouchers contain errors.

### Run journal posting in parallel

We recommend parallel or multithreaded execution of processes whenever possible.

Here are some things to consider:

- The size of the journals
- The advantages of splitting larger journals into multiple smaller journals before posting
- Whether you want the system to split the journals at posting time
- The size of the vouchers

#### Size of journals

For example, a journal has 150,000 lines that must be posted. If you don't configure any of the parallel options, and you post the lines in one journal, journal posting runs in a single thread.

If you manually split the journal into 15 journals, each of which has 10,000 lines, the journals can be manually run in parallel by using a batch. It can be tedious work to manually split journals. However, in many cases, Dynamics 365 Finance can automatically split the journal.

For more information, see 

#### Lines limit

The **Lines limit** value on a journal enables parallel processing when journals are posted in a batch. The **Lines limit** field defines the minimum number of lines to move to a new journal. Those lines are then processed in parallel.

Splitting a journal works best for vouchers that have a smaller number of lines. A voucher can't be split across journals. The **Original journal No.** field on a journal indicates the journal that it was split from. The **Lines limit** field can be set for a journal name. The value is then used by default for all journals that are created that have that journal name.

> [!NOTE]
> In Dynamics 365 Finance version 10.0.36, financial journals supports auto-split of large journals with a threshold value of 1,000 lines per journal. Journals with more than 1,000 lines will be posted as part of the batch job and will be split into 1,000 lines per journal. For more information, see [Autosplit of large financial journals](auto-split-journal.md).   

#### Voucher size

If you use the **Lines limit** feature, it's important that you consider the average voucher size. The posting process can determine when it should split the journals if the vouchers in the journal balances. If the number of lines in each voucher exceeds the **Lines limit** value, the voucher size determines which journal lines are used for the split.

| Journal lines | Voucher lines | Lines Limit | Parallel processing | Number of journals posted |
|---------------|---------------|-------------|---------------------|---------------------------|
| 150,000       | ~500          | 0           | No                  | 1                         |
| 150,000       | ~500          | 10,000      | Yes                 | 15                        |
| 150,000       | ~50,000       | 10,000      | Yes                 | 3                         |
| 150,000       | 150,000       | 10,000      | No                  | 1                         |

### Additional areas to consider for journal performance

Other factors can affect the performance of general journal posting. This section describes some additional areas that you should consider.

#### Database logging and SQL change tracking

SQL change tracking isn't recommended for highly volatile database tables (that is, tables that have a high volume of insertions, updates, and deletions). Some financial journal tables, such as `LedgerJournalTrans`, are among the most volatile tables in Dynamics 365 Finance. In addition, some financial journal tables are considered work tables and therefore aren't candidates for change tracking. If change tracking is enabled on these entities, it can create triggers and affect performance.

For more information, see [Configure database logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

Because of the volatility of financial tables, we recommend that you turn off lock escalation for both the table and the indexes for `LedgerJournalTrans` and its related tables. In production environments, automatic checks try to disable lock escalation if it's enabled for this table. However, these checks don't run in development or user acceptance testing (UAT) environments. If you experience slow performance, we recommend that you verify this setting and disable lock escalation.

#### Tax Engine

By default, the sales tax amounts on journal lines are calculated when tax-related fields are updated. Although this behavior helps users see tax amounts calculated in real time, it can also affect performance for large journals that have a significant number of lines. The **Delayed tax calculation** feature delays the tax calculation on journals and therefore helps ensure optimal performance. When this feature is turned on, tax amounts are calculated only when a user selects **Sales Tax** or posts the journal.

For more information, see [Enable delayed tax calculation on journals](../../finance/general-ledger/enable-delayed-tax-calculation.md).

#### Configuration keys

To ensure optimal performance, you should enable only necessary configuration keys in your environment. For example, if you don't use budget or public sector features, you can disable the configuration keys for those scenarios.

For more information, see [License codes and configuration keys](../../fin-ops-core/dev-itpro/sysadmin/license-codes-configuration-keys-report.md).
