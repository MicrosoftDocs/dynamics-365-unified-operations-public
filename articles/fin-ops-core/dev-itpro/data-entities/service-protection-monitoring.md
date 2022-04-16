---
# required metadata

title: Monitoring for API throttling
description: This topic provides information about tools available to monitor API throttling when service protection limits are reached.
author: jaredha
ms.date: 04/06/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2022-04-16
ms.dyn365.ops.version: Platform update 52

---

# Monitoring for API throttling

[!include [banner](../includes/banner.md)]

To have a successful onboarding experience with the throttling capability, you must also be able to monitor your OData and custom service integration patterns. Microsoft Dynamics Lifecycle Services (LCS), which is the administration center for Finance and Operations apps, contains a collection of monitoring and diagnostics tools that can help ensure that you have an accurate view of the environments you manage. For more information, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](../lifecycle-services/monitoring-diagnostics.md).

You can use the predefined **Requests throttled** query to get raw logs for an issue. You can then export the logs for a more advanced analysis.

To view throttling activity in the **Monitoring and diagnostics** portal:

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the Monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the **Query name**, and then select **Requests throttled** for all OData and custom services requests that have been throttled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
