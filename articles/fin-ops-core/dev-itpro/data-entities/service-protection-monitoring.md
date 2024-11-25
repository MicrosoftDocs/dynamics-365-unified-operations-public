---
title: Monitor API throttling
description: Learn about the tools that are available to monitor application programming interface (API) throttling when service protection limits are reached.
author: jaredha
ms.author: sumadhey
ms.topic: article
ms.date: 08/25/2022
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2022-04-16
ms.search.form: 
ms.dyn365.ops.version: Platform update 52
---

# Monitor API throttling

[!include [banner](../includes/banner.md)]

This article provides information about the tools that are available to monitor usage of application programming interfaces (APIs). This includes queries that display information on API requests that have been throttled when [service protection limits](service-protection-api-limits.md) have been reached, as well as general API usage to help administrators understand when integrations may be nearing the API limits.

To have a successful onboarding experience that includes the throttling capability, you must be able to monitor your Open Data Protocol (OData) and custom service integration patterns. Microsoft Dynamics Lifecycle Services (LCS), which is the administration center for finance and operations apps, contains a collection of monitoring and diagnostics tools that can help ensure that you have an accurate view of the environments that you manage. For more information, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](../lifecycle-services/monitoring-diagnostics.md).

These queries enable you to get raw logs with data related to administration of the service. You can then export the logs for more advanced analysis.

## Requests throttled

You can use the predefined **Requests throttled** to see the list of API requests that have been throttled in a given date/time range due to exceeding service protection API limits.

To view throttling activity in the monitoring and diagnostics portal, follow these steps.

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the query name, and then select **Requests throttled** for all OData and custom service requests that have been throttled.
6. Select **Search**.

## Summarized API requests by application and user

The **Summarized API requests by application and user** query provides a summarized view fo the API requests for a Microsoft Entra user and application. This report shows the usage, which can then be compared to service protection API limits. For the selected user and application, the query displays:
- The total number of API requests in the selected date/time range.
- The total execution time of the API requests in the selected date/time range.

The results are summarized in five-minute intervals, similar to the five-minute sliding window of [user-based service protection API limits](service-protection-api-limits.md#user-based-service-protection-api-limits).

To view the summarized data:

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the query name, and then select **Summarized API requests by application and user**.
6. Enter the following in the query options:
    - **Start date**: The date and time of the beginning of the range for which you want to see the API usage data.
    - **End date**: The date and time of the end of the range for which you want to see the API usage data.
    - **User object ID**: The Microsoft Entra ID (Microsoft Entra ID) user object ID of the user.
    - **Application ID**: The Microsoft Entra application ID of the integrating application using the APIs.
7. Select **Search**.

## API requests by application and user

The **API requests by application and user** query displays the list of API requests made for a defined user and application with the given date/time range. For each record, the query displays:
- The timestamp of the request
- The Microsoft Entra user ID of the user making the API request
- The Microsoft Entra application ID of the request
- The AOS node on which the request was made
- The URL of the API request
- The total execution time of the request

To view the data for the query:

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the query name, and then select **API requests by application and user**.
6. Enter the following in the query options:
    - **Start date**: The date and time of the beginning of the range for which you want to see the API usage data.
    - **End date**: The date and time of the end of the range for which you want to see the API usage data.
      > [!NOTE]
      > The maximum range of time allowed for the query is 20 minutes. Do not set the **End date** value more than 20 minutes from the **Start date** value.
      
    - **User object ID**: The Microsoft Entra ID (Microsoft Entra ID) user object ID of the user.
    - **Application ID**: The Microsoft Entra application ID of the integrating application using the APIs.
7. Select **Search**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
