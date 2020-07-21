---
# required metadata

title: Priority-based throttling
description: This topic provides inofrmaiton about priority-based throttling for Odata and custom service-based integrations.
author: hasaid
manager: AnnBe
ms.date: 07/20/2020
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
[!include [banner](../includes/preview-banner.md)]

Priority-based throttling prevents the over-utilization of resources to preserve the system's responsiveness and ensure consistent availability and performance for Dynamics 365 Finance and Operations apps environments. 

- Integrations can be prioritized based on their business-critical nature, and throttling honors these priorities. 
- For OData and custom service requests, a 429, Too Many Requests, error will occur. 
- On the **Lifecycle Services Monitoring** page, you can query throttling events.  

The idea behind priority-based throttling is to provide the ability to set priorities for Odata and custom service-based integrations depending on the business-critical nature of integrations. 

The **Integration priority** page is used to assign priorities for integrations so that priorities can be honored when requests are throttled. 

Setting appropriate priorities ensures that low priority integrations will be throttled before the high priority integrations based on the business nature of the integration. For more information on how to set up integration, see [Enable connectivity with external services](https://docs.microsoft.com/en-us/learn/modules/integrate-azure-finance-operations/7-connect-external). 

Two kinds of applications are supported in Microsoft Azure Active Directory (AAD): 

- User based: This flow uses a user-name and password for authentication and authorization. 
- AAD app based: A confidential client is an application that can keep a client password confidential. The authorization server assigned this client password to the client application. 

For more information, see [Authentication](services-home-page.md).
 
## How to configure priorities for integrations 

After you have registered your service in Azure AAD and your Finance and Operations apps, you can set up priorities for integrations.  

> [!NOTE]
> Ypu must be assigned the System administrator or Integration priority manager role to complete the set up. 

1. In you Finance and Operations apps, go to **System administration** > **Setup** > **Throttling priority mapping**. 
2. Select **New**. 
3. In the **Authentication type** field, select **User** or **AAD application** based on your integration scenario.
4. If **AAD application type** is selected, in the **Client ID** field select the AAD application that you registered in Azure active directory application.
5. If **User type** is selected, in the **User ID** field select an appropriate service account user ID.
6. Assign the appropriate priority and then select **Save**.

## Retry operations 

When a request is throttled, the system provides a value indicating the duration before any new requests from the user can be processed. 
When a request is throttled and a 429 error occurs, the response header will include a **Retry-After** interval which can be used to retry the request after a specific number of seconds. See the following example:

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



                    // retry sending the request 
                } 
            } 
