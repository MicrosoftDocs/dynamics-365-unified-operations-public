---
# required metadata

title: General journal posting performance 
description: The article suggests ways to troubleshoot performance issues when you post general journals. For example, you can adjust the number sequence setup and limit journal lines.
author: Livbjerg
ms.date: 07/24/2023
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

# General journal posting performance

[!include [banner](../includes/banner.md)]

The article suggests ways to troubleshoot performance issues when you post general journals. These issues might be caused by the following factors:

- The number sequence setup
- The number of lines per journal
- Batch processing of journals
- The **Lines limit** feature

## Symptom

General journal posting seems slower than you expect.

## Resolution

Microsoft Dynamics 365 Finance supports journals that have a large number of lines. However, the configuration of the **Finance** module and journal posting can create situations where general journal posting seem slower than customers expect.

### Number sequences and journal performance

The number sequence, and the retrieval of numbers in it, can affect the performance of general ledger posting. In particular, the voucher number sequence itself can be a factor.

In some countries/regions or industries, a continuous number sequence for ledger vouchers is a regulatory requirement. However, in many jurisdictions, continuous voucher numbers aren't a regulatory requirement.

When general journal posting becomes a performance bottleneck, we recommend that you use a noncontinuous number sequence and enable preallocation for the voucher number sequence.

On the **Number sequences** page, you can enable preallocation when a noncontinuous number sequence is used. You can specify how many numbers should be requested from the database and stored in memory. After all the preallocated numbers are used, new numbers are requested from the database.

For more information about preallocation of number sequences, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md?context=/dynamics365/context/finance).

### Run journal posting in batch mode

We recommend that you post journals in the background as a batch job. Journal posting in batch mode can improve performance in several ways:

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

#### Lines limit

The **Lines limit** value on a journal enables parallel processing when journals are posted in a batch. The **Lines limit** field defines the minimum number of lines to move to a new journal. Those lines are then processed in parallel.

Splitting a journal works best for vouchers that have a smaller number of lines. A voucher can't be split across journals. The **Original journal No.** field on a journal indicates the journal that it was split from. The **Lines limit** field can be set for a journal name. The value is then used by default for all journals that are created that have that journal name.

> [!NOTE]
> We recommend that you start the **Lines limit** value at 1,000 and then test specific workloads until you find the optimal number.
>
> When the **Lines Limit** feature is used, any document attachment or workflow on the original journal isn't copied to the additional journals that are created during posting. Users must pay attention to the **Original Journal No.** value for document and workflow references.

#### Voucher size

If you use the **Lines limit** feature, it's important that you consider the average voucher size. The posting process can determine when it should split the journals if the vouchers in the journal balances. If the number of lines in each voucher exceeds the **Lines limit** value, the voucher size determines which journal lines are used for the split.

| Journal lines | Voucher lines | Lines Limit | Parallel processing | Number of journals posted |
|---------------|---------------|-------------|---------------------|---------------------------|
| 150,000       | ~500          | 0           | No                  | 1                         |
| 150,000       | ~500          | 10,000      | Yes                 | 15                        |
| 150,000       | ~50,000       | 10,000      | Yes                 | 3                         |
| 150,000       | 150,000       | 10,000      | No                  | 1                         |


### Other areas to consider for journal performance

There are several other indicators that might be impacting general journal posting performance. Below are a few which should be considered carefully.

#### Database logging and SQL change tracking

In general, SQL change tracking isn't recommended for highly volatile (high volume of inserts, updates and deletes) database tables. Some financial journal tables, such as LedgerJournalTrans, are among the most volatile tables within Dynamics 365 Finance. In addition, some financial journal tables are considered work tables and aren't candidates for change tracking. When change tracking is enabled on these entities, it can create triggers and have performance impact.

For more information, see [Configure database logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

Due to volatility of financial tables, it's also recommended that lock escalation of both the table and indexes for LedgerJournalTrans and its related tables be turned off. In production environments, we have automatic checks that attempt to disable lock escalation if it's enabled on this table. However, these checks don't run on development or UAT environments. If you are experiencing slow performance, it's suggested that this setting is verified and lock escalation is disabled.

#### Tax Engine

By default, sales tax amounts on journal lines are calculated when tax-related fields are updated. Although this behavior helps users see tax amounts calculated in real time, it can also affect performance for large journals with significant number of lines. The **Delayed tax calculation feature** lets you delay tax calculation on journals and therefore helps assure optimal performance. When this feature is turned on, tax amounts are calculated only when a user presses **Sales Tax** or posts the journal.

For more information about this feature, see [Enable delayed tax calculation on journals](../../finance/general-ledger/enable-delayed-tax-calculation.md).

#### Configuration keys

To assure optimal performance, only necessary configuration keys should be enabled in your environment. If you do not use, for example, budget or public sector features, configuration keys can be disabled for these scenarios.

See [License codes and configuration keys](../../fin-ops-core/dev-itpro/sysadmin/license-codes-configuration-keys-report.md) for more details.
