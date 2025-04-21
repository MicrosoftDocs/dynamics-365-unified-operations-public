---
title: Correction of deferral schedule and unbilled revenue calculation during subscription termination
description: Learn about the correction of deferral schedule and unbilled revenue calculation during subscription termination.
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: article
ms.date: 04/21/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.search.form: CustPosting, CustVendExternalItem
ms.dyn365.ops.version: 10.0.25
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Correction of deferral schedule and unbilled revenue calculation during subscription termination

[!include [banner](../includes/banner.md)]

In version 10.0.44 of Dynamics 365 Finance, Microsoft has addressed a critical issue where deferral schedules and unbilled revenue audit entries were calculated incorrectly when subscription billing contracts were terminated with refunds. This issue previously prevented accurate credit note generation and led to inconsistent financial reporting.

When a subscription contract is fully terminated and a refund is issued, the system is expected to reverse the relevant amounts in both the deferral schedule and unbilled revenue audit entries. However, prior to 
this fix, the system incorrectly calculated these values, particularly when currency exchange rate differences were involved.
To address the issue, Microsoft introduced a fix in version 10.0.44 that ensures the termination adjustment is calculated using the exchange rate effective on the termination date. The system now computes the 
difference due to currency fluctuation and automatically posts it to the designated Profit & Loss account. While the adjustment invoice proposal continues to post the original reversal. The deferral schedule 
clearly shows the adjusted totals and includes a complete audit trail for transparency.
This correction ensures accurate financial reporting, enables timely credit note issuance, and supports compliance in revenue recognition. It is particularly critical for customers in the final stages of 
deployment, helping prevent revenue loss and ensuring readiness for go-live.
