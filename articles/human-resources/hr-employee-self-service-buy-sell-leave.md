---
# required metadata

title: Buy and sell leave
description: This article describes how to submit requests to buy and sell leave in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to
# optional metadata

ms.search.form: ESSLeaveBuyRequestEntry, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Human Resources

---

# Buy and sell leave

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Dynamics 365 Human Resources, you can submit requests to buy and sell leave based on the buy and sell leave policies that your company sets up.  

## Request to buy leave

1. In the **Employee self service** workspace, select **Buy leave request** in the **Time Off balances** tile.

1. Add a **Leave type** and enter an **Amount** for the amount of leave you want to buy.

1. Select **Submit** when you're ready to submit your request.

Your balances either automatically update or go through an approval process before updating, depending on how the buy policy is configured.

## Request to sell leave

1. In the **Employee self service** workspace, select **Sell leave request** in the **Time Off balances** tile.

1. Add a **Leave type** and enter an **Amount** for the amount of leave you want to sell.

1. Select **Submit** when you're ready to submit your request.

Your balances either automatically update or go through an approval process before updating. This process depends on how the buy policy is configured.

## Troubleshooting

If a buy or sell leave request workflow fails, users with the **EssLeaveBuySellRequestApprover** privilege can review the message log for all leave buy and sell requests. To do this, go to **Leave and absence > Links > Buy and sell leave requests > Message log** (on the upper left). The **Message log** shows users how the transactions were processed and the associated workflow history.

## See also

[Leave and absence overview](hr-leave-and-absence-overview.md)</br>
[Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
