---
title: Dual reporting
description: Learn about an example that shows how you can fulfill the requirements for both International Financial Reporting Standard (IFRS) reporting in Asset leasing.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseBookMaster
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Dual reporting

[!include [banner](../includes/banner.md)]

This article guides you through an example that shows how you can fulfill the requirements for both International Financial Reporting Standard (IFRS) reporting and statutory reporting in Asset leasing. Familiarity with posting layers in Microsoft Dynamics 365 Finance is required and will make the example easier to understand.

## Example

The following example accounts for a lease under Italian statutory reporting by using both the cash-basis method and IFRS reporting methods. The company must establish three books to account for both the Italian statutory requirements and the IFRS 16 requirements. One book is required for IFRS 16, one book is required for statutory requirements, and one book is required to automatically reverse statutory postings. The books are set up as shown in the following tables.

**IFRS 16 book**

The IFRS 16 book is set up so that it complies with the IFRS 16 accounting standard. All entries that are posted in this book will be posted to a custom layer.

| Name                                    | Description    |
|-----------------------------------------|----------------|
| Book type                               | IFRS 16        |
| Book description                        | IFRS 16        |
| Posting Layer                           | Custom layer 1 |
| Lease Type                              | Finance        |
| Accounting Framework                    | IFRS 16        |
| Lease Term / Useful life Set Up         | 0.00           |
| Present Value / Asset Fair Value Set Up | 0.00           |
| Short-term threshold                    | 12             |
| Low Value Threshold                     | 5,000.00       |
| Pay to Vendor                           | No             |

**Statutory book**

The statutory book is a cash-basis book where the company will account for the lease expense as the amount of cash that is paid each month for rent. This book won't produce a right-of-use (ROU) asset or lease liability.

| Name                                    | Description |
|-----------------------------------------|-------------|
| Book type                               | Statutory   |
| Book description                        | Local GAAP  |
| Posting Layer                           | Current     |
| Lease Type                              | Automatic   |
| Accounting Framework                    | Cash basis  |
| Lease Term / Useful life Set Up         | 0.00        |
| Present Value / Asset Fair Value Set Up | 0.00        |
| Short-term threshold                    | 0           |
| Low Value Threshold                     | 0           |
| Pay to Vendor                           | No          |

**Statutory reversal book**

The statutory reversal book is set up in the same way as the statutory book.

| Name                                    | Description                    |
|-----------------------------------------|--------------------------------|
| Book type                               | Statutory – Reversal           |
| Book description                        | Book to reverse statutory book |
| Posting Layer                           | Custom layer 1                 |
| Lease Type                              | Automatic                      |
| Accounting Framework                    | Cash basis                     |
| Lease Term / Useful life Set Up         | 0.00                           |
| Present Value / Asset Fair Value Set Up | 0.00                           |
| Short-term threshold                    | 0                              |
| Low Value Threshold                     | 0                              |
| Pay to Vendor                           | No                             |

For this example, a lease has been created that has the following settings on the **General** and **Payment schedule lines** tabs.

**General tab**

| Field                      | Value            |
|----------------------------|------------------|
| Incremental borrowing rate | 5%               |
| Commencement date          | 1/1/2020         |
| Lease group                | Buildings        |
| Vendor                     | 1001             |
| Fair value of the asset    | 245,000          |
| Asset useful life          | 120              |
| Annuity type               | Ordinary annuity |
| Compounding interval       | Monthly          |

**Payment schedule lines tab**

| Field             | Value      |
|-------------------|------------|
| Start date        | 1/1/2020   |
| Period interval   | Months     |
| Periods           | 24         |
| End date          | 12/31/2020 |
| Payment frequency | Monthly    |
| Payment amount    | 1,000      |

To account for this lease under two frameworks, you use a current posting layer and a custom posting layer. The following table shows an example of every journal entry that required to fairly represent the financials under each reporting standard. A detailed description of each journal entry for the first month of the lease is provided afterward.

<table>
<thead>
<tr>
<th rowspan='3'>Account number</th>
<th rowspan='3'>Description</th>
<th colspan='3'>Statutory book (current layer)</th>
<th rowspan='3'>Current layer total</th>
<th>Reversal book (custom layer)</th>
<th colspan='4'>IFRS 16 book (custom layer)</th>
<th rowspan='3'>Current layer + custom layer total</th>
</tr>
<tr>
<th>JE-100</th>
<th>JE-110</th>
<th>JE-120</th>
<th>JE-130</th>
<th>JE-140</th>
<th>JE-150</th>
<th>JE-160</th>
<th>JE-170</th>
</tr>
<tr>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>Lease expense</td>
<td>1,000.00</td>
<td></td>
<td></td>
<td>1,000.00</td>
<td>-1,000.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>2</td>
<td>Bank fee</td>
<td></td>
<td>3.00</td>
<td></td>
<td>3.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>3.00</td>
</tr>
<tr>
<td>3</td>
<td>VAT expense</td>
<td></td>
<td>5.00</td>
<td></td>
<td>5.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>5.00</td>
</tr>
<tr>
<td>4</td>
<td>Clearing account</td>
<td>-1,000.00</td>
<td>1,000.00</td>
<td></td>
<td>0.00</td>
<td>1,000.00</td>
<td></td>
<td>-1,000.00</td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>5</td>
<td>Accounts payable</td>
<td></td>
<td>-1,008.00</td>
<td>1,008.00</td>
<td>0.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>6</td>
<td>ROU asset</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
<td></td>
<td>22,794.00</td>
<td></td>
<td></td>
<td></td>
<td>22,793.90</td>
</tr>
<tr>
<td>7</td>
<td>Finance lease obligation</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
<td></td>
<td>-22,794.00</td>
<td>1,000.00</td>
<td>-94.97</td>
<td></td>
<td>-21,888.87</td>
</tr>
<tr>
<td>8</td>
<td>Interest expense</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
<td></td>
<td></td>
<td></td>
<td>94.97</td>
<td></td>
<td>94.97</td>
</tr>
<tr>
<td>9</td>
<td>Cash</td>
<td></td>
<td></td>
<td>-1,008.00</td>
<td>-1,008.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>-1,008.00</td>
</tr>
<tr>
<td>10</td>
<td>Depreciation expense</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>949.75</td>
<td>949.75</td>
</tr>
<tr>
<td>11</td>
<td>Accumulated depreciation</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>-949.75</td>
<td>-949.75</td>
</tr>
</tbody>
</table>

As the preceding table shows, three books are required to report under both statutory reporting and IFRS reporting.

- The statutory book records the lease payment according to the rules for cash-basis accounting under the current layer.
- The statutory reversal book reverses the statutory journal entries.
- The IFRS 16 book creates the journal entries that are required under IFRS 16.

You must enter a lease only one time. You can then open the **Books** page to see all the books that are associated with the lease.

> [!NOTE]
> When you create the books, all three of them must be associated with the same lease record.

The first journal entry records the lease expense under the statutory book. You can create the payments either in a batch or by selecting the payment schedule in the statutory book.

For this example, the following journal entry is produced for the statutory book from the payment schedule.

### Lease payment – 1/31/2020 – JE 100

| Account type | Account number | Layer   | Account description | Debit    | Credit   |
|--------------|----------------|---------|---------------------|----------|----------|
| Ledger       | 1              | Current | Lease expense       | 1,000.00 |          |
| Ledger       | 4              | Current | Clearing account    |          | 1,000.00 |

An Accounts payable clerk uses standard Dynamics 365 functionality to create an invoice to pay for the lease outside Asset leasing. However, instead of selecting **Lease expense** as the debit account, the Accounts payable clerk selects a clearing account to generate the following entry.

### AP process – 1/31/2020 – JE 110

| Account type | Account number | Layer   | Account description | Debit    | Credit   |
|--------------|----------------|---------|---------------------|----------|----------|
| Ledger       | 4              | Current | Clearing account    | 1,000.00 |          |
| Ledger       | 2              | Current | Bank fee            | 3.00     |          |
| Ledger       | 3              | Current | VAT expense         | 5.00     |          |
| Vendor       | 5              | Current | Accounts payable    |          | 1,008.00 |

When the statement is issued to the vendor, you follow the regular payment process. During this process, the following journal entry is generated.

### Cash payment – 1/31/2020 – JE 120

| Account type | Account number | Layer   | Account description | Debit    | Credit   |
|--------------|----------------|---------|---------------------|----------|----------|
| Vendor       | 5              | Current | Accounts Payable    | 1,008.00 |          |
| Bank         | 9              | Current | Cash                |          | 1,008.00 |

At this point, you've fully accounted for this lease under statutory reporting requirements and can generate a trial balance by using the current layer. The system returns a trial balance that has the following figures.

<table>
<thead>
<tr>
<th rowspan='3'>Account number</th>
<th rowspan='3'>Description</th>
<th colspan='3'>Statutory book (current layer)</th>
<th rowspan='3'>Current layer total</th>
</tr>
<tr>
<th>JE-100</th>
<th>JE-110</th>
<th>JE-120</th>
</tr>
<tr>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
<th>Dr (Cr)</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>Lease expense</td>
<td>1,000.00</td>
<td></td>
<td></td>
<td>1,000.00</td>
</tr>
<tr>
<td>2</td>
<td>Bank fee</td>
<td></td>
<td>3.00</td>
<td></td>
<td>3.00</td>
</tr>
<tr>
<td>3</td>
<td>VAT expense</td>
<td></td>
<td>5.00</td>
<td></td>
<td>5.00</td>
</tr>
<tr>
<td>4</td>
<td>Clearing account</td>
<td>-1,000.00</td>
<td>1,000.00</td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>5</td>
<td>Accounts payable</td>
<td></td>
<td>-1,008.00</td>
<td>1,008.00</td>
<td>0.00</td>
</tr>
<tr>
<td>6</td>
<td>ROU asset</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>7</td>
<td>Finance lease obligation</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>8</td>
<td>Interest expense</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>9</td>
<td>Cash</td>
<td></td>
<td></td>
<td>-1,008.00</td>
<td>-1,008.00</td>
</tr>
<tr>
<td>10</td>
<td>Depreciation expense</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
<tr>
<td>11</td>
<td>Accumulated depreciation</td>
<td></td>
<td></td>
<td></td>
<td>0.00</td>
</tr>
</tbody>
</table>

If you want to use the IFRS 16 figures to run the same trial balance, the statutory accounting journal entries must be reversed, and the IFRS 16 journal entries must be posted. To reverse the statutory journal entries, this example includes a statutory reversal book that has the same setup as the statutory book but an opposite posting profile. For example, the statutory book *debited* a lease expense account, but the reversal book will *credit* this account. These relationships are easily defined in the Asset leasing posting accounts on the **Asset leasing parameters** page (**Asset leasing \> Setup \> Asset leasing parameters**).

When the same process that was used for the statutory book is used for the reversal book, the following journal entry is produced. The difference is that the reversal book books the reversing entries from the statutory book. The reversing entries are also made to the custom layer. When a trial balance is run at the current layer, the reversing journal entries aren't included.

### Lease payment – 1/31/2020 – JE 130

| Account type | Account number | Layer  | Account description | Debit    | Credit   |
|--------------|----------------|--------|---------------------|----------|----------|
| Ledger       | 4              | Custom | Clearing account    | 1,000.00 |          |
| Ledger       | 1              | Custom | Lease expense       |          | 1,000.00 |

Now that you've eliminated the statutory journal entries, you will book all the journal entries that IFRS 16 requires in the IFRS 16 book. These entries include the initial recognition of the ROU asset and the liability, and the record of interest and depreciation.

### Initial recognition – 1/1/2020 – JE 140

| Account type | Account number | Layer  | Account description      | Debit     | Credit    |
|--------------|----------------|--------|--------------------------|-----------|-----------|
| Ledger       | 6              | Custom | ROU Asset                | 22,793.90 |           |
| Ledger       | 7              | Custom | Finance lease obligation |           | 22,793.90 |

The lease payment is posted like the other lease payments. The reason for using the clearing account is to ensure that cash is credited only one time.

### Lease payment – 1/31/2020 – JE 150

| Account type | Account number | Layer  | Account description      | Debit    | Credit   |
|--------------|----------------|--------|--------------------------|----------|----------|
| Ledger       | 7              | Custom | Finance lease obligation | 1,000.00 |          |
| Ledger       | 4              | Custom | Clearing account         |          | 1,000.00 |

The interest expense journal entry is generated from the liability amortization schedule.

### Interest expense – 1/31/2020 – JE 160

| Account type | Account number | Layer  | Account description      | Debit | Credit |
|--------------|----------------|--------|--------------------------|-------|--------|
| Ledger       | 8              | Custom | Interest expense         | 94.97 |        |
| Ledger       | 7              | Custom | Finance lease obligation |       | 94.97  |

The depreciation expense journal entry is generated from the asset depreciation schedule.

### Depreciation expense – 1/31/2020 – JE 170

| Account type | Account number | Layer  | Account description      | Debit  | Credit |
|--------------|----------------|--------|--------------------------|--------|--------|
| Ledger       | 10             | Custom | Depreciation expense     | 949.75 |        |
| Ledger       | 11             | Custom | Accumulated depreciation |        | 949.75 |

After all these journal entries are created and posted, you will see the following "custom layer 1" values. Note that the last column includes the bank fee, the value-added tax (VAT) expense, and the reduction of cash from the previous layer, but it doesn't include the statutory reporting journal entries. Therefore, you achieve true dual-reporting capabilities. At this point, the company just has to run its trial balance, and combine the current layer and the custom layer to create an IFRS trial balance.

| Account No | Description              | Statutory Book\-Current Layer\-JE\-100\-Dr \(Cr\) | Statutory Book\-Current Layer\-JE\-110\-Dr \(Cr\) | Statutory Book\-Current Layer\-JE\-120\-Dr \(Cr\) | Current Layer \- Totals | - | Reversal Book\-Custom layer\-JE\-130\-Dr \(Cr\) | IFRS 16 Book\-Custom layer\-JE\-140\-Dr \(Cr\) | IFRS 16 Book\-Custom layer\-JE\-150\-Dr \(Cr\) | IFRS 16 Book\-Custom layer\-JE\-160\-Dr \(Cr\) | IFRS 16 Book\-Custom layer\-JE\-170\-Dr \(Cr\) | Custom Layer \+ Current Layer \- Totals |
|------------|--------------------------|---------------------------------------------------|---------------------------------------------------|---------------------------------------------------|-------------------------|---|-------------------------------------------------|------------------------------------------------|------------------------------------------------|------------------------------------------------|------------------------------------------------|-----------------------------------------|
| 1          | Lease expense            | 1,000\.00                                         |                                                   |                                                   | 1,000\.00               |   | \-1,000                                         |                                                |                                                |                                                |                                                | 0\.00                                   |
| 2          | Bank fee                 |                                                   | 3\.00                                             |                                                   | 3\.00                   |   |                                                 |                                                |                                                |                                                |                                                | 3\.00                                   |
| 3          | VAT expense              |                                                   | 5\.00                                             |                                                   | 5\.00                   |   |                                                 |                                                |                                                |                                                |                                                | 5\.00                                   |
| 4          | Clearing account         | \-1,000\.00                                       | 1,000\.00                                         |                                                   | 0\.00                   |   | 1,000                                           |                                                | \-1,000                                        |                                                |                                                | 0\.00                                   |
| 5          | Accounts payable         |                                                   | \-1,008\.00                                       | 1,008\.00                                         | 0\.00                   |   |                                                 |                                                |                                                |                                                |                                                | 0\.00                                   |
| 6          | ROU asset                |                                                   |                                                   |                                                   | 0\.00                   |   |                                                 | 22,794                                         |                                                |                                                |                                                | 22,793\.90                              |
| 7          | Finance lease obligation |                                                   |                                                   |                                                   | 0\.00                   |   |                                                 | \-22,794                                       | 1,000                                          | \-94\.97                                       |                                                | \-21,888\.87                            |
| 8          | Interest expense         |                                                   |                                                   |                                                   | 0\.00                   |   |                                                 |                                                |                                                | 94\.97                                         |                                                | 94\.97                                  |
| 9          | Cash                     |                                                   |                                                   | \-1,008\.00                                       | \-1,008\.00             |   |                                                 |                                                |                                                |                                                |                                                | \-1,008\.00                             |
| 10         | Depreciation expense     |                                                   |                                                   |                                                   | 0\.00                   |   |                                                 |                                                |                                                |                                                | 949\.75                                        | 949\.75                                 |
| 11         | Accumulated depreciation |                                                   |                                                   |                                                   | 0\.00                   |   |                                                 |                                                |                                                |                                                | \-949\.75                                      | \-949\.75                               |




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
