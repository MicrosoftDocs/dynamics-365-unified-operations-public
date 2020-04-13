---
# required metadata

title: Removed or deprecated platform features
description: This topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.
author: sericks007
manager: AnnBe
ms.date: 04/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-02-29 
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated platform features

[!include [banner](../includes/banner.md)]

This topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!NOTE]
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Platform updates for version 10.0.11 of Finance and Operations apps

> [!NOTE]
> The following information is being provided so that you can plan appropriately. For more information about the targeted release schedule of version 10.0.11 of Finance and Operations apps, see [Service update availability](../../fin-ops/get-started/public-preview-releases.md).

### Field groups containing invalid field references

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** |It is possible for table metadata definitions to have field groups that contain invalid field references. If deployed, these field groups can cause runtime failures in Financial Reporting and SQL Server Reporting Services (SSRS).  A compiler *warning* was introduced in Platform update 23 to allow for these metadata issues to be addressed. Platform updates for version 10.0.11 of Finance and Operations apps categorize this issue as a compiler *error*.<br><br>To fix this issue:<br><br>1. Remove the invalid field reference from the table field group definition.<br><br>2. Recompile.<br><br>3. Ensure that any errors are addressed. |
| **Replaced by another feature?**   | This compiler error permanently replaces the compiler warning.  |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning is now a compiler error with platform updates for version 10.0.11 of Finance and Operations apps. |

### ISV licenses created with SHA1 hashing algorithm



|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for creating ISV licenses has changed. For more information, see [Independent software vendor (ISV) licensing](../dev-tools/isv-licensing.md#appendix-create-self-signed-certificates-for-test-purposes). |
| **Replaced by another feature?**   | Yes, you create licenses with Powershell.  |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | <strong>Deprecated</strong>: ISV licenses created with SHA1 hashing algorithm which depended upon certificates created with the MakeCert utility which has been deprecated.<br><strong>Deprecated</strong>: The use of SHA1 for security or hashing purposes. SHA1 will be cease to function in early 2021 and as such should no longer be used.<br><strong>Removed</strong>: Support of TLS 1.0 and TLS 1.1 incoming or outgoing requests. |



## Platform update 32

### Workflow request change dialog box no longer includes user selection drop-down list
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This was a security issue because the request for change could be sent to an unintended user. This was also a usability issue because it forced the user to determine who the workflow originator was and manually select them.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Workflow |
| **Deployment option**              | All |
| **Status**                         | The user selection drop-down list was removed from the request change dialog box in Platform update 32. Request change requests will be automatically sent to the originator as intended. For more information about this functionality, see [Actions in workflow approval processes](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/workflow-actions?toc=%2Fdynamics365%2Fcommerce%2Ftoc.json#request-change). |

### Embedded drill-through links are no longer supported in paginated documents rendered by the cloud-hosted service 
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Navigation URLs embedded in documents rendered by the service may contain sensitive business data. We are removing support for embedded drill-through links in documents as a security precaution to further protect customer's data. Users will also benefit from improved performance while interactively producing documents as a result of this change.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Reporting |
| **Deployment option**              | All |
| **Status**                         | This feature is actively being removed from the service.<br><br>The modern client offers numerous options for producing views that include auto-generated links to assist in navigating the application. Paginated documents rendered by the service are recommended for external communications that are emailed, archived, and printed for recipients. We have improved the experience for previewing documents directly in the browser, which offers direct access to local printers. For more information, see [Preview PDF documents with an embedded viewer](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/preview-pdf-documents). |

## Previous announcements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../migration-upgrade/deprecated-features.md).

