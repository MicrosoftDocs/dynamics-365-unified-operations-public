---
# required metadata

title: Throttling prioritization
description: This article provides information about priority-based throttling for OData and custom service-based integrations.
author: jaredha
ms.date: 05/04/2022
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
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Platform update 37

---

# Throttling prioritization

[!include [banner](../includes/banner.md)]

This article provides information about priority-based throttling for Open Data Protocol (OData) and custom service-based integrations.

Resource-based limits for service protection application programming interfaces (APIs) work together with the user-based limits for service protection APIs as protective settings that help prevent the over-utilization of resources. In this way, they help preserve the system's responsiveness and ensure consistent availability and performance for environments that run Finance and Operations apps. The resource-based limits will throttle service requests when the aggregate consumption of web server resources reaches levels that threaten service performance and availability.

For resource-based service protection API limits, you can set the relative priority for OData and custom service-based integrations, depending on your business-critical need for these integrations. The throttling manager will then honor the priorities that are set for the requests. For OData and custom service-based requests, a "Too many requests" error will be sent if system health and performance are affected.

The **Throttling Priority Mapping** page is used to assign priorities for integrations so that priorities can be honored when requests are throttled. 

Setting appropriate priorities ensures that low-priority integrations will be throttled before high-priority integrations. For more information about how to set up integration, see [Enable connectivity with external services](/learn/modules/integrate-azure-finance-operations/7-connect-external). 

Two kinds of applications are supported in Azure Active Directory (Azure AD):

- **User based** – This flow uses a username and password for authentication and authorization. 
- **Azure AD app based** – A confidential client is an application that can keep a client password confidential. The authorization server assigned this client password to the client application. 

For more information, see [Authentication](services-home-page.md).
 
## Configure priorities for integrations 

After you have registered your service in Azure AD and in your Finance and Operations apps, you can set up priorities for integrations.

> [!NOTE]
> You must be assigned the **System administrator** or **Integration priority manager** role to complete the set up. 

1. In Finance and Operations apps, go to **System administration** > **Setup** > **Throttling priority mapping**. 
2. Select **New**. 
3. In the **Authentication type** field, select **User** or **Azure AD application** based on your integration scenario.
4. If **Azure AD application type** is selected, in the **Client ID** field select the application that you registered in the Azure Active Directory application.
5. If **User type** is selected, in the **User ID** field select an appropriate service account user ID.
6. Assign the appropriate priority and then select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
