---
# required metadata

title: Transition methods
description: This topic describes the three transition methods that are compliant with International Financial Reporting Standard 16 (IFRS 16). These methods are named full retrospective, cumulative catch-up option A, and cumulative catch-up option B.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Transition methods

[!include [banner](../includes/banner.md)]

This topic describes the three transition methods that are compliant with International Financial Reporting Standard 16 (IFRS 16):

- Full retrospective
- Cumulative catch-up option A
- Cumulative catch-up option B

Asset leasing includes all three transition methods.

## Full retrospective

The full retrospective method treats the lease as if IFRS 16 has always been applied, starting on the original commencement date. The payments are discounted by using the incremental borrowing rate as of the commencement date. Therefore, all schedules are created forward from the commencement date.

- **Lease liability** – The ending balance from the liability amortization schedule in the period immediately before the transition date.
- **Right-of-use (ROU) asset** – The net book value from the asset depreciation schedule in the period immediately before the transition date.

## Cumulative catch-up

In both cumulative catch-up methods, the comparative periods can stay as they were reported in the past. The differences between the assets and liability are recognized in opening retained earnings on the transition date.

### Cumulative catch-up option A

Like the full retrospective method, the cumulative catch-up option A method creates all schedules forward from the commencement date. However, this method differs from the full retrospective method in that the system calculates the present value of lease payments by using the incremental borrowing rate as of the transition date.

- **Lease liability** – The ending balance from the liability amortization schedule in the period immediately before the transition date.
- **ROU asset** – The net book value from the asset depreciation schedule in the period immediately before the transition date.

### Cumulative catch-up option B

In the cumulative catch-up option B method, schedules are created starting on the transition date. The leases are treated as new leases that have a commencement date that equals the transition date. Payments are discounted by using the incremental borrowing rate as of the transition date.

- **Lease liability** – The sum of the present value of lease payments from the payment schedule.
- **ROU asset** – The sum of the present value of lease payments from the payment schedule, plus any deferred rent carry-over.

## Examples

The following examples show the different transition methods, and the expected beginning balances of the ROU asset and lease liability that the transition adjustment generates. For all these examples, the transition date is January 1, 2020.

### Setup

The following tables show the values that are set on the **General** and **Payment schedule lines** tabs.

**General tab**

| Field                                    | Value       |
|------------------------------------------|-------------|
| Fair value of the asset                  | 600,000     |
| Incremental borrowing rate               | 5%          |
| Incremental borrowing rate at transition | 10%         |
| Compounding interval                     | Monthly     |
| Asset useful life (months)               | 600         |
| Annuity type                             | Annuity due |
| Commencement date                        | 07/01/2019  |

**Payment schedule lines tab**

| Field             | Value      |
|-------------------|------------|
| Start date        | 7/1/2019   |
| Period interval   | Monthly    |
| Periods           | 12         |
| End date          | 06/30/2020 |
| Payment frequency | Monthly    |
| Payment amount    | 1,000      |

### Full retrospective example

In this method, the liability and asset are calculated as if IFRS 16 has always applied to the lease. The liability of the lease is calculated by discounting the sum of the present value of the future minimum lease payments (PVFMLP) by the rate at commencement (5 percent in this example).

- For the period that ended on December 31, 2019, the ending liability balance from the liability amortization schedule is 5,938.10.
- For the period that ended on December 31, 2019, the net book value from the asset depreciation schedule is 5,864.95.

Here is the transition adjustment journal entry:

Dr. Lease asset 5,864.95  
Dr. Retained earnings 73.15  
Cr. Lease liability 5,938.10

### Cumulative catch-up option A example

In this method, the liability and asset are calculated as if IFRS 16 has always applied to the lease. However, the payments are discounted by using the current incremental borrowing rate. The liability of the lease is calculated by discounting the sum of the PVFMLP by the rate at transition (10 percent in this example).

- For the period that ended on December 31, 2019, the ending liability balance from the liability amortization schedule is 5,877.39.
- For the period that ended on December 31, 2019, the net book value from the asset depreciation schedule is 5,734.65.

Here is the transition adjustment journal entry:

Dr. Lease asset 5,734.65  
Dr. Retained earnings 142.74  
Cr. Lease liability 5,877.39

### Cumulative catch-up option B example

In this method, the lease is treated as if it's a new lease that commenced on the transition date. The liability of the lease is calculated by discounting the sum of the PVFMLP from the transition date by the rate at transition (10 percent in this example). The asset equals the liability amount plus any deferred rent carry-over amount.

For the remaining six months, the PVFMLP of 1,000 discounted at a compounded monthly rate of 10 percent is 5,877.39.

Here is the transition adjustment journal entry:

Dr. Lease asset 5,877.39  
Cr. Lease liability 5,877.39
