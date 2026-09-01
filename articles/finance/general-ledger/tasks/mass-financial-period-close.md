--- 
title: Mass financial period close
description: Learn how to place a period on hold or permanently close a period or more than one legal entity at a time with a step-by-step process. 
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 08/05/2026
ms.custom:
ms.reviewer: twheeloc    
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerCalendar, LedgerPeriodModuleAccessControlUpdate, SysLookupPicklist, LedgerFiscalCalendarPeriodStatus
ms.dyn365.ops.version: Version 7.0.0 
---

# Mass financial period close

[!INCLUDE [banner](../../includes/banner.md)]

This article shows how to place a period on hold or permanently close a period for one or more legal entities. In addition, it shows how to restrict user group posting to specific modules.

1. Go to **General ledger > Period close > Ledger calendars**.

>[!NOTE]
> The list of legal entities depends on the fiscal calendar you select on the page. You see only legal entities that use the selected fiscal calendar.

1. Select **Edit**.
1. Select the period for which you want to modify the status.
1. Select the legal entities for which you want to update the status. To quickly select all legal entities, select the check mark on the upper left side of the grid.  
1. Select **Update module access** to define the posting access to a selected module. You can also update the module status one-by-one by editing the records in the grid. The button is useful when you want to quickly update multiple legal entity records.  
1. In the **Application** module, select the module that you want to update the status. Select **Select**.
1. In the **Access** level, select **All**, **None**, or a specific user group. Select **Select**.  

- **All** - All users with edit access to the module can post if the period is open.
- **None** - Users can't post to the module if the period is open. A specific user group indicates only users in the group can post to the module if the period is open.  

1. Select **Update**.
1. Select another period to update the status.
1. Select the legal entities for which you want to update the period status.
1. Select **Update period status** and set the status to **On hold**, **Open**, or **Permanently closed**. **Open** indicates the period can be posted to, provided the user has access. **On hold** means the period can't be posted to, but the period can be reopened. **Permanently closed** means the period is closed and can never be opened. Adjustments can't be posted. Don't set a period to **Permanently closed** until all adjustments and audits are complete.  
1. Select **Update**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
