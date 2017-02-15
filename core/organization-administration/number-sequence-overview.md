---
# required metadata

title: Number sequence overview
description: Number sequences in Microsoft Dynamics 365 for Operations are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. A master data record or transaction record that requires an identifier is referred to as a <em>reference</em>.
author: MargoC
manager: AnnBe
ms.date: 2015-12-03 20 - 19 - 22
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 15461
ms.assetid: e48d3d6c-55bb-4561-9f6b-0a6304a0eadd
ms.search.region: Global
# ms.search.industry: 
ms.author: margoc
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Number sequence overview

Number sequences in Microsoft Dynamics 365 for Operations are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. A master data record or transaction record that requires an identifier is referred to as a <em>reference</em>.

Before you can create new records for a reference in Microsoft Dynamics 365 for Operations, you must set up a number sequence and associate it with the reference. We recommend that you use the pages in **Organization administration** to set up number sequences. If module-specific settings are required, you can use the parameters page in a module to specify number sequences for the references in that module. For example, in **Accounts receivable** and **Accounts payable**, you can set up number sequence groups to allocate specific number sequences to specific customers or vendors. When you set up a number sequence, you must specify a scope, which defines which organization uses the number sequence. The scope can be **Shared**, **Company**, **Legal entity**, or **Operating unit**. **Legal entity** and **Company** scopes can be combined with **Fiscal calendar period** to create even more specific number sequences. Number sequence formats consist of segments. Number sequences with a scope other than **Shared** can contain segments that correspond to the scope. For example, a number sequence with a scope of **Legal entity** can contain a legal entity segment. By including a scope segment in the number sequence format, you can identify the scope of a particular record by looking at its number. In addition to segments that correspond to scopes, number sequence formats can contain **Constant** and **Alphanumeric segments**. A **Constant** segment contains a set of letters, numbers, or symbols that does not change. An **Alphanumeric** segment contains a set of letters or numbers that increment every time that a number is used. Use a number sign (\#) to represent incrementing numbers and an ampersand (&) to represent incrementing letters. For example, the format \#\#\#\#\#\_2017 creates the sequence 00001\_2017, 00002\_2017, and so on.
Number sequence examples
------------------------

The following examples show how to use segments to create number sequence formats. In particular, the examples demonstrate the effects of using scope segments.
### Expense report numbers

In the following example, expense report numbers are set up for the legal entity that is titled **CS**. **Area:** Travel and expense **Reference:** Expense report number **Scope:** Legal entity **Legal entity:** CS
| Segments  | Segment type | Value     |
|-----------|--------------|-----------|
| Segment 1 | Legal entity | CS        |
| Segment 2 | Constant     | -EXPENSE- |
| Segment 3 | Alphanumeric | \#\#\#\#  |

**Example of formatted number**: CS-EXPENSE-0039 You can set up a similar number sequence format for other legal entities. For example, for a legal entity that is named **RW**, if you change only the value of the legal entity segment, the formatted number is RW-EXPENSE-0039. You can also change the whole number sequence format for other legal entities. For example, you can omit the legal entity scope segment to create a formatted number such as Exp-0001.

### Sales order numbers

In the following example, sales order numbers are set up for the company ID **CEU**. **Area:** Sales **Reference:** Sales order **Scope:** Company **Company:** CEU
| Segments  | Segment type | Value    |
|-----------|--------------|----------|
| Segment 1 | Constant     | SO-      |
| Segment 2 | Alphanumeric | \#\#\#\# |

**Example of formatted number**: SO-0029 Even though a scope segment is not included in the format, numbering restarts for each company ID. If you use the same format for all company IDs, the same numbers are used in each company. For example, sales order number SO-0029 is used in each company. You can also change the whole number sequence format for other company IDs.

### Purchase requisition numbers

In the following example, purchase requisition numbers are organization-wide. **Area:** Purchase **Reference:** Purchase requisition **Scope:** Shared
| Segments  | Segment type | Value    |
|-----------|--------------|----------|
| Segment 1 | Constant     | Req      |
| Segment 2 | Alphanumeric | \#\#\#\# |

**Example of formatted number**: Req0052 Because the scope is **Shared**, the number sequence format is used across the organization. You cannot set up different number sequence formats for different parts of the organization. 
Performance considerations for number sequences
-----------------------------------------------

Consider the following information about how the configuration of number sequences can affect system performance before you set up number sequences.
### Continuous and non-continuous number sequences

Number sequences can be continuous or non-continuous. A continuous number sequence does not skip any numbers, but numbers may not be used sequentially. Numbers from a non-continuous number sequence are used sequentially, but the number sequence may skip numbers. For example, if a user cancels a transaction, a number is generated, but not used. In a continuous number sequence, that number is recycled later. In a non-continuous number sequence, the number is not used. Continuous number sequences are typically required for external documents, such as purchase orders, sales orders, and invoices. However, continuous number sequences can adversely affect system response times because the system must request a number from the database every time that a new document or record is created. If you use a non-continuous number sequence, you can enable **Preallocation** on the **Performance** FastTab of the **Number sequences** page. When you specify a quantity of numbers to preallocate, the system selects those numbers and stores them in memory. New numbers are requested from the database only after the preallocated quantity has been used. Unless there is a regulatory requirement that you use continuous number sequences, we recommend that you use non-continuous number sequences for better performance.

### Automatic cleanup of number sequences

In case of a power failure, an application error, or other unexpected failure, the system cannot recycle numbers automatically for continuous number sequences. You can run the cleanup process manually or automatically to recover the lost numbers. Carefully consider server usage when you plan the cleanup process. We recommend that you perform the cleanup as a batch job during non-peak hours.



