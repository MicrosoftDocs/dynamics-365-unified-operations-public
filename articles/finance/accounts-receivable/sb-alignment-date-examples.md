---
# required metadata

title: Alignment date scenarios
description: This topic provides examples that show how alignment dates work in Subscription billing.
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Alignment date scenarios

This topic provides examples that show how alignment dates work in Subscription billing.

For these examples, a billing detail for a billing schedule has an alignment date of October 31, 2019. The first billing detail for the line ends on October 31, 2019 and is prorated accordingly. The line is automatically renewed by using a renewal start date of November 11.

> [!NOTE]
> The year is relevant because it can cause the alignment date to be more or less than a year. For these examples, the proration method is set to **Monthly** on the **Recurring contract billing parameters** page. If it's set to **Daily**, some partial amounts will differ.

## Scenario 1: No alignment

The billing schedule is set up with the following data:

- **Start date:** May 1, 2019
- **End date:** December 31, 2024
- **Amount:** $1,000

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2019 | 4/30/2020 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2020 | 4/30/2021 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2021 | 4/30/2022 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2022 | 4/30/2023 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2023 | 4/30/2024 | | | 1.00 | | 1.00 | 1,000.00 |
| 5/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 666.67 |

## Scenario 2: Shortened alignment

The billing schedule is set up with the following data:

- **Start date:** May 1, 2019
- **End date:** December 31, 2024
- **Amount:** $1,000
- **Alignment date:** December 31, 2019

The first renewal amount is for less than one year.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2019 | 12/31/2019 | | | 1.00 | | 1.00 | 666.67 |
| 1/1/2020 | 12/31/2020 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2021 | 12/31/2021 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2022 | 12/31/2022 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 1,000.00 |

## Scenario 3: Extended alignment

The billing schedule is set up with the following data:

- **Start date:** May 1, 2019
- **End date:** December 31, 2024
- **Amount:** $1,000
- **Alignment date:** December 31, 2020

The first renewal amount is for more than one year.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2019 | 12/31/2020 | | | 1.00 | | 1.00 | 1,666.67 |
| 1/1/2021 | 12/31/2021 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2022 | 12/31/2022 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 1,000.00 |

## Scenario 4: Alignment with a different end month

The billing schedule is set up with the following data:

- **Start date:** May 1, 2019
- **End date:** October 31, 2024
- **Amount:** $1,000
- **Alignment date:** December 31, 2019

> [!NOTE]
> This scenario isn't common.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2019 | 12/31/2019 | | | 1.00 | | 1.00 | 666.67 |
| 1/1/2020 | 12/31/2020 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2021 | 12/31/2021 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2022 | 12/31/2022 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 1,000.00 |
| 1/1/2024 | 10/31/2024 | | | 1.00 | | 1.00 | 833.33 |

## Scenario 5: Single partial year

The billing schedule is set up with the following data:

- **Start date:** May 1, 2019
- **End date:** December 31, 2019
- **Amount:** $1,000
- **Alignment date**: December 31, 2019

In this scenario, the alignment date isn't needed. This scenario is common for automatic renewals.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 5/1/2019 | 12/31/2019 | | | 1.00 | | 1.00 | 666.67 |

## Scenario 6: Calculated dates

The support and renewal is set up with the following data:

- **Override start date:** No
- **Support and renewal start dates:** Beginning of next month
- **Invoice posting date:** June 22, 2019
- **Alignment date:** December 31, 2020

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 7/1/2019 | 7/31/2019 | | | 1.00 | | 1.00 | 297.60 |
| 8/1/2019 | 12/31/2020 | | | 1.00 | | 1.00 | 6,936.00 |

## Scenario 7: Calculated dates and future posting

The support and renewal is set up with the following data:

- **Override start date:** No
- **Support and renewal start dates:** Beginning of next month
- **Invoice posting date:** June 22, 2019
- **Alignment date:** December 31, 2020

For this scenario, the alignment date is changed to December 31, 2021.

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2019 | 6/22/2019 | | | 1.00 | | 1.00 | 0.00 |
| 8/1/2019 | 12/31/2020 | | | 1.00 | | 1.00 | 4,250.00 |

## Scenario 8: Manual dates and multiple years

The support and renewal is set up with the following data:

- **Override start date:** Yes
- **Renewal start date:** July 1,2020
- **Renewal end date:** December 31, 2024
- **Alignment date:** December 31, 2021

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2019 | 6/22/2019 | | | 1.00 | | 1.00 | 0.00 |
| 7/1/2020 | 12/31/2021 | | | 1.00 | | 1.00 | 375.00 |
| 1/1/2022 | 12/31/2022 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2024 | 12/31/2024 | | | 1.00 | | 1.00 | 250.00 |

## Scenario 9: Manual dates, multiple years, and a different end month

The support and renewal is set up with the following data:

- **Override start date:** Yes
- **Renewal start date:** July 1, 2020
- **Renewal end date:** October 31, 2024
- **Alignment date:** December 31, 2021

| Billing start date | Billing end date | Previous reading | Current reading | Quantity entered | Free quantity | Billable quantity | Unit price |
|---|---|---|---|---|---|---|---|
| 6/22/2019 | 6/22/2019 | | | 1.00 | | 1.00 | 0.00 |
| 7/1/2020 | 12/31/2021 | | | 1.00 | | 1.00 | 375.00 |
| 1/1/2022 | 12/31/2022 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2023 | 12/31/2023 | | | 1.00 | | 1.00 | 250.00 |
| 1/1/2024 | 10/31/2024 | | | 1.00 | | 1.00 | 208.33 |

## Scenario 10: Alignment without proration

The support and renewal is set up with the following data:

- **Override start date:** No
- **Invoice posting date:** June 22, 2019
- **Alignment date:** December 31, 2019

The renewal start date and the alignment dates are adjusted so that both start dates are after the posting date.

- **Renewal start date:** January 1, 2020
- **Renewal end date:** December 31, 2020
