---
# required metadata

title: Monitor API throttling
description: This topic provides information about the tools that are available to monitor application programming interface (API) throttling when service protection limits are reached.
author: jaredha
ms.date: 04/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2022-04-16
ms.dyn365.ops.version: Platform update 52

---

# Monitor API throttling

[!include [banner](../includes/banner.md)]

This topic provides information about the tools that are available to monitor application programming interface (API) throttling when service protection limits are reached.

To have a successful onboarding experience that includes the throttling capability, you must be able to monitor your Open Data Protocol (OData) and custom service integration patterns. Microsoft Dynamics Lifecycle Services (LCS), which is the administration center for Dynamics 365 Finance + Operations apps, contains a collection of monitoring and diagnostics tools that can help ensure that you have an accurate view of the environments that you manage. For more information, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](../lifecycle-services/monitoring-diagnostics.md).

You can use the predefined **Requests throttled** query to get raw logs for an issue. You can then export the logs for more advanced analysis.

To view throttling activity in the monitoring and diagnostics portal, follow these steps.

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the query name, and then select **Requests throttled** for all OData and custom service requests that have been throttled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
