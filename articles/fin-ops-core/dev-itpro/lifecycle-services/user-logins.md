---
title: Track user sign-ins 
description: Learn about how to create an audit log of users who signed into your Dynamics environments and used finance and operations apps.
author: angelmarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 12
ms.assetid: 
---

# Track user sign-ins
 
[!include [banner](../includes/banner.md)]

Many organizations need to maintain an audit trail of users who use the system. This requirement can be in place for compliance reasons, or to enable trackbacks in the event of incorrect use.

In Microsoft Dynamics AX 2012, the **Audit log** form recorded which users accessed the Microsoft Dynamics AX environment. In Microsoft Dynamics 365 finance and operations apps, telemetry captures this information. IT administrators can use Microsoft Dynamics Lifecycle Services to download this information and then move it to offline storage to maintain the audit trail of users who sign in.

To generate an audit log of users who use the system, follow these steps:

1. Sign in to Lifecycle Services, and open the project that's associated with your implementation.
1. Go to the production environment, and open the **Environment details** page.
1. On the **Monitoring** tab, select the **Environment monitoring** link to open the monitoring dashboard.
1. On the **Activity** tab, select **View raw logs**.
1. In the **Query** field, select **User Login Events**. You see a time duration that has a start date that's set to **End date - 7 days**.
1. Set the end date, and then select **Search**. The search results include all users who signed in to the system during the seven days before the selected end date.
1. The search results show the **Microsoft Entra IDUserID** value and the sign-in start and end times of the user's session. To map the **Microsoft Entra IDUserID** value to the user's user name and email address, use the **Users** page (**System administration** > **Users**).
1. To export the records and keep them for a longer period, select **Export grid**.

To help guarantee a complete audit trail, an IT administrator must complete this procedure every seven days.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
