---
title: Data maintenance job for backfilling deferral schedule 
description: Learn how to backfill deferral schedule lines in Microsoft Dynamics 365 Finance. 
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: how-to
ms.date: 08/13/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Data maintenance job for backfilling deferral schedule line fields

[!include [banner](../includes/banner.md)]

This article explains how to backfill deferral schedule lines in Microsoft Dynamics 365 Finance. 

## Data maintenance
Beginning in Microsoft Dynamics 365 Finance version 10.0.45, there's an option for the user to run the data maintenance job for backfilling Deferral schedule line fields. This data maintenance job is designed to 
backfill essential fields (Voucher, JournalNum, and TransDate) in the SubBillDeferralScheduleLine table. The values are fetched by referencing the corresponding data from the LedgerJournalTrans table. 


To run the data maintenance job, follow these steps:
1. Go to **System administration** > **Periodic tasks** > **Data maintenance**.
2. Deferral schedule lines may exist without journal information due to historical gaps or technical constraints during migration. This job ensures that the SubBillDeferralScheduleLine table is
properly linked to its originating ledger journal transactions.
3. The goal of this job is to ensure data consistency and accurate journal linkage for each deferral schedule line.
4. This job isn't scheduled by default and must be run manually by the user. It's intended as a one-time data correction task, typically after an upgrade, migration, or initial setup of the Subscription billing
module. Users can rerun the job if data discrepancies are later identified.


