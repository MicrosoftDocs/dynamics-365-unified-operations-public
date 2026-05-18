---
title: Known issues with self-service deployment
description: Learn about known issues that you might experience when using self-service deployment for Microsoft Dynamics Lifecycle Services.
author: rashmansur
ms.author: rashmim
ms.topic: troubleshooting-known-issue
ms.custom: 
  - bap-template
ms.date: 04/02/2026
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: IT Pro 
ms.search.region: Global 
ms.search.validFrom: 2018-12-31
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 8.1.1
---

# Known issues with self-service deployment

[!include[banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]
[!include [LCS deprecation](../includes/lcs-deprecation.md)]

This article describes the known issues with [self-service deployment](infrastructure-stack.md).

## Microsoft Dynamics Lifecycle Services

### Features not intended for implementation

The following Lifecycle Services features aren't implemented in self-service deployment.

- **System diagnostics** - You can access all data and functionality that system diagnostics provides today through other features in the product and Lifecycle Services.
- **Service requests** - Self-service actions replace service requests.

### Known issues in this release

Known issues are bugs that the product team plans to address in upcoming releases. Every two weeks, there's a new release of Lifecycle Services.

## Finance and operations apps

> [!NOTE]
> Dynamics 365 Commerce is implemented in the modern deployment experience with the 10.0.10 release. For more information, see [Create payment packaging for Application Explorer for self-service deployment](../../../commerce/dev-itpro/payment-connector-package.md).

### Features not intended for implementation

The following features aren't supported in self-service deployment.

- **Custom fonts** - Custom fonts aren't supported. For more information, see [Document Reporting Service in Dynamics 365 applications](../analytics/reporting-experience-iias-environments.md).
- **Customizations related to user interface (UI) components on self service** - Customizations that don't use the standard Financial Reporting or SQL Server Reporting Services (SSRS) in finance and operations apps often take a dependency on UI components of the operating system where the AOS runs. Example dependencies include Windows fonts, web browsers such as Microsoft Edge, or custom PDF rendering. Microsoft doesn't ensure the host operating system includes any support for font infrastructure, web browsers, or any general UI components. The host operating system changes when migrating to self-service infrastructure. If you have such dependencies and have additional questions, contact Microsoft Support.

### Features no longer supported

The following feature isn't supported with self-service deployment.

#### FTP

Customizations that rely on FTP aren't supported with self-service deployment. Consider the following information:

- Microsoft doesn't ensure that all outbound requests from an Application Object Server (AOS) are on a static IP address.

- Until June 2021, Microsoft ensures that all outbound requests during a particular AOS session are on the same IP address. This restriction can affect some processes, such as FTP. Remove the use of FTP by using Power Apps to pull the files in and make API calls into finance and operations apps to import the files by using the Data Integration framework. For more information, see [Data entities integration overview](../data-entities/integration-overview.md). Some specific examples include:

  - Use the native SFTP connector (as described in [Monitor, create, and manage SFTP files in Azure Logic Apps](/azure/connectors/connectors-create-api-sftp)), which still requires some port opening on the firewall to call the on-premises service. Consider that for Logic Apps, the list of IPs is much shorter than the entire [region allowlist](/azure/logic-apps/logic-apps-limits-and-config#outbound) and the [limits and configuration in Power Automate](/power-automate/limits-and-config#logic-apps).

  - Use the **Local Filesystem** connector, as described in [Outbound IP addresses](/azure/logic-apps/logic-apps-limits-and-config#outbound), in combination with the on-premises data gateway. For more information, see [Install on-premises data gateway for Azure Logic Apps](/azure/logic-apps/logic-apps-gateway-install). This solution completely removes the need for the IP allowlist, which is deprecated in self-service deployment, while keeping a very high level of security.

  - Self-service capabilities: If FTP scenarios fail after migrating to self-service capabilities, review the configuration at the FTP server. The most common scenario is the need to update the allowed [IP list](deploymentFAQ.md) with the ranges for self-service environments.

> [!NOTE]
> For more information about deprecated features, see [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md) and [Removed or deprecated features from previous releases](../migration-upgrade/deprecated-features.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
