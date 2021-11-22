---
# required metadata

title: Compounding interval functionality
description: This topic provides information that will help you choose among monthly, quarterly, semiannual, and annual compounding intervals.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseDetail
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Compounding interval functionality

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic provides information that will help you choose among monthly, quarterly, semiannual, and annual compounding intervals. The compounding interval functionality is used to determine the number of compounding periods per year in a lease's payment schedule. Each of the four examples in this topic shows what a lease's payment schedule will look like for a different interval.

You can't select a compounding interval that is less frequent than the lease's payment frequency. For example, a quarterly compounding interval can't be used with a monthly payment frequency, and an annual compounding interval can't be used with a semiannual payment frequency. If you try to select a compounding interval that is less frequent than the lease's payment frequency, you receive an error message.

> [!NOTE]
> In all four examples in this topic, the compounding interval matches the payment frequency.

## Examples

### Setup for all four leases

The following tables show the values that are set on the **General** and **Payment schedule lines** tabs for the four leases that are used in the examples.

**General tab**

| Field                      | Value                        |
|----------------------------|------------------------------|
| Incremental borrowing rate | **5%**                       |
| Annuity type               | **Ordinary annuity**         |
| Compounding interval       | See the individual examples. |
| Payment frequency          | **Monthly**                  |
| Commencement date          | **1/1/2020**                 |

**Payment schedule lines tab**

| Field             | Value                        |
|-------------------|------------------------------|
| Start date        | **1/1/2020**                 |
| Periods           | **120**                      |
| Period interval   | **Months**                   |
| End date          | **12/31/2029**               |
| Payment frequency | See the individual examples. |
| Payment amount    | **50,000**                   |

### Lease 1: Monthly compounding interval and monthly payment frequency

The following table lists the first 12 months of the payment schedule. Note the following details:

- The value in the "Period" column increases by 1 every month, because each month is a new compounding interval.
- In the formula in the "Present value" column, the rate is divided by 12, because there are 12 compounding periods per year. The exponent (that is, the superscript numeral) equals the value in the "Period" column.

| Period | Month | Date       | Payment amount | Present value                                       |
|--------|-------|------------|----------------|-----------------------------------------------------|
| 1      | 1     | 1/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>1</sup> = 49,792.53  |
| 2      | 2     | 2/29/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>2</sup> = 49,585.92  |
| 3      | 3     | 3/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>3</sup> = 49,380.17  |
| 4      | 4     | 4/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>4</sup> = 49,175.28  |
| 5      | 5     | 5/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>5</sup> = 48,971.23  |
| 6      | 6     | 6/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>6</sup> = 48,768.03  |
| 7      | 7     | 7/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>7</sup> = 48,565.67  |
| 8      | 8     | 8/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>8</sup> = 48,364.15  |
| 9      | 9     | 9/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>9</sup> = 48,163.47  |
| 10     | 10    | 10/31/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>10</sup> = 47,963.62 |
| 11     | 11    | 11/30/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>11</sup> = 47,764.61 |
| 12     | 12    | 12/31/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 12\])<sup>12</sup> = 47,566.41 |

### Lease 2: Quarterly compounding interval and quarterly payment frequency

The following table lists the first 12 months of the payment schedule. Note the following details:

- The value in the "Period" column increases by 1 every three months (that is, every quarter), because each quarter is a new compounding interval.
- In the formula in the "Present value" column, the rate is divided by 4, because there are four compounding periods per year. The exponent equals the value in the "Period" column.

| Period | Month | Date       | Payment amount | Present value                                     |
|--------|-------|------------|----------------|---------------------------------------------------|
| 1      | 1     | 1/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>1</sup> = 0           |
| 1      | 2     | 2/29/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>1</sup> = 0           |
| 1      | 3     | 3/31/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 4\])<sup>1</sup> = 49,382.72 |
| 2      | 4     | 4/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>2</sup> = 0           |
| 2      | 5     | 5/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>2</sup> = 0           |
| 2      | 6     | 6/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 4\])<sup>2</sup> = 48,773.05 |
| 3      | 7     | 7/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>3</sup> = 0           |
| 3      | 8     | 8/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>3</sup> = 0           |
| 3      | 9     | 9/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 4\])<sup>3</sup> = 48,170.92 |
| 4      | 10    | 10/31/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>4</sup> = 0           |
| 4      | 11    | 11/30/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 4\])<sup>4</sup> = 0           |
| 4      | 12    | 12/31/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 4\])<sup>4</sup> = 47,576.21 |

> [!NOTE]
> If the annuity type is changed to **Annuity due**, the payment will be at the beginning of the quarter instead of the end of the quarter.

### Lease 3: Semiannual compounding interval and semiannual payment frequency

The following table lists the first 12 months of the payment schedule. Note the following details:

- The value in the "Period" column increases by 1 every six months (that is, semiannually), because each half-year is a new compounding interval.
- In the formula in the "Present value" column, the rate is divided by 2, because there are two compounding periods per year. The exponent equals the value in the "Period" column.

| Period | Month | Date       | Payment amount | Present value                                     |
|--------|-------|------------|----------------|---------------------------------------------------|
| 1      | 1     | 1/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 0           |
| 1      | 2     | 2/29/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 0           |
| 1      | 3     | 3/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 0           |
| 1      | 4     | 4/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 0           |
| 1      | 5     | 5/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 0           |
| 1      | 6     | 6/30/2020  | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 2\])<sup>1</sup> = 48,780.49 |
| 2      | 7     | 7/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 0           |
| 2      | 8     | 8/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 0           |
| 2      | 9     | 9/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 0           |
| 2      | 10    | 10/31/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 0           |
| 2      | 11    | 11/30/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 0           |
| 2      | 12    | 12/31/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 2\])<sup>2</sup> = 47,590.72 |

> [!NOTE]
> If the annuity type is changed to **Annuity due**, the payment will be in January and July instead of June and December.

### Lease 4: Annual compounding interval and annual payment frequency

The following table lists the first 12 months of the payment schedule. Note the following details:

- The value in the "Period" column increases by 1 every 12 months (that is, annually), because each year is a new compounding interval.
- In the formula in the "Present value" column, the rate is divided by 1, because there is one compounding period per year. The exponent equals the value in the "Period" column.

| Period | Month | Date       | Payment amount | Present value                                     |
|--------|-------|------------|----------------|---------------------------------------------------|
| 1      | 1     | 1/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 2     | 2/29/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 3     | 3/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 4     | 4/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 5     | 5/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 6     | 6/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 7     | 7/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 8     | 8/31/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 9     | 9/30/2020  | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 10    | 10/31/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 11    | 11/30/2020 | 0.00           | 0.00 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 0           |
| 1      | 12    | 12/31/2020 | 50,000.00      | 50,000 ÷ (1 + \[5% ÷ 1\])<sup>1</sup> = 47,619.05 |

> [!NOTE]
> If the annuity type is changed to **Annuity due**, the payment will be in January instead of December.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
