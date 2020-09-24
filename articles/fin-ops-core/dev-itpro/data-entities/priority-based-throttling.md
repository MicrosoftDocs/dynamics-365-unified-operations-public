---
# required metadata

title: Priority-based throttling
description: This topic provides information about priority-based throttling for Odata and custom service-based integrations.
author: hasaid
manager: AnnBe
ms.date: 09/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Platform update 37

---

# Priority-based throttling

[!include [banner](../includes/banner.md)]


Priority-based throttling prevents the over-utilization of resources to preserve the system's responsiveness and ensure consistent availability and performance for environments running Dynamics 365 Finance and Operations apps.

- Integrations can be prioritized based on business-critical needs. Throttling honors these priorities. 
- For OData and custom service requests, a 429 error "Too many requests", will occur. 
- You can query throttling events on the **Lifecycle Services Monitoring** page.  

Priority-based throttling provides the ability to set priorities for OData and custom service-based integrations, depending on the business-critical need of integrations.

The **Integration priority** page is used to assign priorities for integrations so that priorities can be honored when requests are throttled. 

Setting appropriate priorities ensures that low-priority integrations will be throttled before high-priority integrations, based on the the integration. For more information about how to set up integration, see [Enable connectivity with external services](https://docs.microsoft.com/learn/modules/integrate-azure-finance-operations/7-connect-external). 

There are two kinds of applications are supported in Microsoft Azure Active Directory (Azure AD):

- User based - This flow uses a username and password for authentication and authorization. 
- Azure AD app based - A confidential client is an application that can keep a client password confidential. The authorization server assigned this client password to the client application. 

For more information, see [Authentication](services-home-page.md).
 
## Configure priorities for integrations 

After you have registered your service in Azure AD and in your Finance and Operations apps, you can set up priorities for integrations.

> [!NOTE]
> You must be assigned the System administrator or Integration priority manager role to complete the set up. 

1. In Finance and Operations apps, go to **System administration** > **Setup** > **Throttling priority mapping**. 
2. Select **New**. 
3. In the **Authentication type** field, select **User** or **Azure AD application** based on your integration scenario.
4. If **Azure AD application type** is selected, in the **Client ID** field select the application that you registered in the Azure Active Directory application.
5. If **User type** is selected, in the **User ID** field select an appropriate service account user ID.
6. Assign the appropriate priority and then select **Save**.

## Retry operations 

When a request is throttled, the system provides a value indicating the duration before any new requests from the user can be processed. When a request is throttled and a 429 error occurs, the response header will include a **Retry-After** interval, which can be used to retry the request after a specific number of seconds. The following example shows this operation. 

```x++
    if (!response.IsSuccessStatusCode) 
            { 
                if ((int)response.StatusCode == 429) 
                { 
                    int seconds = 30; 
                    //Try to use the Retry-After header value if it is returned. 
                    if (response.Headers.Contains("Retry-After")) 
                    { 
                        seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault()); 
                    } 
                    Thread.Sleep(TimeSpan.FromSeconds(seconds)); 



                    // Retry sending the request.
                } 
            } 
```


## Monitoring

To have a successful onboarding experience with the throttling capability, you must also be able to monitor your Odata and custom service integration patterns. Microsoft Dynamics Lifecycle Services (LCS), which is the administration center, contains a collection of monitoring and diagnostics tools that can help ensure that you have an accurate view of the environments you manage. For more details, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](../lifecycle-services/monitoring-diagnostics.md).

You can use a set of predefined queries to get raw logs for an issue. You can then export the logs for a more advanced analysis. The following types of queries are available:

- All throttling events
- Requests throttled

## Access the Monitoring and diagnostics portal

1. In LCS, open the appropriate project.
2. In the **Environments** section, select the environment to view, and then select **Full details**.
3. On the **Environment details** page, select **Environment monitoring** to open the Monitoring and diagnostics portal. 
4. On the **Environment monitoring** page, select the **Activity** tab to view the **Raw logs** page. 
5. Select the **Query name**, and then select **All throttling events** for all Odata and custom services activities.
6. Select the **Query name**, and then select **Requests throttled** for all Odata and custom services requests that have been throttled.
