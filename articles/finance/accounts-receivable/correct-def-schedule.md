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

## Previous releases 
When a subscription contract is fully terminated and a refund is issued, the relevant amounts should be reveresed in both the deferral schedule and unbilled revenue audit entries. Prior to this release, these values were incorrectly calculated, particularly when currency exchange rate differences were involved.

### Correct calculation of adjustment
Starting in Dynamics 365 version 10.0.44, the termination adjustment is calculated using the exchange rate effective on the termination date. The difference is calculated due to currency fluctuation and automatically posts it to the designated profit and loss account. While the adjustment invoice proposal continues to post the original reversal. The deferral schedule displays the adjusted totals and includes a complete audit trail for transparency. 

This correction ensures accurate financial reporting, enables timely credit note issuance, and supports compliance in revenue recognition. 
