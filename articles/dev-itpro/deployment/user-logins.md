---
# required metadata

title: Track user logins 
description: This topic provides information about how to create an audit log of users who logged in and used Dynamics 365 for Finance and Operations, Enterprise edition.  
author: manado
manager: AnnBe
ms.date: 11/2/2017
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
ms.search.scope: Operations, Unified Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 12

---
# Track user logins 
 
[!include[banner](../includes/banner.md)]

Many organizations are required to maintain an audit trail of the users who have used the system. This requirement can be for compliance reasons, or to track back in case of incorrect use. In Microsoft Dynamics AX 2012, the **Audit log** form recorded which users accessed the Dynamics AX environment. With Dynamics 365 for Finance and Operations, this information is captured in telemetry and is available for download by using Lifecycle Services for IT administrators. Administrators can then move the downloaded information to their offline storage to maintain the audit trail of who logged in. 
To generate an audit log of who used the system, complete the following steps: 

1. Log into Lifecycle Services and open the project associated with the Dynamics 365 for Finance and Operations implementation. 
2. Navigate to the production environment and open the **Environment details** page.  
3. Under the **Monitoring** tab, click the **Environment monitoring** link  to open the monitoring dashboard.  
4. On the **Activity** tab, click **View raw logs** . 
5. In the **Query** drop-down, select **User Login Events**. This will show a time duration with start date that is set to **End date - 7 days**.  
6. Set the end date and then click **Search**. This will return results on all users that have logged into the system for the last 7 days from the selected end date. 
7. The returned results show the AADUserID and the login start and end time of the user's session. To map the AADUserID with the user name and email, open Dynamics 365 for Finance and Operations and check the **System administration** > **Users** form.  
8. To export the records and keep them for longer time period, click **Export grid**.  

To ensure a complete audit trail, an IT administrator will have to do complete this task every seven days. 


