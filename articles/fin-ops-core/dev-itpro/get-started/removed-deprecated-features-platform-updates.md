---
# required metadata

title: Removed or deprecated platform features
description: This topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.
author: sericks007
manager: AnnBe
ms.date: 09/17/2020
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

Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Platform updates for version 10.0.14 of Finance and Operations apps

> [!NOTE]
> Version 10.0.14 is a preview release. The content and the functionality are subject to change. For more information about preview releases, see [Service update availability](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/public-preview-releases).


### Online users page 

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This is a legacy page that was built for previous client/server architecture. The information on this page is not always accurate, which can be confusing and misleading. |
| **Replaced by another feature?**   | We will provide a new page in a future update.|
| **Product areas affected**         | System Administration |
| **Deployment option**              | All |
| **Status**                         | By October 2021 this form will be removed.   |

## Platform updates for version 10.0.13 of Finance and Operations apps


### Custom code defined in SSRS report properties 

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | In general, custom code offers limited benefits while at the same time, requires significant resourcing and compute to support. Custom code is primarily used by report authors to call public methods from a custom code assembly. However, the cloud-hosted service does not support references to custom assemblies for SSRS reports. |
| **Replaced by another feature?**   | Report authors may choose to continue referencing public .NET APIs for Math, Conversion, and Format operations from any textbox expression. For more information, see [Add Code to a Report (SSRS)](https://docs.microsoft.comsql/reporting-services/report-design/add-code-to-a-report-ssrs?view=sql-server-ver15).  |
| **Product areas affected**         | Subset of application report designs defined in RDL that contain custom code. |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13, the compiler will begin issuing a warning for instances where custom code is detected in a SSRS report definition. To fix the issue, open the report design definition and remove all custom code artifacts. This warning will be replaced with a compiler error in a future update.   |

### Upgrade of three jQuery component libraries 

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Three jQuery component libraries are being updated for security fixes and to maintain currency.   
| **Replaced by another feature?**   | The following libraries are being affected: jQuery (to version 3.5.0 from version 2.1.4), jQuery UI (to version 1.12.1 from version 1.11.4), jQuery qTip (to version 3.0.3 from 2.2.1). Migration guidance has been provided online by jQuery.  |
| **Product areas affected**         | Extensible controls, specifically custom JavaScript code utilizing deprecated or removed APIs |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13/Platform update 37, customers can optionally move to the latest libraries by enabling the "Upgrade three jQuery component libraries" feature. Moving to the new libraries will be mandatory with the April 2021 release to allow time for migration of affected APIs.   |

### Existing grid control/forceLegacyGrid() API

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The existing grid control is being replaced by the new grid control. |
| **Replaced by another feature?**   | The [new grid control](../..//fin-ops/get-started/grid-capabilities.md) |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | In version 10.0.13, the new grid control is generally available, and customers can optionally turn on this feature. The new grid control will become mandatory in the October 2021 release. When the new grid control becomes mandatory, the **forceLegacyGrid()** API will no longer be honored. |

### Personalization without saved views 

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The personalization subsystem has been overhauled with the saved views feature, so that it has better performance and offers additional capabilities. |
| **Replaced by another feature?**   | Saved views |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | In version 10.0.13/Platform update 37, the saved views feature is generally available, and customers can optionally turn on this feature. The saved views feature will become mandatory in the October 2021 release. |


## Platform updates for version 10.0.12 of Finance and Operations apps

### Grid or group control form extensions containing invalid field references

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The data group property on grid or group controls is used to automatically show all the fields of a field group. A grid or group control added by extension could contain fields that are no longer defined on the field group, or it might be missing fields that are defined on the field group. This can cause inconsistent behavior at runtime. Platform updates for version 10.0.12 of Finance and Operations apps now categorize this issue as a compiler *warning*. To fix this issue, open the form extension and save it.
| **Replaced by another feature?**   | This compiler warning will be replaced with a compiler error in a future update. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | A compiler warning is introduced in platform updates for version 10.0.12 of Finance and Operations apps. |

## Platform updates for version 10.0.11 of Finance and Operations apps

### Explicit safe lists for self-service environments

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for moving IP to safe lists has changed. Self-service no longer supports IP safe lists. |
| **Replaced by another feature?**   | For more information, see [Configuring Azure Active Directory Conditional Access](https://docs.microsoft.com/appcenter/general/configuring-aad-conditional-access).|
| **Product areas affected**         | Security |
| **Deployment option**              | Cloud |
| **Status**                         | **Deprecated:** This feature is fully-deprecated for self-service deployments. |

### Visual Studio 2015

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | To support the latest versions of Visual Studio, some changes have to be made to the X++ extensions for Visual Studio. These changes are incompatible with Visual Studio 2015. |
| **Replaced by another feature?**   | Visual Studio 2017 will replace Visual Studio 2015 as the deployed and required version. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Once the availability of new virtual machines (VMs) with Visual Studio 2017 is announced, existing VMs with only Visual Studio 2015 will have to be redeployed by Release Wave 1 of 2021. |

### Field groups containing invalid field references

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Field groups in table metadata definitions can contain field references that aren't valid. If these field groups are deployed, they can cause runtime failures in Financial Reporting and Microsoft SQL Server Reporting Services (SSRS). Platform update 23 introduced a compiler *warning* that enabled this metadata issue to be addressed. Platform updates for version 10.0.11 of Finance and Operations apps categorize this issue as a compiler *error*.<p>To fix this issue, follow these steps.</p><ol><li>Remove the invalid field reference from the table field group definition.</li><li>Recompile.</li><li>Make sure that any errors are addressed.</li></ol> |
| **Replaced by another feature?**   | This compiler error permanently replaces the compiler warning.  |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | **Deprecated:** The compiler warning is a compiler error in platform updates for version 10.0.11 of Finance and Operations apps. |

### ISV licenses created by using the SHA1 hashing algorithm

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for creating independent software vendor (ISV) licenses has changed. For more information, see [Independent software vendor (ISV) licensing](../dev-tools/isv-licensing.md#appendix-create-self-signed-certificates-for-test-purposes). |
| **Replaced by another feature?**   | Yes. Use Windows PowerShell to create licenses. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | <strong>Deprecated:</strong> ISV licenses that were created by using the SHA1 hashing algorithm. This algorithm depended on certificates that were created by using the MakeCert utility, and this utility has been deprecated.<p><strong>Deprecated:</strong> The use of SHA1 for security or hashing purposes. SHA1 will cease to function in early 2021. Therefore, it should no longer be used.<p><strong>Removed:</strong> Support for Transport Layer Security (TLS) 1.0 and TLS 1.1 incoming or outgoing requests. |

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

