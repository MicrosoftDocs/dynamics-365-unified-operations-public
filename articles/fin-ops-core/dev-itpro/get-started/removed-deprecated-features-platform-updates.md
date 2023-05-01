---
# required metadata

title: Removed or deprecated platform features
description: This article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.
author: sericks007
ms.date: 02/27/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-02-29 
ms.dyn365.ops.version: Platform update 33

---
# Removed or deprecated platform features

[!include [banner](../includes/banner.md)]

This article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of finance and operations apps.

## Feature deprecation effective July 2023

### Non-Azure AD external user sign-in 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating access for external users who aren't present in the Microsoft Azure Active Directory (Azure AD) tenant that's used for your finance and operations environment. Microsoft has identified this type of access as a security issue. For more information, see [Security alert: common or tenanted passthrough tokens alert](/identity/microsoft-identity-platform/first-party-alert/passthrough?branch=main/). |
| **Replaced by another feature?**   | Yes, finance and operations apps already support business-to-business (B2B) collaboration that provides a secure way to provide access for external guest users. For more information, see [B2B collaboration overview](/azure/active-directory/external-identities/what-is-b2b/). If you want, you can take proactive action by inviting and onboarding external users from the Azure AD portal. No changes are required through finance and operations apps. We will share customer communications with affected customers, and will also share instructions for fixing this issue in version 10.0.35 or later of finance and operations apps. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. End of support date is targeted for October 2023. |

## Feature deprecation effective August 2022

### Lifecycle Services (LCS) features deprecated in August 2022

As part of the [One Dynamics One Platform](/dynamics365-release-plan/2022wave2/finance-operations/finance-operations-crossapp-capabilities/one-dynamics-one-platform) work effort, the following LCS features are deprecated.

| Feature name | Used with AX 2012? | Used with finance and operations apps? | Replaced by another feature? |
|--------------|--------------------|----------------------------------------|------------------------------|
| Announcements | Yes | Yes | Yes: Banners exist on individual project and environment pages for notifications. |
| Configuration manager | Yes | No | No |
| Crash and dump analysis | Yes | No | No |
| Feedback and bugs | Yes | Yes | No |
| My subscription | Yes | Yes | No |
| Office 365 | Yes | Yes | Yes: Azure Active Directory or Microsoft admin portal. |
| Impact analysis | No | Yes | No |
| Total economic impact estimator | No | Yes | No |
| Service requests | No | Yes | Yes: [Self-service deployments](../deployment/infrastructure-stack.md) |
| SharePoint integration | Yes | Yes | No |
| Configuration and data manager | No | Yes | No |
| Process data packages | No | Yes | Yes: [Data Import Export Framework (DIXF)](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job) |
| Environment upgrade | No | Yes | Yes: [One Version](../lifecycle-services/oneversion-overview.md) service updates are available. |
| Infrastructure estimator | Yes | No | No |
| License sizing | Yes | No | No |
| Usage profiler | Yes | No | No |
| Customization analysis | Yes | No | No |
| System diagnostics | Yes | Yes | No |
| Business process modeler Visio management | Yes | Yes | No |
| AX 2012 cloud environment management | Yes | No | No |
| RDFE Azure connectors | Yes | Yes | No |
| AX 2012 versions | Yes | No | No |
| Work items stored in LCS storage | Yes | Yes | No |
| Hotfix requests | Yes | Yes | No |


### Transport Layer Security (TLS) RSA cipher suites

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're removing the following list of cipher suites to comply with our current security protocols.<br><br>TLS_RSA_WITH_AES_256_GCM_SHA384<br>TLS_RSA_WITH_AES_128_GCM_SHA256<br>TLS_RSA_WITH_AES_256_CBC_SHA256<br>TLS_RSA_WITH_AES_128_CBC_SHA256<br>TLS_RSA_WITH_AES_256_CBC_SHA<br>TLS_RSA_WITH_AES_256_CBC_SHA  |
| **Replaced by another feature?**   | Beginning January, 2023, customers can only use our [standard cipher suites](/power-platform/admin/server-cipher-tls-requirements). This change impacts your clients and servers that communicate with our servers, for example, it may impact your third party integrations, that aren't adhering to our standard cipher suites. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | Cloud deployments |
| **Status**                         | Deprecated. Customers must upgrade their servers before January, 2023. For more information about configuring TLS Cipher Suite order, see [Manage Transport Layer Security (TLS)](/windows-server/security/tls/manage-tls).  |


## Feature deprecation effective June 2022

### Finance and operations (Dynamics 365) mobile application and mobile platform 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We are deprecating the finance and operations (Dynamics 365) mobile application and platform to consolidate to a single mobile platform, which is Power Apps. |
| **Replaced by another feature?**   | Yes, mobile experiences over finance and operations app data can be built with Power Platform integration. See the [blog post](https://cloudblogs.microsoft.com/dynamics365/it/2022/06/03/finance-and-operations-dynamics-365-mobile-app-to-be-deprecated/) and [Building mobile experiences](../power-platform/build-mobile-experiences.md) for more details. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. End of support date is targeted for October 2024. |


## Platform updates for version 10.0.29 of finance and operations apps

### Panorama tab style

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Horizontally-scrolling pages align to out-dated layout patterns that have known usability and accessibility issues.  |
| **Replaced by another feature?**   | No, but other tab styles are still available. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. |


## Feature deprecation effective April 2022

### XML URL resolution in Data management 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're removing support for XML URL resolution since this has been identified as a potential security vulnerability. This means that external resources associated with XML files will no longer be resolved.  |
| **Replaced by another feature?**   | No. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. |

## Feature deprecation effective March 14, 2022

### XSLT scripting in Data management

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The support for XSLT scripting in Data management is deprecated to improve security and data protection within finance and operations apps.  |
| **Replaced by another feature?**   | No. Customers and ISVs should consider reimplementing their solutions based on X++ language, in place of XSLT scripting. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated <br><br>**Exception:** Customers who are currently using XLST scripting can continue to use it until they update to version 10.0.30 or later. For earlier versions, the exception will expire effective January 31, 2023. Customers with this exception have received a notification in the Message center available in the Microsoft 365 Admin Center. |

## Feature removal effective October 2021

### Microsoft Azure SQL reports in Lifecycle Services (LCS)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | All activities and monitoring will be performed internally, by the platform, through automation. This will not require any manual intervention.|
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL reports: Current DTU, Current DTU Details, Get Lock Details, List of Current Plan Guide, Get List of Query ID’s, Get the SQL query plan for a given Plan ID, Get query plans and execution status, Get throttle config, Get wait stats, List most expensive queries |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Removed |

### Azure SQL actions in LCS

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating some SQL actions in LCS. All activities and monitoring will be performed internally, by the platform, through automation. This will not require any manual intervention. |
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL actions: Create a plan guide to force Plan ID, Create a plan guide to add table hints, Remove Plan guide, Disable/Enable page locks and lock escalation, Update statistics on a table, Rebuild Index, Create Index |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Removed |


## Feature deprecation effective October 2021

### "Show related document attachments" feature

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The feature was returning unexpected results. |
| **Replaced by another feature?**   | No. Any further plans regarding this functionality will be communicated through our standard release wave disclosure process. |
| **Product areas affected**         | Web client - Document attachment experience |
| **Deployment option**              | All |
| **Status**                         | Deprecated  |

## Platform updates for version 10.0.23 of finance and operations apps

### OnDBSynchronize event

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | There's no control to execute this event. |
| **Replaced by another feature?**   | Yes, move existing methods subscribed to by the **OnDBSynchronize** event to a SysSetup extended class. |
| **Product areas affected**         | Database synchronization |
| **Deployment option**              | All |
| **Status**                         | Deprecated. Planned removal date is October 2022. |


### SystemNotificationsManager.AddNotification API

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Microsoft requires additional parameters when adding notifications. |
| **Replaced by another feature?**   | Yes, the **SystemNotificationsManager.AddSystemNotification()** API. This API requires that you explicitly set ExpirationDateTime and RuleID for generated notifications. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. Planned removal date is April 2023. |

## Platform updates for version 10.0.21 of finance and operations apps

### Skype for Business Online support

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Skype for Business Online has been retired. For more information, see [The Skype for Business Online service has retired](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/the-skype-for-business-online-service-has-retired/ba-p/2596601). |
| **Replaced by another feature?**   | Not currently, although we may consider adding presence from Teams in the future.|
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. The **Skype enabled** setting has been turned off starting in release 10.0.21. The removal of this setting is targeted for April 2022; however, the feature will stop functioning after the Skype team shuts down the service. |
 
## Feature deprecation effective August 2021

### Microsoft Azure SQL reports in Lifecycle Services (LCS)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | All activities and monitoring will be performed internally, by the platform, through automation. This will not require any manual intervention.|
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL reports: Current DTU, Current DTU Details, Get Lock Details, List of Current Plan Guide, Get List of Query ID’s, Get the SQL query plan for a given Plan ID, Get query plans and execution status, Get throttle config, Get wait stats, List most expensive queries |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Deprecated: Planned removal date is October 2021. |

### Azure SQL actions in LCS

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating some SQL actions in LCS. All activities and monitoring will be performed internally, by the platform, through automation. This will not require any manual intervention. |
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL actions: Create a plan guide to force Plan ID, Create a plan guide to add table hints, Remove Plan guide, Disable/Enable page locks and lock escalation, Update statistics on a table, Rebuild Index, Create Index |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Deprecated: Planned removal date is October 2021. |

## Feature deprecation effective May 2021

### Globalization portal in Lifecycle Services (LCS)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating the Globalization portal in LCS as this feature has been superseded by other LCS-based services. |
| **Replaced by another feature?**   | Yes, this feature is replaced by LCS [Issue search](../lifecycle-services/issue-search-lcs.md) and [Dynamics regulatory alert submission service](../lcs-solutions/submit-localization-alerts.md). |
| **Product areas affected**         | Globalization portal in LCS|
| **Deployment option**              | Cloud deployment |
| **Status**                         | Deprecated: Planned removal date is May 2022. |


## Feature removed effective January 28, 2021

### Batch job to handle SQL index defragmentation

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In order to reduce the overhead of operating, monitoring, and maintaining the index management by customers, this feature has been removed. |
| **Replaced by another feature?**   | Going forward, the index maintenance will be performed by Microsoft services. This will happen continuously without affecting the user workloads. |
| **Product areas affected**         | Finance and operations apps|
| **Deployment option**              | Cloud deployment - affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | This feature is removed. |


## Platform updates for version 10.0.17 of finance and operations apps


### Visual Studio 2015

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To support the latest versions of Visual Studio, some changes have to be made to the X++ extensions for Visual Studio. These changes are incompatible with Visual Studio 2015. |
| **Replaced by another feature?**   | Visual Studio 2017 will replace Visual Studio 2015 as the deployed and required version. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Upon updating, the previous X++ tools will be removed from Visual Studio 2015, and the updated tools will not install on Visual Studio 2015. There is no impact on hosted builds. For build virtual machines, the build pipeline (build definition) needs to be manually updated to change the dependency from MSBuild 14.0 (Visual Studio 2015) to MSBuild 15.0 (Visual Studio 2017) as described in [Update a legacy pipeline in Azure Pipelines](../dev-tools/pipeline-msbuild-update.md). |

### User avatar 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The user avatar that displays on the right side of the navigation bar was retrieved using an API from the Dynamics 365 header control, which has been deprecated. |
| **Replaced by another feature?**   | Users will see their initials in a circle in the navigation bar instead. This is the same visual currently used on development machines. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Removed as of version 10.0.17 |

### Enterprise Portal (EP) deprecation  

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The metadata artifacts associated with Dynamics AX 2012 Enterprise Portal (EP) have been deprecated, as EP was never supported in the finance and operations apps. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: All EP code is scheduled to be removed in the October 2021 release. |

## Deprecation effective December 2020

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products and Dynamics Lifecycle Services (LCS) is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This will impact customers who use Dynamics 365 products and LCS that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products and LCS. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products and LCS |
| **Deployment option**              | All|
| **Status**                         | Deprecated: Internet Explorer 11 won’t be supported after August 2021.|

## Platform updates for version 10.0.15 of finance and operations apps

### Visual Studio add-in to apply metadata hotfixes

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Metadata hotfixes are no longer supported with the [One Version](../../fin-ops/get-started/one-version.md) service updates that were introduced in July 2018 with version 8.1. |
| **Replaced by another feature?**   | Individual metadata hotfixes are not available for supported versions. Cumulative quality updates are applied instead. |
| **Product areas affected**         | Visual Studio add-ins |
| **Deployment option**              | Development virtual machines |
| **Status**                         | With version 10.0.15, the add-in is no longer included in the Visual Studio tools. |


## Platform updates for version 10.0.14 of finance and operations apps

### Online users page 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This is a legacy page that was built for previous client/server architecture. The information on this page is not always accurate, which can be confusing and misleading. |
| **Replaced by another feature?**   | We will provide a new page in a future update.|
| **Product areas affected**         | System Administration |
| **Deployment option**              | All |
| **Status**                         | By October 2021 this form will be removed.   |


## Platform updates for version 10.0.13 of finance and operations apps


### Custom code defined in SSRS report properties 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In general, custom code offers limited benefits while at the same time, requires significant resourcing and compute to support. Custom code is primarily used by report authors to call public methods from a custom code assembly. However, the cloud-hosted service does not support references to custom assemblies for SSRS reports. |
| **Replaced by another feature?**   | Report authors may choose to continue referencing public .NET APIs for Math, Conversion, and Format operations from any textbox expression. For more information, see [Add Code to a Report (SSRS)](/sql/reporting-services/report-design/add-code-to-a-report-ssrs).  |
| **Product areas affected**         | Subset of application report designs defined in RDL that contain custom code. |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13, the compiler will begin issuing a warning for instances where custom code is detected in a SSRS report definition. To fix the issue, open the report design definition and remove all custom code artifacts. This warning will be replaced with a compiler error in a future update.   |

### Upgrade of three jQuery component libraries 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Three jQuery component libraries are being updated for security fixes and to maintain currency.   
| **Replaced by another feature?**   | The following libraries are being affected: jQuery (to version 3.5.0 from version 2.1.4), jQuery UI (to version 1.12.1 from version 1.11.4), jQuery qTip (to version 3.0.3 from 2.2.1). Migration guidance has been provided online by jQuery.  |
| **Product areas affected**         | Extensible controls, specifically custom JavaScript code utilizing deprecated or removed APIs |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13/Platform update 37, customers can optionally move to the latest libraries by enabling the "Upgrade three jQuery component libraries" feature. Moving to the new libraries will be mandatory with the April 2021 release to allow time for migration of affected APIs.   |

### Existing grid control/forceLegacyGrid() API

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The existing grid control is being replaced by the new grid control. |
| **Replaced by another feature?**   | The [new grid control](../..//fin-ops/get-started/grid-capabilities.md) |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | The new grid control is mandatory with the October 2022 release (version 10.0.29). The **forceLegacyGrid()** API is currently still being honored if the old grid is still needed; however, this API is targeted to be deprecated by the October 2023 release. When the deprecation of this API is announced, it will be available for at least 12 months before no longer being available. |

### Personalization without saved views 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The personalization subsystem has been overhauled with the saved views feature, so that it has better performance and offers additional capabilities. |
| **Replaced by another feature?**   | Saved views |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | In version 10.0.13/Platform update 37, the saved views feature is generally available, and customers can optionally turn on this feature. The saved views feature will become mandatory in the October 2021 release. |


## Platform updates for version 10.0.12 of finance and operations apps

### Grid or group control form extensions containing invalid field references

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The data group property on grid or group controls is used to automatically show all the fields of a field group. A grid or group control added by extension could contain fields that are no longer defined on the field group, or it might be missing fields that are defined on the field group. This can cause inconsistent behavior at runtime. Platform updates for version 10.0.12 of finance and operations apps now categorize this issue as a compiler *warning*. To fix this issue, open the form extension and save it.
| **Replaced by another feature?**   | This compiler warning will be replaced with a compiler error in a future update. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | A compiler warning is introduced in platform updates for version 10.0.12 of finance and operations apps. |

## Platform updates for version 10.0.11 of finance and operations apps

### Explicit safe lists for self-service environments

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for moving IP to safe lists has changed. Self-service no longer supports IP safe lists. |
| **Replaced by another feature?**   | For more information, see [Configuring Azure Active Directory Conditional Access](/appcenter/general/configuring-aad-conditional-access).|
| **Product areas affected**         | Security |
| **Deployment option**              | Cloud |
| **Status**                         | Deprecated: This feature is fully-deprecated for self-service deployments. |

### Visual Studio 2015

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To support the latest versions of Visual Studio, some changes have to be made to the X++ extensions for Visual Studio. These changes are incompatible with Visual Studio 2015. |
| **Replaced by another feature?**   | Visual Studio 2017 will replace Visual Studio 2015 as the deployed and required version. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Virtual machines deployed on version 10.0.13 (Platform update 37) or later contain Visual Studio 2017. Version 10.0.16 (Platform update 40) is the final release with support for Visual Studio 2015. Virtual machines with only Visual Studio 2015 will not be able to update to version 10.0.17 (Platform update 41). |

### Field groups containing invalid field references

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Field groups in table metadata definitions can contain field references that aren't valid. If these field groups are deployed, they can cause runtime failures in Financial Reporting and Microsoft SQL Server Reporting Services (SSRS). Platform update 23 introduced a compiler *warning* that enabled this metadata issue to be addressed. Platform updates for version 10.0.11 of finance and operations apps categorize this issue as a compiler *error*.<p>To fix this issue, follow these steps.</p><ol><li>Remove the invalid field reference from the table field group definition.</li><li>Recompile.</li><li>Make sure that any errors are addressed.</li></ol> |
| **Replaced by another feature?**   | This compiler error permanently replaces the compiler warning.  |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The compiler warning is a compiler error in platform updates for version 10.0.11 of finance and operations apps. |

### ISV licenses created by using the SHA1 hashing algorithm

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for creating independent software vendor (ISV) licenses has changed. For more information, see [Independent software vendor (ISV) licensing](../dev-tools/isv-licensing.md#appendix-create-self-signed-certificates-for-test-purposes). |
| **Replaced by another feature?**   | Yes. Use Windows PowerShell to create licenses. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: ISV licenses that were created by using the SHA1 hashing algorithm. This algorithm depended on certificates that were created by using the MakeCert utility, and this utility has been deprecated.<br><br>Deprecated: The use of SHA1 for security or hashing purposes. SHA1 will cease to function in early 2021. Therefore, it should no longer be used.<br><br>Removed: Support for Transport Layer Security (TLS) 1.0 and TLS 1.1 incoming or outgoing requests. |

## Platform update 32

### Workflow request change dialog box no longer includes user selection drop-down list

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This was a security issue because the request for change could be sent to an unintended user. This was also a usability issue because it forced the user to determine who the workflow originator was and manually select them.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Workflow |
| **Deployment option**              | All |
| **Status**                         | The user selection drop-down list was removed from the request change dialog box in Platform update 32. Request change requests will be automatically sent to the originator as intended. For more information about this functionality, see [Actions in workflow approval processes](../../fin-ops/organization-administration/workflow-actions.md?toc=%2fdynamics365%2fcommerce%2ftoc.json#request-change). |

### Embedded drill-through links are no longer supported in paginated documents rendered by the cloud-hosted service 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Navigation URLs embedded in documents rendered by the service may contain sensitive business data. We are removing support for embedded drill-through links in documents as a security precaution to further protect customer's data. Users will also benefit from improved performance while interactively producing documents as a result of this change.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Reporting |
| **Deployment option**              | All |
| **Status**                         | This feature is actively being removed from the service.<br><br>The modern client offers numerous options for producing views that include auto-generated links to assist in navigating the application. Paginated documents rendered by the service are recommended for external communications that are emailed, archived, and printed for recipients. We have improved the experience for previewing documents directly in the browser, which offers direct access to local printers. For more information, see [Preview PDF documents with an embedded viewer](../analytics/preview-pdf-documents.md). |

## Previous announcements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../migration-upgrade/deprecated-features.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

