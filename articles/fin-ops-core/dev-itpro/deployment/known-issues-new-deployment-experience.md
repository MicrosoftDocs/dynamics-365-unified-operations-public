---
# required metadata

title: Known issues with self-service deployment
description: This topic lists known issues that you might experience when using self-service deployment.
author: rashmansur
manager: AnnBe
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: 
ms.author: rashmim
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Known issues with self-service deployment

[!include[banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic describes the known issues with [self-service deployment](infrastructure-stack.md).

## Lifecycle Services (LCS)

### Features not intended to be implemented
The following LCS features will not be implemented in self-service deployment.

- **System diagnostics** - All data and functionality provided by system diagnostics today will be available through other features in the product and LCS. 
 - **Service requests** - Service requests are being replaced with self-service actions. 

### Known issues in this release
Know issues are bugs that will be addressed in upcoming releases. Every 2 weeks there is a new release of LCS.

## Finance and Operations apps 

> [!NOTE]
> Dynamics 365 Commerce is implemented in the modern deployment experience with the 10.0.10 release. For more information, see [Create payment packaging for Application Explorer for self-service deployment](../../../commerce/dev-itpro/payment-connector-package.md).

### Features not intended to be implemented
The following feature will not be implemented in self-service deployment.

- **Custom fonts** - Custom fonts are not supported. For more information, see [Document Reporting Service in Dynamics 365 applications](../analytics/reporting-experience-iias-environments.md).

### Features no longer supported
The following feature is no longer supported with self-service deployment.

#### FTP
Customizations relying on FTP are not supported with self-service deployment and should consider the following actions.

- **Add retries** - This should be viewed as a short to medium term option. The current infrastructure design allows control and data calls to occasionally have matching IP. This design is subject to change. 
- **Disabling the FTP requirement for control and data that is from the same IP** - Carefully evaluate the security implications for your situation in this case.
- **Remove the use of FTP** - For example, use Power Apps to pull the files in and make API calls into Finance and Operations apps to import the files using the Data Integration framework. For more information, see [Choose a data integration strategy](../data-entities/integration-overview.md).
- **Use SFTP** - We do not recommend using static outbound IP addresses. For more information, see the [Finance and Operations Static IP Addresses](https://community.dynamics.com/ax/b/axinthefield/posts/dynamics-365-for-finance-and-operations-static-ip-addresses) blog post.

Our general recommendation is to remove the use of FTP. Do not use a direct connection from Dynamics 365 to an SFTP. Instead, use a Logic App in between the two. With the Logic App you have two options:

- Use the native SFTP connector (as described in [Monitor, create, and manage SFTP files in Azure Logic Apps](https://docs.microsoft.com/azure/connectors/connectors-create-api-sftp)), which still requires some port opening on the firewall to call the on-premises service. Consider that for Logic Apps, the list of IPs is much shorter than the entire [region allow list](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-limits-and-config#outbound) and the [limits and configuration in Power Automate](https://docs.microsoft.com/power-automate/limits-and-config#logic-apps).

- Use the “Local Filesystem” connector, as described in [Outbound IP addresses](https://docs.microsoft.com/azure/logic-apps/logic-apps-limits-and-config#outbound), in combination with the on-premises data gateway. For more information, see [Install on-premises data gateway for Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-gateway-install). This solution completely removes the need for the IP allow list, which is deprecated in self-service deployment, while keeping a very high-level of security.

> [!NOTE]
> For more information about deprecated features, see [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md) and [Removed or deprecated features from previous releases](../migration-upgrade/deprecated-features.md) and [Removed or deprecated features in previous releases](../get-started/removed-deprecated-features-platform-updates.md).
