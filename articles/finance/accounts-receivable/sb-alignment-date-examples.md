---
title: Alignment date scenarios
description: Access examples that show how alignment dates work in Subscription billing, including various scenarios with different levels of alignment.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 07/30/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Alignment date scenarios

This article provides examples that show how alignment dates work in Subscription billing.

For these examples, a billing detail for a billing schedule has an alignment date of October 31, 2019. The first billing detail for the line ends on October 31, 2019 and is prorated accordingly. The line is automatically renewed by using a renewal start date of November 11.

> [!NOTE]
> The year is relevant because it can cause the alignment date to be more or less than a year. For these examples, the proration method is set to **Monthly** on the **Recurring contract billing parameters** page. If you set it to **Daily**, some partial amounts differ.

## No alignment

Set up the billing schedule with the following data:

- **Start date:** May 1, 2023
- **End date:** December 31, 2028
- **Amount:** $1,000

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2023 | 4/30/2024 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2024 | 4/30/2025 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2025 | 4/30/2026 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2026 | 4/30/2027 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2027 | 4/30/2028 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2028 | 12/31/2028 | | | 1.00 | | 1.00 | 666.67 |

## Scenario 2: Shortened alignment

Set up the billing schedule with the following data:

- **Start date:** May 1, 2023
- **End date:** December 31, 2028
- **Amount:** $1,000
- **Alignment date:** December 31, 2023

The first renewal amount is for less than one year.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 666.67 |
| 1/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2025 | 12/31/2025 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2026 | 12/31/2026 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2027 | 12/31/2027 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2028 | 12/31/2028 | | | 1.00 | | 1.00 | 1,000.00 |

## Scenario 3: Extended alignment

Set up the billing schedule with the following data:

- **Start date:** May 1, 2023
- **End date:** December 31, 2028
- **Amount:** $1,000
- **Alignment date:** December 31, 2024

The first renewal amount covers more than one year.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2023 | 12/31/2024 | | | 1.00 | | 1.00 | 1,666.67 |
| 1/1/2025 | 12/31/2025 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2026 | 12/31/2026 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2027 | 12/31/2027 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2028 | 12/31/2028 | | | 1.00 | | 1.00 | 1,000.00 |

### Alignment with a different end month

Set up the billing schedule with the following data:

- **Start date:** May 1, 2023
- **End date:** October 31, 2028
- **Amount:** $1,000
- **Alignment date:** December 31, 2023

> [!NOTE]
> This scenario isn't common.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 666.67 |
| 1/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2025 | 12/31/2025 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2026 | 12/31/2026 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2027 | 12/31/2027 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2028 | 10/31/2028 | | | 1.00 | | 1.00 | 833.33 |

### Single partial year

Set up the billing schedule with the following data:

- **Start date:** May 1, 2023
- **End date:** December 31, 2023
- **Amount:** $1,000
- **Alignment date**: December 31, 2023

In this scenario, you don't need the alignment date. This scenario is common for automatic renewals.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 666.67 |

### Calculated dates

Set up the support and renewal with the following data:

- **Override start date:** No
- **Support and renewal start dates:** Beginning of next month
- **Invoice posting date:** June 22, 2023
- **Alignment date:** December 31, 2024

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 7/1/2023 | 7/31/2023 | | | 1.00 | | 1.00 | 297.60 |
| 8/1/2023 | 12/31/2024 | | | 1.00 | | 1.00 | 6,936.00 |

### Calculated dates and future posting

Set up the support and renewal with the following data:

- **Override start date:** No
- **Support and renewal start dates:** Beginning of next month
- **Invoice posting date:** June 22, 2023
- **Alignment date:** December 31, 2024

For this scenario, change the alignment date to December 31, 2021.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2023 | 6/22/2023 | | | 1.00 | | 1.00 | 0.00 |
| 8/1/2023 | 12/31/2024 | | | 1.00 | | 1.00 | 4,250.00 |

### Manual dates and multiple years

Set up the support and renewal with the following data:

- **Override start date:** Yes
- **Renewal start date:** July 1,2024
- **Renewal end date:** December 31, 2028
- **Alignment date:** December 31, 2025

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2023 | 6/22/2023 | | | 1.00 | | 1.00 | 0.00 |
| 7/1/2024 | 12/31/2025 | | | 1.00 | | 1.00 | 375.00 |
| 1/1/2026 | 12/31/2026 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2027 | 12/31/2027 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/20228 | 12/31/2028 | | | 1.00 | | 1.00 | 250.00 |

### Manual dates, multiple years, and a different end month

Set up the support and renewal with the following data:

- **Override start date:** Yes
- **Renewal start date:** July 1, 2024
- **Renewal end date:** October 31, 2028
- **Alignment date:** December 31, 2025

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2023 | 6/22/2023 | | | 1.00 | | 1.00 | 0.00 |
| 7/1/2023| 12/31/2024 | | | 1.00 | | 1.00 | 375.00 |
| 1/1/2025 | 12/31/2025 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2026 | 12/31/2026 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2027 | 10/31/2027 | | | 1.00 | | 1.00 | 208.33 |

### Alignment without proration

Set up the support and renewal with the following data:

- **Override start date:** No
- **Invoice posting date:** June 22, 2023
- **Alignment date:** December 31, 2023

The renewal start date and the alignment dates are adjusted so that both start dates are after the posting date.

- **Renewal start date:** January 1, 2024
- **Renewal end date:** December 31, 2024
