---
# required metadata

title: Throttling prioritization
description: This article provides information about priority-based throttling for OData and custom service-based integrations.
author: jaredha
ms.date: 08/25/2022
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

Resource-based limits for service protection application programming interfaces (APIs) work together with the user-based limits for service protection APIs as protective settings that help prevent the over-utilization of resources. In this way, they help preserve the system's responsiveness and ensure consistent availability and performance for environments that run finance and operations apps. The resource-based limits will throttle service requests when the aggregate consumption of web server resources reaches levels that threaten service performance and availability.

> [!NOTE]
> Throttling priority mapping does not apply to user-based service protection API limits. The priority mapping is specific to resource-based service protection API limits. See [Service protection API limits](service-protection-api-limits.md) for more information on the API limit types.

For resource-based service protection API limits, you can set the relative priority for OData and custom service-based integrations, depending on your business-critical need for these integrations. The throttling manager will then honor the priorities that are set for the requests. For OData and custom service-based requests, a "Too many requests" error will be sent if system health and performance are affected.

## Determine prioritization

The **Throttling Priority Mapping** page is used to assign priorities for integrations so that priorities can be honored when requests are throttled. Setting appropriate priorities ensures that low-priority integrations will be throttled before high-priority integrations. For more information about how to set up integration, see [Enable connectivity with external services](/training/modules/integrate-azure-finance-operations/7-connect-external). 

The following are the authentication types supported in Azure Active Directory (AAD). For more information, see [Authentication](services-home-page.md).
- **User based**: This flow uses a username and password for authentication and authorization. 
- **AAD application based**: This flow uses an application registered in AAD and an associated secret for authentication. 

When setting the priority mapping, you will select the authentication type that is used for the integration, either for a specific application (client ID) or a specific user.
- If the priority mapping is set for an application, then the priority mapping is applied to any API request from the selected AAD application ID.
- If the priority mapping is set for a user, then the priority mapping is applied to any API request from the selected AAD user ID.

There are three priority levels available: Low, Medium, and High. Each priority level assigns different throttling thresholds for the selected application or user.
- **Low**: Applications or users with a Low priority mapping have a lower threshold of service resource consumption for which they will be throttled than integrations set with a Medium or High priority.
- **Medium**: Applications or users with a Medium priority mapping have a higher throttling threshold of service resource consumption than integrations with a Low priority mapping, and lower throttling threshold of resource consumption than integrations with a High priority mapping.
- **High**: Applications or users with a High priority mapping have a higher throttling threshold of service resource consumption than integrations with either a Low or Medium priority mapping.

These priority mappings ensure that requests from high-priority applications and users not throttled due to service resource consumption by lower-priority integrations.
 
## Configure priorities for integrations 

After you have registered your service in AAD and in your finance and operations apps, you can set up priorities for integrations.

> [!NOTE]
> You must be assigned the **System administrator** or **Integration priority manager** role to complete the set up. 

1. In finance and operations apps, go to **System administration** > **Setup** > **Throttling priority mapping**. 
2. Select **New**. 
3. In the **Authentication type** field, select **User** or **AAD application** based on your integration scenario.
4. If **AAD application type** is selected, in the **Client ID** field select the application that you registered in the Azure Active Directory application.
5. If **User** type is selected, in the **User ID** field select an appropriate service account user ID.
6. Assign the appropriate priority and then select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
