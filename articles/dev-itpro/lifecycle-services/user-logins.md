---
# required metadata

title: Track user sign-ins 
description: This topic explains how to create an audit log of users who have signed in and used Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: manado
manager: AnnBe
ms.date: 11/02/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 12

---
# Track user sign-ins 
 
[!include[banner](../includes/banner.md)]

Many organizations are required to maintain an audit trail of users who have used the system. This requirement can be in place for compliance reasons, or to enable trackbacks in the event of incorrect use.

In Microsoft Dynamics AX 2012, the **Audit log** form recorded which users accessed the Microsoft Dynamics AX environment. In Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, this information is captured in telemetry. IT administrators can download this information by using Microsoft Dynamics Lifecycle Services (LCS) and then move it to offline storage to maintain the audit trail of users who have signed in.

To generate an audit log of users who have used the system, follow these steps.

1. Sign in to LCS, and open the project that is associated with the Finance and Operations implementation.
2. Navigate to the production environment, and open the **Environment details** page.
3. On the **Monitoring** tab, select the **Environment monitoring** link to open the monitoring dashboard.
4. On the **Activity** tab, select **View raw logs**.
5. In the **Query** field, select **User Login Events**. You see a time duration that has a start date that is set to **End date - 7 days**.
6. Set the end date, and then select **Search**. The search results that are returned include all users who signed in to the system during the seven days before the selected end date.
7. The search results show the **AADUserID** value and the sign-in start and end times of the user's session. To map the **AADUserID** value to the user's user name and email address, use the **Users** page in Finance and Operations (**System administration** > **Users**).
8. To export the records and keep them for a longer period, select **Export grid**.

To help guarantee a complete audit trail, an IT administrator must complete this procedure every seven days.
