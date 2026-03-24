---
title: Number sequences overview
description: Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers.
author: SunilGarg
ms.author: sunilg
ms.topic: overview
ms.date: 03/10/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: NumberSequenceTableListPage, NumberSequenceConfiguration
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6e19bd1d-192b-4da2-8573-84f6e1ce98ef
---

# Number sequences overview

[!include [banner](../includes/banner.md)]

Use number sequences to generate readable, unique identifiers for master data records and transaction records that need identifiers. A master data record or transaction record that needs an identifier is called a *reference*.

Before you can create new records for a reference, set up a number sequence and associate it with the reference. Use the pages in **Organization administration** to set up number sequences. If you need module-specific settings, use the parameters page in a module to specify number sequences for the references in that module. For example, in **Accounts receivable** and **Accounts payable**, you can set up number sequence groups to allocate specific number sequences to specific customers or vendors.

When you set up a number sequence, specify a scope to define which organization uses the number sequence. The scope can be **Shared**, **Company**, **Legal entity**, or **Operating unit**. You can combine **Legal entity** and **Company** scopes with **Fiscal calendar period** to create even more specific number sequences.

Number sequence formats consist of segments. Number sequences with a scope other than **Shared** can contain segments that correspond to the scope. For example, a number sequence with a scope of **Legal entity** can contain a legal entity segment. By including a scope segment in the number sequence format, you can identify the scope of a particular record by looking at its number.

In addition to segments that correspond to scopes, number sequence formats can contain **Constant** and **Alphanumeric segments**. A **Constant** segment contains a set of letters, numbers, or symbols that doesn't change. An **Alphanumeric** segment contains a set of letters or numbers that increment each time you use a number. Use a number sign (\#) to represent incrementing numbers and an ampersand (&) to represent incrementing letters. For example, the format \#\#\#\#\#\_2017 creates the sequence 00001\_2017, 00002\_2017, and so on.

## Number sequence examples

The following examples show how to use segments to create number sequence formats. In particular, the examples demonstrate the effects of using scope segments.

### Expense report numbers

In the following example, you set up expense report numbers for the legal entity that is titled **CS**.

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

In the following example, you set up sales order numbers for the company ID **CEU**.

- **Area:** Sales
- **Reference:** Sales order
- **Scope:** Company
- **Company:** CEU

| Segments  | Segment type | Value    |
|-----------|--------------|----------|
| Segment 1 | Constant     | SO-      |
| Segment 2 | Alphanumeric | \#\#\#\# |

**Example of formatted number**: SO-0029

Even though the format doesn't include a scope segment, numbering restarts for each company ID. If you use the same format for all company IDs, each company uses the same numbers. For example, sales order number SO-0029 is used in each company. You can also change the whole number sequence format for other company IDs.

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

Because the scope is **Shared**, the number sequence format is used across the organization. You can't set up different number sequence formats for different parts of the organization.

## Performance considerations for number sequences

Consider the following information about how the configuration of number sequences can affect system performance before you set up number sequences.

### Continuous and noncontinuous number sequences

Number sequences can be continuous or noncontinuous. A continuous number sequence doesn't skip any numbers, but you might not use the numbers sequentially. You use numbers from a noncontinuous number sequence sequentially, but the number sequence might skip numbers.

- Continuous Number Sequence (CNS)

  - Doesn't skip any numbers
  - You might not use numbers sequentially
  - Example: If a user cancels a transaction, the system generates a number but later recycles (reuses) it

- Noncontinuous Number Sequence (Non-CNS)

  - Might skip numbers
  - You use numbers sequentially (based on caching)
  - Example: If a user cancels a transaction, the system generates a number but doesn't use it

> [!NOTE]
> The **Enable continuous number sequence performance improvements** feature provides enterprise readiness with continuous number sequences, which was challenging in finance and operations apps. The feature is in public preview in version 10.0.34, and generally available in version 10.0.36.
>
> This feature improves performance with continuous number sequences by preallocating a number in the sequence for each request. By default, the system allocates five numbers in a sequence, but you can adjust this value. If there's an unexpected termination of any number, the clean-up job is improved.

For continuous and noncontinuous number sequences, you can enable **Preallocation** on the **Performance** FastTab of the **Number sequences** page. When you specify a quantity of numbers to preallocate, the system selects those numbers and stores them in memory for noncontinuous number sequences and in the database for continuous number sequences.

If you use a noncontinuous number sequence, you can enable **Preallocation** on the **Performance** FastTab of the **Number sequences** page. When you specify a quantity of numbers to preallocate, the system selects those numbers and stores them in memory. The system requests new numbers from the database only after it uses the preallocated quantity.

Unless there's a regulatory or legal compliance requirement that you use continuous number sequences, use noncontinuous number sequences.

### Automatic cleanup of number sequences

If an application error, crash, or other unexpected failure occurs, the system tries to automatically recycle numbers for continuous number sequences. You can run the cleanup process manually or automatically to recover lost numbers.

Carefully consider server usage when you plan the cleanup process. Perform the cleanup as a batch job during nonpeak hours.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
