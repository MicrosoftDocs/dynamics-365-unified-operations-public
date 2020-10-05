---
# required metadata

title: Known issues with self-service deployment
description: This topic lists known issues that you might experience when using self-service deployment.
author: rashmansur
manager: AnnBe
ms.date: 10/05/2020
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
The following LCS features are deprecated and will not be implemented in self-service deployment.

- **System diagnostics:** System diagnostics has been deprecated. All data and functionality provided by system diagnostics today will be available through other features in the product and LCS. 
 - **Service requests:**  Service requests are being replaced with self-service actions. 

### Known issues in this release
Know issues are bugs that will be addressed in upcoming releases. Every 2 weeks there is a new release of LCS.

## Finance and Operations apps 

> [!NOTE]
> Dynamics 365 Commerce is implemented in the modern deployment experience with the 10.0.10 release. For more information, see [Create payment packaging for Application Explorer for self-service deployment](../../../commerce/dev-itpro/payment-connector-package.md).

### Features not intended to be implemented
The following feature is deprecated and will not be implemented in self-service deployment.

- **Custom fonts:** Custom fonts are not supported. For more information, see [Document Reporting Service in Dynamics 365 applications](../analytics/reporting-experience-iias-environments.md).

### Features no longer supported
The following feature is no longer supported in self-service deployment.

- **CFTP:** Customizations currently relying on FTP could are not supported on Self Service and should consider the following actions.

 1. Add retries. (This should be viewed as a short to medium term option. The current infrastructure design allows control and data calls to occasionally have matching IP. This design is subject to change.)
 2. Disabling the FTP requirement for control and data being from the same IP. (Please evaluate the security implications for your situation in this case.)
 3. Remove the use of FTP. For example, use powerapps to pull the files in and make api calls into F&O to import the files using the Data Integration framework. [Additional options here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/integration-overview)
 4. Use SFTP
 Note that we have not guaranteed static outbound IP addresses for some years, as discussed [at this blog post](https://community.dynamics.com/ax/b/axinthefield/posts/dynamics-365-for-finance-and-operations-static-ip-addresses).

 Our general recommendation is to follow item 3. Do not use a direct connection from Dynamics to an SFTP, instead use a Logic App in between the two. With the Logic app you have   two options:

  A. Use the native SFTP connector [Connect to SFTP account (Deprecated) - Azure Logic Apps | Microsoft Docs ](https://docs.microsoft.com/en-us/azure/connectors/connectors-  create-api-sftp) which still require some port opening on the firewall to call the on prem service. Consider that for Logic Apps the list of IPs is much shorter than the entire  [region whitelisting](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-limits-and-config#outbound) and [Power Automate limits and Config](    https://docs.microsoft.com/en-us/power-automate/limits-and-config#logic-apps).

  B. Use the “Local Filesystem” connector [Connect to file systems on premises - Azure Logic Apps | Microsoft Docs](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-  limits-and-config#outbound) in combination with the on-premises data gateway. [Install on-premises data gateway - Azure Logic Apps | Microsoft Docs] (https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-gateway-install). This solution also completely removes the need for the IP whitelisting which is deprecated in Sef Service while keeping very high level  of security.


> [!NOTE]
> For more information about deprecated features, see [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md) and [Removed or deprecated features from previous releases](../migration-upgrade/deprecated-features.md) and [Removed or deprecated features in previous releases](../get-started/removed-deprecated-features-platform-updates.md).
