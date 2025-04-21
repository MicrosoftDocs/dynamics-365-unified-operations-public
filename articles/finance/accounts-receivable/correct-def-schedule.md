---
title: Calculation of deferral schedule and unbilled revenue during subscription termination
description: Learn about the correct calculation of deferral schedule and unbilled revenue during subscription termination.
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

# Correct calculation of deferral schedule and unbilled revenue during subscription termination

[!include [banner](../includes/banner.md)]

In version 10.0.44 of Dynamics 365 Finance, the termination adjustment is calculated using the exchange rate effective on the termination date.

## Previous releases 
When a subscription contract is terminated and a refund is issued, the relevant amounts should be reversed in both the deferral schedule and unbilled revenue audit entries. Prior to the Dynamics 365 Finance 10.0.44 release, these values were incorrectly calculated, particularly when currency exchange rate differences were involved. 

### Correct calculation of adjustment
Starting in Dynamics 365 Finance version 10.0.44, the termination adjustment is calculated using the effective exchange rate on the termination date. The difference is calculated due to currency fluctuation and automatically posts it to the designated profit and loss account. While the adjustment invoice proposal continues to post the original reversal. The deferral schedule displays the adjusted totals and includes a complete audit trail for transparency. 

This correction ensures accurate financial reporting, enables timely credit note issuance, and supports compliance in revenue recognition. 
