---
# required metadata

title: Buy and sell leave
description: In Dynamics 365 Human Resources, you can submit requests to buy and sell leave based on the buy and sell leave policies set up by your company.
author: andreabichsel
ms.date: 08/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ESSLeaveBuyRequestEntry, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Human Resources

---

# Buy and sell leave

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Dynamics 365 Human Resources, you can submit requests to buy and sell leave based on the buy and sell leave policies set up by your company.  

## Request to buy leave

1. In the **Employee self service** workspace, select **Buy leave request** in the **Time Off Balances** tile. 

2. Add a **Leave type** and enter an **Amount** for the amount of leave you'd like to buy. 

3. Select **Submit** when you're ready to submit your request. 

Your balances will either automatically update or go through an approval process before updating. This depends on how the buy policy has been configured.

## Request to sell leave

1. In the **Employee self service** workspace, select **Sell leave request** in the **Time Off Balances** tile. 

2. Add a **Leave type** and enter an **Amount** for the amount of leave you'd like to sell. 

3. Select **Submit** when you're ready to submit your request.

Your balances will either automatically update or go through an approval process before updating. This depends on how the buy policy has been configured.


## Troubleshooting 

In case a buy or sell leave request workflow errors out or fails, administrators or users with **EssLeaveBuySellRequestApprover** privilege can review the message log for all leave buy and sell requests via this form: Leave and absence -> Link -> Buy and sell leave requests -> Message log (on the top left). The **Message log** should inform the users for how the transactions were processed and be able to view the associated workflow history. 

## See also

[Leave and absence overview](hr-leave-and-absence-overview.md)</br>
[Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
