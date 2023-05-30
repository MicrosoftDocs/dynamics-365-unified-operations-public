---
# required metadata

title: Number sequences overview
description: Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers.
author: SunilGarg
ms.date: 05/03/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: NumberSequenceTableListPage, NumberSequenceConfiguration
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 6e19bd1d-192b-4da2-8573-84f6e1ce98ef
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
contributors: 
- saurabh-kuchhal

---

# Number sequences overview

[!include [banner](../includes/banner.md)]

> [!NOTE]
> The 'Enable continuous number sequence performance improvements' feature provides enterprise readiness with continuous number sequence, which was challenging in finance and operations apps. The feature is in Public Preview in 10.0.34 version, and GA in 10.0.36 version.

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. A master data record or transaction record that requires an identifier is referred to as a *reference*.

Before you can create new records for a reference, you must set up a number sequence and associate it with the reference. We recommend that you use the pages in **Organization administration** to set up number sequences. If module-specific settings are required, you can use the parameters page in a module to specify number sequences for the references in that module. For example, in **Accounts receivable** and **Accounts payable**, you can set up number sequence groups to allocate specific number sequences to specific customers or vendors.

When you set up a number sequence, you must specify a scope, which defines which organization uses the number sequence. The scope can be **Shared**, **Company**, **Legal entity**, or **Operating unit**. **Legal entity** and **Company** scopes can be combined with **Fiscal calendar period** to create even more specific number sequences.

Number sequence formats consist of segments. Number sequences with a scope other than **Shared** can contain segments that correspond to the scope. For example, a number sequence with a scope of **Legal entity** can contain a legal entity segment. By including a scope segment in the number sequence format, you can identify the scope of a particular record by looking at its number.

In addition to segments that correspond to scopes, number sequence formats can contain **Constant** and **Alphanumeric segments**. A **Constant** segment contains a set of letters, numbers, or symbols that doesn't change. An **Alphanumeric** segment contains a set of letters or numbers that increment every time that a number is used. Use a number sign (\#) to represent incrementing numbers and an ampersand (&) to represent incrementing letters. For example, the format \#\#\#\#\#\_2017 creates the sequence 00001\_2017, 00002\_2017, and so on.

## Number sequence examples

The following examples show how to use segments to create number sequence formats. In particular, the examples demonstrate the effects of using scope segments.

### Expense report numbers

In the following example, expense report numbers are set up for the legal entity that is titled **CS**.

- **Area:** Travel and expense
- **Reference:** Expense report number
- **Scope:** Legal entity
- **Legal entity:** CS

| Segments  | Segment type | Value     |
|-----------|--------------|-----------|
| Segment 1 | Legal entity | CS        |
| Segment 2 | Constant     | -EXPENSE- |
| Segment 3 | Alphanumeric | \#\#\#\#  |

**Example of formatted number**: CS-EXPENSE-0039

You can set up a similar number sequence format for other legal entities. For example, for a legal entity that is named **RW**, if you change only the value of the legal entity segment, the formatted number is RW-EXPENSE-0039. You can also change the whole number sequence format for other legal entities. For example, you can omit the legal entity scope segment to create a formatted number such as Exp-0001.

### Sales order numbers

In the following example, sales order numbers are set up for the company ID **CEU**.

- **Area:** Sales
- **Reference:** Sales order
- **Scope:** Company
- **Company:** CEU

| Segments  | Segment type | Value    |
|-----------|--------------|----------|
| Segment 1 | Constant     | SO-      |
| Segment 2 | Alphanumeric | \#\#\#\# |

**Example of formatted number**: SO-0029

Even though a scope segment isn't included in the format, numbering restarts for each company ID. If you use the same format for all company IDs, the same numbers are used in each company. For example, sales order number SO-0029 is used in each company. You can also change the whole number sequence format for other company IDs.

### Purchase requisition numbers

In the following example, purchase requisition numbers are organization-wide.

- **Area:** Purchase
- **Reference:** Purchase requisition
- **Scope:** Shared

| Segments  | Segment type | Value    |
|-----------|--------------|----------|
| Segment 1 | Constant     | Req      |
| Segment 2 | Alphanumeric | \#\#\#\# |

**Example of formatted number**: Req0052

Because the scope is **Shared**, the number sequence format is used across the organization. You cannot set up different number sequence formats for different parts of the organization.

## Performance considerations for number sequences

Consider the following information about how the configuration of number sequences can affect system performance before you set up number sequences.

### Continuous and noncontinuous number sequences

Number sequences can be continuous or noncontinuous. A continuous number sequence doesn't skip any numbers, but numbers may not be used sequentially. Numbers from a noncontinuous number sequence are used sequentially, but the number sequence may skip numbers.
- Continuous Number Sequence (CNS)

   - Doesn't skip any numbers
   - Numbers may not be used sequentially
   - Ex: If a user cancels a transaction, a number is generated, but recycled (re-used) later

- Noncontinuous Number Sequence (Non-CNS)

   - May skip numbers
   - Numbers may be used sequentially (based on caching)
   - Ex: If a user cancels a transaction, a number is generated, but not used

> [!NOTE]
> The 'Enable continuous number sequence performance improvements' feature provides enterprise readiness with continuous number sequence, which was challenging in finance and operations apps. The feature is in Public Preview in 10.0.34 version, and GA in 10.0.36 version.
>
>This feature improves performance with continuous number sequences by pre-allocating a number in the sequence for each request. By default, five numbers in a sequence will be allocated, but this can be adjusted as you need. In the event of an unexpected termination of any number, improvements have been made to the clean-up job that runs.

For continuous/noncontinuous number sequences, you can enable **Preallocation** on the **Performance** FastTab of the Number sequences page. When you specify a quantity of numbers to preallocate, the system selects those numbers, then stores them in memory in case of noncontinuous number sequences and in the database for continuous number sequences.


If you use a noncontinuous number sequence, you can enable **Preallocation** on the **Performance** FastTab of the **Number sequences** page. When you specify a quantity of numbers to preallocate, the system selects those numbers and stores them in memory. New numbers are requested from the database only after the preallocated quantity has been used.

Unless there's a regulatory/legal compliance requirement that you use continuous number sequences, we recommend that you use noncontinuous number sequences.

### Automatic cleanup of number sequences

In case of an application error, crashes or other unexpected failure, the system tries to recycle numbers automatically for continuous number sequences. You can run the cleanup process manually or automatically to recover the lost numbers.

Carefully consider server usage when you plan the cleanup process. We recommend that you perform the cleanup as a batch job during nonpeak hours.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
