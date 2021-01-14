---
# required metadata

title: Priority-based throttling in Human Resources
description: This topic provides information about priority-based throttling for OData and custom service-based integrations in Dynamics 365 Human Resources.
author: andreabichsel
manager: tfehr
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Admin
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2021-01-14
ms.dyn365.ops.version: Human Resources

---

# Priority-based throttling in Human Resources

Priority-based throttling prevents the over-utilization of resources. It preserves system responsiveness and ensures consistent availability and performance.

- Integrations can be prioritized based on business-critical needs. Throttling honors these priorities. 
- For OData and custom service requests, a 429 error "Too many requests", will occur. 

Priority-based throttling lets you set priorities for OData and custom service-based integrations, depending on the business-critical need of integrations.

Use the **Integration priority** page to assign priorities for integrations. Priorities are honored when requests are throttled. 

Setting appropriate priorities ensures that low-priority integrations will be throttled before high-priority integrations, based on the integration. For more information about how to set up integration, see [Enable connectivity with external services](https://docs.microsoft.com/learn/modules/integrate-azure-finance-operations/7-connect-external). 

Two kinds of applications are supported in Microsoft Azure Active Directory (Azure AD):

- User-based - This flow uses a username and password for authentication and authorization. 
- Azure AD app-based - A confidential client is an application that can keep a client password confidential. The authorization server assigned this client password to the client application. 

For more information, see [Authentication](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/services-home-page).
 
## Configure priorities for integrations 

After you register your service in Azure AD and in your Finance and Operations apps, you can set up priorities for integrations.

> [!NOTE]
> You must be assigned the System administrator or Integration priority manager role to complete the set up. 

1. In the search bar at the top of the screen, enter **Throttling priority mapping**. 
2. Select **New**. 
3. In the **Authentication type** field, select **User** or **Azure AD application** based on your integration scenario.
4. If **Azure AD application type** is selected, in the **Client ID** field select the application that you registered in the Azure Active Directory application.
5. If **User type** is selected, in the **User ID** field select an appropriate service account user ID.
6. Assign the appropriate priority and then select **Save**.

## Retry operations 

When a request is throttled, the system provides a value indicating the duration before any new requests from the user can be processed. When a request is throttled and a 429 error occurs, the response header will include a **Retry-After** interval, which can be used to retry the request after a specific number of seconds. The following example shows this operation. 

```C#
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
