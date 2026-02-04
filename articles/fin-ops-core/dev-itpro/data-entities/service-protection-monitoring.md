---
title: Monitor API throttling
description: Learn about the tools that are available to monitor application programming interface (API) throttling when service protection limits are reached.
author: jaredha
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.topic: how-to
ms.date: 01/14/2026
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2022-04-16
ms.search.form: 
ms.dyn365.ops.version: Platform update 52
---

# Monitor API throttling

[!include [banner](../includes/banner.md)]

This article provides information about the tools that are available to monitor usage of application programming interfaces (APIs). This usage includes queries that display information on API requests that the system throttled when it reached [service protection limits](service-protection-api-limits.md). It also includes general API usage to help administrators understand when integrations might be nearing the API limits.

To successfully onboard with the throttling capability, you must monitor your Open Data Protocol (OData) and custom service integration patterns. Microsoft Dynamics Lifecycle Services (LCS), which is the administration center for finance and operations apps, contains a collection of monitoring and diagnostics tools that can help ensure you have an accurate view of the environments you manage. For more information, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](../lifecycle-services/monitoring-diagnostics.md).

These queries enable you to get raw logs with data related to administration of the service. You can then export the logs for more advanced analysis.

## Requests throttled

Use the predefined **Requests throttled** query to see the list of API requests that the system throttled in a given date and time range due to exceeding service protection API limits.

To view throttling activity in the monitoring and diagnostics portal, follow these steps:

1. In LCS, open the appropriate project.
1. In the **Environments** section, select the environment to view, and then select **Full details**.
1. On **Environment details**, select **Environment monitoring** to open the monitoring and diagnostics portal.
1. On **Environment monitoring**, select the **Activity** tab to view the **Raw logs**.
1. Select the query name, and then select **Requests throttled** for all OData and custom service requests that the system throttled.
1. Select **Search**.

## Summarized API requests by application and user

The **Summarized API requests by application and user** query provides a summarized view of the API requests for a Microsoft Entra user and application. You can use this report to compare usage to service protection API limits. For the selected user and application, the query displays:

- The total number of API requests in the selected date and time range.
- The total execution time of the API requests in the selected date and time range.

The results are summarized in five-minute intervals, similar to the five-minute sliding window of [user-based service protection API limits](service-protection-api-limits.md#user-based-service-protection-api-limits).

To view the summarized data:

1. In LCS, open the appropriate project.
1. In the **Environments** section, select the environment to view, and then select **Full details**.
1. On **Environment details**, select **Environment monitoring** to open the monitoring and diagnostics portal.
1. On **Environment monitoring**, select the **Activity** tab to view the **Raw logs**.
1. Select the query name, and then select **Summarized API requests by application and user**.
1. Enter the following information in the query options:
    - **Start date**: The date and time for the beginning of the range for which you want to see the API usage data.
    - **End date**: The date and time for the end of the range for which you want to see the API usage data.
    - **User object ID**: The Microsoft Entra ID user object ID of the user.
    - **Application ID**: The Microsoft Entra application ID of the integrating application that uses the APIs.
1. Select **Search**.

## API requests by application and user

The **API requests by application and user** query shows the list of API requests made by a specific user and application during a selected date and time range. For each record, the query shows:

- The timestamp of the request
- The Microsoft Entra user ID of the user making the API request
- The Microsoft Entra application ID of the request
- The AOS node where the request was made
- The URL of the API request
- The total execution time of the request

To view the data for the query:

1. In LCS, open the appropriate project.
1. In the **Environments** section, select the environment to view, and then select **Full details**.
1. On **Environment details**, select **Environment monitoring** to open the monitoring and diagnostics portal.
1. On **Environment monitoring**, select the **Activity** tab to view the **Raw logs**.
1. Select the query name, and then select **API requests by application and user**.
1. Enter the following information in the query options:
    - **Start date**: The date and time for the beginning of the range for which you want to see the API usage data.
    - **End date**: The date and time for the end of the range for which you want to see the API usage data.
      > [!NOTE]
      > The maximum range of time allowed for the query is 20 minutes. Set the **End date** value to no more than 20 minutes after the **Start date** value.

    - **User object ID**: The Microsoft Entra ID user object ID of the user.
    - **Application ID**: The Microsoft Entra application ID of the integrating application that uses the APIs.
1. Select **Search**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
