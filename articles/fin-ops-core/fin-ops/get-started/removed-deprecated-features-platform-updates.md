---
title: Removed or deprecated platform features
description: Learn about features that have been removed, or that are planned for removal in platform updates of finance and operations apps.
author: twheeloc
ms.author: twheeloc
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 08/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-02-29
ms.dyn365.ops.version: Platform update 33
---

# Removed or deprecated platform features

[!include [banner](../../../finance/includes/banner.md)]

This article describes removed features, or features that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61). You can compare the different versions of these reports to learn about objects that are changed or removed in each version of finance and operations apps.


## Feature deprecation effective October 2024

### Disable storage account key access to FnO managed storage accounts

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Improve platform security and disable storage account key access to FnO managed storage accounts. |
| **Replaced by another feature?**   | Microsoft Entra ID based authentication. |
| **What do you need to do?**        | When Allow storage account key access is disabled, any requests to the account that are authorized with Shared Key, including shared access signatures (SAS), will be denied. (Any SAS url generated using GetSharedAccessSignature) <br><br> 1. For customers who haven’t done any kind of customization and interact with the storage account based on the existing exposed platform APIs, the existing functionalities shall remain unaffected. <br><br> 2. For customers where storage connection string is acquired by third-party code that isn't using any public API present in platform, some of the functionalities might get affected. <br> Recommendations: <br> - If Azure.Storage.Blobs is used for storage account interaction, then use user delegated SAS URLs. <br> - If WindowsAzure.Storage v9.3.3 is still being used for storage account interaction, then you can leverage a platform API to get user delegated SAS url. <br><br> Note- LBD and CHE environments shall remain unaffected.  |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Rollout for the change will start from October 2024 is phase wise manner. Changes will be backported to 10.0.41 (PU65) and all greater releases.|

### Migration from deprecated libraries - WindowsAzure.Storage and Microsoft.Azure.Storage to Azure.Storage.Blobs

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Improve platform security and remove dependency on deprecated and out of maintenance nugets : <br> [WindowsAzure.Storage (v9.3.3)](https://www.nuget.org/packages/WindowsAzure.Storage/) (Along with Microsoft.WindowsAzure.StorageClient.dll 6.0.6002.18488 and Microsoft.WindowsAzure.Storage.dll 9.3.2.0)<br> [Microsoft.Azure.Storage.Common (v11.xx)](https://www.nuget.org/packages/Microsoft.Azure.Storage.Common) <br> [Microsoft.Azure.Storage.Blob](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob) (Microsoft.Azure.Storage.Blob.dll 11.2.3 and Microsoft.Azure.Storage.Common.dll 11.2.3) |
| **Replaced by another feature?**   | Use [Azure.Storage.Common](https://www.nuget.org/packages/Azure.Storage.Common/) , [Azure.Storage.Blobs](https://www.nuget.org/packages/Azure.Storage.blobs/), Azure.Storage.* and [Azure.Data.Tables](https://www.nuget.org/packages/Azure.Data.Tables)|
| **What do you need to do?**        | As platform code continues to leverage WindowsAzure.Storage v9.3.3 for storage interaction, alongside the old libraries-based storage classes we parallelly have started the migration of these implementations to Azure.Storage.Blobs. <br> **Customers and ISVs should review their dependencies/ customizations and make necessary changes to move to new libraries by March 2025.** |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | **Phase 1: Release and Feedback (October 2024 - November 2024)** <br> The new code will be released to a select group of users for beta testing. Feedback will be collected, and any necessary adjustments will be made. It will be rolled out fully after all fixes. We will continue to support the old package during this period. <br><br> **Phase 2: Deprecation Timeline for customers (March 2025)** <br> This is the timeline by when customers must move to new libraries. (Tentatively in 10.0.41 PQU-5, 10.0.41 PQU-6 ). <br><br> **Phase 3: Stop shipping old libraries (June 2025)** <br> Support for the old package will end so we will stop shipping the old libraries and the old code will be removed. This will be done only after validating that customer scenarios are not affected using telemetry data. |

### Platform is changing the authentication protocol from password based auth to Microsoft Entra ID based authentication for 10.0.39 and greater releases.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Improve platform security and remove dependency on password-based authentication. |
| **Replaced by another feature?**   | Microsoft Entra ID based authentication. |
| **What do you need to do?**        | This change impacts the following set of functionalities. <br><br> 1. The SQL Connection string acquired by third-party code that isn't using any platforms public API present in platform. <br> <br>**Recommendation**: Switch to public API rather than reading it directly from config. <br><br> 2. Long-running transactions that run for several hours.<br><br> **Recommendation**: Reduce the time the connection is opened and keep the transactions as short-lived as possible. <br><br>  NOTE: LBD and CHE environments still use password-based authentication. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | End of support date is Oct 2024 starting with 10.0.39 (PU63) and greater releases. |

## Feature deprecation effective September 2024

### End of support for sharing storage account connection strings via public API GetCsuStorageConnectionString
Public method: Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString() will be depcrecated. 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Maintaining storage connection string usage is a security issue and we want a more secure approach of connecting to storage account. |
| **Replaced by another feature?**   | A managed service identity based connection will be used to storage account. |
| **What do you need to do?**        | 1. For new tenants, created after August 19th 2024, the connection string won't be available to you and you shall use public APIs from platform SharedServiceUnitStorage class to interact with storage account. <br> <br> 2. For existing tenants, created before August 19th 2024, your current code continues to function, but it is recommended to remove direct dependency on storage connection string and use public methods from SharedServiceUnitStorage as GetCsuStorageConnectionString will be deprecated by March 2025. <br> <br> 3. For ISVs, if you have direct usage of connection string in your solutions, it must be removed and public APIs from SharedServiceUnitStorage shall be used to get relevant storage objects for interacting with storage account. |
| **Product areas affected**         |  Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | The rollout of this change is being done in phases, region by region, starting first with sandbox environments. Then it'll be applied in production environments. The full rollout is estimated in October 2024. Changes are backported to 10.0.39 (PU63) and all greater releases. |

### Microsoft will no longer ship or support the Visual Studio extensions for finance and operations apps, Power Platform tools, and Visual Studio versions prior to 2022.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We want to focus our attention on one platform, harvesting the benefits provided from the 64 bit platform. |
| **Replaced by another feature?**   | [Visual Studio 2022](https://visualstudio.microsoft.com/vs/). |
| **What do you need to do?**        | Install [Visual Studio version 2022](https://visualstudio.microsoft.com/vs/). |
| **Product areas affected**         | Development for finance and operations apps, including the Unified Development experience, and development of plugins with the Power Platform Tools. |
| **Deployment option**              | All |
| **Status**                         | This change is effective as of Platform update 65 and Dynamics 365 Finance version 10.0.41 and later. |

## Feature deprecation effective July 2024

### Azure Active Directory Graph to Microsoft Graph Migration

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance platform security and compliance, we're deprecating Azure Active Directory Graph in finance and operations apps. |
| **Replaced by another feature?**   | Microsoft Graph - To ensure the security and integrity of your system and data, we strongly encourage all our customers to migrate to the more secure Microsoft Graph for making graph calls. |
| **What do you need to do?**         | We strongly recommend that any customers with dependencies on the GraphAPIClient class (responsible for making Azure Active Directory Graph calls) migrate to the MicrosoftGraphClient (responsible for making Microsoft Graph calls) as soon as possible to avoid service disruptions. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | The Support for Azure Active Directory Graph will end in PU66. |

### SharePoint integration authentication using a Microsoft-managed high-trust connection

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The authentication mechanism used to integrate to SharePoint is being removed. |
| **Replaced by another feature?**   | An alternate authentication mechanism is available via the **SharePoint user authentication** feature. For more information about setup, including a one-time permission grant to the application at the tenant level, see [Configure document management](../../dev-itpro/organization-administration/configure-document-management.md). Calling SharePoint as a user that isn't the currently logged in user is no longer supported. |
| **Product areas affected**         | System administration  |
| **Deployment option**              | Microsoft-managed cloud environments |
| **Status**                         | The **SharePoint user authentication** feature is available in Dynamics 365 Finance version 10.0.40, and is mandatory in version 10.0.42. Migration to the new SharePoint authentication must occur by February 28, 2025, at which time the current SharePoint connection stops working. |

## Feature deprecation effective August 2024

### Support for unregistered Microsoft account and external Microsoft Entra ID users

**Login will be blocked for unregistered [Microsoft Account (MSA)](/entra/external-id/microsoft-account) and [External Microsoft Entra ID users](/entra/external-id/default-account) in Finance and Operation Apps**

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance the security and performance of finance and operations apps, we're announcing the deprecation of support for unregistered Microsoft account users and external Microsoft Entra users in finance and operations apps. |
| **What is changing?**   | If a [Microsoft account](/entra/external-id/microsoft-account) or [Microsoft Entra ID account](/entra/external-id/default-account) isn't registered in your Microsoft Entra ID tenant, you aren't able to access finance and operations apps. You receive the following error message: "AADSTS50020: user account '`contoso@contoso.com`;' from identity provider '`https://sts.windows.net/{tenant ID}/`' doesn't exist in tenant '\{tenant name\}' and can't access the application '\{application ID\}'(Finance and operations environment name) in that tenant. The account needs to be added as an external user in the tenant first. Sign out and sign in again with different Microsoft Entra ID user account." The user is blocked at the Microsoft Entra ID tenant level. This change doesn't affect granular delegated admin permissions (GDAP) or CSP users. |
| **What do you need to do?**         | If a user who isn't part of your Microsoft Entra requires access to finance and operations apps, that user must be added to the Microsoft Entra ID tenant as an external user or guest user. For more information, see [B2B collaboration overview](/entra/external-id/what-is-b2b/). |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | This change reaches your environment anytime starting August 2024. |

## Feature deprecation effective April 2024

### Token resource or audience without an environment URL in finance and operations apps 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance security compliance, we're deprecating the use of tokens that aren't acquired with the resource or audience that's set as the environment URL in finance and operations apps. |
| **Replaced by another feature?**   | To ensure the security and integrity of your system and data, we strongly encourage all our customers to ensure that tokens are acquired only with the resource or audience that's set as the environment URL. Failure to comply with this requirement results in API calls in finance and operations apps beginning to fail. We encourage all developers and administrators to update their token acquisition processes accordingly to avoid any disruption in API functionality. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | To enhance security compliance, support for tokens with an audience claim value other than the environment URL is removed by April 2024 for nonproduction environments and by May 2024 for production environments. Platform update 63 and Dynamics 365 finance version 10.0.39 and later. |

To troubleshoot unauthorized 401 errors, see [Check token compliance](../../dev-itpro/data-entities/troubleshoot-service-authentication.md#check-token-compliance).

### Multitenant apps without a service principal in the Microsoft Entra ID tenant 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | [Multitenant apps](/entra/identity-platform/single-and-multi-tenant-apps) that don't have a client service principal have been recognized as vulnerable, because they pose a significant risk of acquiring cross-tenant Open Authorization (OAuth) app-only tokens for multitenant services across arbitrary tenants. To address this security vulnerability, apps without a service principal in the tenant is no longer authenticated. Finance and operations APIs will start to fail from these apps in deprecated environments. To review your onboarded applications, in finance and operations apps, go to **System administration** > **Setup** > **Microsoft Entra applications**. For information about how to review your onboarded applications, see [Register your external application](../../dev-itpro/data-entities/services-home-page.md#register-your-external-application). |
| **Replaced by another feature?**   | To ensure the security and integrity of your system and data, we strongly encourage all our customers to provision the multitenant apps in their Microsoft Entra ID tenant. For more information, see [Create an enterprise application from a multitenant application](/entra/identity/enterprise-apps/create-service-principal-cross-tenant?pivots=ms-graph). Note – If application onboarding isn't expected, remove that app or replace with a compliant app that has a client service principal in tenant. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Support for app-only tokens by multitenant apps that don't have a service principal ID will be removed by February 2024 for nonproduction environments and by April 2024 for production environments. Platform update 63 and Dynamics 365 finance version 10.0.39 and later |

To troubleshoot unauthorized 401 errors, see [Check token compliance](../../dev-itpro/data-entities/troubleshoot-service-authentication.md#check-token-compliance).

## Feature deprecation effective March 2024

### Non Microsoft Entra ID external user sign-in 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're discontinuing onboardings for all users, both Service to Service and Interactive, who aren't present in the Microsoft Entra ID tenant associated with your Finance and Operations environment. Microsoft has flagged this access method as a security concern. For more information, see [Manually add a new user](../sysadmin/create-new-users.md#manually-add-a-new-user).|
| **Replaced by another feature?**   | No, to ensure compliance among existing users, you must either extend invitations to users with the same email addresses to your Microsoft Entra ID or remove these users from the Finance and Operations system, create new user accounts within your Microsoft Entra ID, and proceed to import them accordingly. For more information, refer [How to create or delete users in Microsoft Entra ID - Microsoft Entra](/entra/fundamentals/how-to-create-delete-users).|
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | The rollout for sandbox environments begins from Feb 2024 and for prod environments from March 2024. |

## Feature deprecation effective February 2024

### ISV Licenses generated using SHA1 algorithm (signature version 1)  

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The SHA1 algorithm was widely recognized as vulnerable to security breaches due to its susceptibility to collision attacks. To address this security requirement, imports for ISV licenses that are generated using the SHA1 cryptographic algorithm are longer supported. |
| **Replaced by another feature?**   | SHA256 - To ensure the security and integrity of your system and data, we strongly encourage all our customers to migrate to the more secure SHA256 algorithm for generating ISV licenses. 

Migrating to SHA256 is straightforward: You need to use signature version 2 or keep this field empty while generating license using AxUtil tool to generate a new license using SHA256. For more information, see [Independent software vendor (ISV) licensing](../../dev-itpro/dev-tools/isv-licensing.md). 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Product areas affected**         | System Administration  |
| **Deployment option**              | All |
| **Status**                         | Support for SHA1 is removed by February 2024 (10.0.39/PU63) |

## Feature deprecation effective January 2024

### System Admin > Inquiries > User Log 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The **Inquiries** > **User Log** is a legacy page that was built for the older client/server architecture. The information on this page isn't always accurate and can be misleading. |
| **Replaced by another feature?**   | In finance and operations apps, this information is captured in telemetry and Lifecycle Services has details. For more information, see [Track user sign-ins](../../dev-itpro/lifecycle-services/user-logins.md). |
| **Product areas affected**         | System Administration  |
| **Deployment option**              | All |
| **Status**                         | The User Log page will be removed by Jan 12 2024 (10.0.38/PU62) |

### Exchange email provider

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The authentication mechanism that the Exchange email provider uses is being removed, and the Exchange provider never supported sovereign clouds. |
| **Replaced by another feature?**   | Customers who use the Exchange email provider should migrate to the Microsoft Graph email provider. For more information, see [Configure and send email](../../dev-itpro/organization-administration/configure-email.md). |
| **Product areas affected**         | System administration  |
| **Deployment option**              | All |
| **Status**                         | The Exchange email provider stops sending emails as of September 15, 2024. |

## Feature deprecation effective October 2022

### Microsoft SQL Server 14.x or older 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're discontinuing support for Microsoft SQL Server 14.x and older versions in Finance and Operations (Dynamics 365), as active support for 14.x ended in October 2022. Starting from 10.0.40 (PU 64), there may be SQL-related updates in FinOps that aren't compatible with older versions of MS SQL Server. |
| **Replaced by another feature?**   | Yes, customers can use Microsoft SQL Server 15.x or higher with their Finance and Operations (Dynamics 365).|
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. End of support date is targeted for 10.0.28 (PU 52), which went out of support on October 21, 2022. |


## Feature deprecation effective August 2022

### Lifecycle Services features deprecated in August 2022

As part of the [One Dynamics One Platform](/dynamics365-release-plan/2022wave2/finance-operations/finance-operations-crossapp-capabilities/one-dynamics-one-platform) work effort, the following Lifecycle Services features are deprecated.

| Feature name | Used with AX 2012? | Used with finance and operations apps? | Replaced by another feature? |
|--------------|--------------------|----------------------------------------|------------------------------|
| Announcements | Yes | Yes | Yes: Banners exist on individual project and environment pages for notifications. |
| Configuration manager | Yes | No | No |
| Crash and dump analysis | Yes | No | No |
| Feedback and bugs | Yes | Yes | No |
| My subscription | Yes | Yes | No |
| Office 365 | Yes | Yes | Yes: Microsoft Entra ID or Microsoft admin portal. |
| Impact analysis | No | Yes | No |
| Total economic impact estimator | No | Yes | No |
| Service requests | No | Yes | Yes: [Self-service deployments](../../dev-itpro/deployment/infrastructure-stack.md) |
| SharePoint integration | Yes | Yes | No |
| Configuration and data manager | No | Yes | No |
| Process data packages | No | Yes | Yes: [Data Import Export Framework (DIXF)](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job) |
| Environment upgrade | No | Yes | Yes: [One Version](../../dev-itpro/lifecycle-services/oneversion-overview.md) service updates are available. |
| Infrastructure estimator | Yes | No | No |
| License sizing | Yes | No | No |
| Usage profiler | Yes | No | No |
| Customization analysis | Yes | No | No |
| System diagnostics | Yes | Yes | No |
| Business process modeler Visio management | Yes | Yes | No |
| AX 2012 cloud environment management | Yes | No | No |
| RDFE Azure connectors | Yes | Yes | No |
| AX 2012 versions | Yes | No | No |
| Work items stored in Lifecycle Services storage | Yes | Yes | No |
| Hotfix requests | Yes | Yes | No |
 

### Transport Layer Security (TLS) RSA cipher suites

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The following list of cipher suites is removed to comply with our current security protocols.<br><br>TLS_RSA_WITH_AES_256_GCM_SHA384<br>TLS_RSA_WITH_AES_128_GCM_SHA256<br>TLS_RSA_WITH_AES_256_CBC_SHA256<br>TLS_RSA_WITH_AES_128_CBC_SHA256<br>TLS_RSA_WITH_AES_256_CBC_SHA<br>TLS_RSA_WITH_AES_256_CBC_SHA  |
| **Replaced by another feature?**   | Beginning January 2023, customers can only use our [standard cipher suites](/power-platform/admin/server-cipher-tls-requirements). This change impacts your clients and servers that communicate with our servers. For example, it may impact your third party integrations that aren't adhering to our standard cipher suites. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | Cloud deployments |
| **Status**                         | Deprecated. Customers must upgrade their servers before January 2023. For more information about configuring TLS Cipher Suite order, see [Manage Transport Layer Security (TLS)](/windows-server/security/tls/manage-tls).  |


## Feature deprecation effective June 2022

### Finance and operations (Dynamics 365) mobile application and mobile platform 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating the finance and operations (Dynamics 365) mobile application and platform to consolidate to a single mobile platform, which is Power Apps. |
| **Replaced by another feature?**   | Yes, mobile experiences over finance and operations app data can be built with Power Platform integration. For more information, see the blog post [What’s happening to the Finance and Operations (Dynamics 365) mobile workspaces?](https://cloudblogs.microsoft.com/dynamics365/it/2022/06/03/finance-and-operations-dynamics-365-mobile-app-to-be-deprecated/) and [Building mobile experiences](../../dev-itpro/power-platform/build-mobile-experiences.md). |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. End of support date is targeted for October 2024. |


## Platform updates for version 10.0.29 of finance and operations apps

### Panorama tab style

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Horizontally scrolling pages align to outdated layout patterns that have known usability and accessibility issues.  |
| **Replaced by another feature?**   | No, but other tab styles are still available. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. |


## Feature deprecation effective April 2022

### XML URL resolution in Data management 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're removing support for XML URL resolution since it was identified as a potential security vulnerability. This change means that external resources associated with XML files are no longer resolved.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated. |

## Feature deprecation effective March 14, 2022

### XSLT scripting in Data management

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The support for XSLT scripting in Data management is deprecated to improve security and data protection within finance and operations apps.  |
| **Replaced by another feature?**   | No, customers and ISVs should consider reimplementing their solutions based on X++ language, in place of XSLT scripting. |
| **Product areas affected**         | Finance and operations apps |
| **Deployment option**              | All |
| **Status**                         | Deprecated <br><br>**Exception:** Customers who are currently using XLST scripting can continue to use it until they update to version 10.0.30 or later. For earlier versions, the exception expires effective January 31, 2023. Customers with this exception have received a notification in the Message center available in the Microsoft 365 Admin Center. |

## Feature removal effective October 2021

### Microsoft Azure SQL reports in Lifecycle Services

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | All activities and monitoring are performed internally, by the platform, through automation. This change won't require any manual intervention.|
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL reports: Current DTU, Current DTU Details, Get Lock Details, List of Current Plan Guide, Get List of Query IDs, Get the SQL query plan for a given Plan ID, Get query plans and execution status, Get throttle config, Get wait stats, List most expensive queries |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Removed |

### Azure SQL actions in Lifecycle Services

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating some SQL actions in Lifecycle Services. All activities and monitoring are performed internally, by the platform, through automation. This change won't require any manual intervention. |
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL actions: Create a plan guide to force Plan ID, Create a plan guide to add table hints, Remove Plan guide, Disable/Enable page locks, and lock escalation, Update statistics on a table, Rebuild Index, Create Index |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Removed |


## Feature deprecation effective October 2021

### "Show related document attachments" feature

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The feature was returning unexpected results. |
| **Replaced by another feature?**   | No, any further plans regarding this functionality is communicated through our standard release wave disclosure process. |
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
| **Reason for deprecation/removal** | Microsoft requires more parameters when adding notifications. |
| **Replaced by another feature?**   | Yes, the **SystemNotificationsManager.AddSystemNotification()** API. This API requires that you explicitly set ExpirationDateTime and RuleID for generated notifications. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. Planned removal date is April 2023. |

## Platform updates for version 10.0.21 of finance and operations apps

### Skype for Business Online support

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Skype for Business Online was retired. For more information, see [The Skype for Business Online service has retired](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/the-skype-for-business-online-service-has-retired/ba-p/2596601). |
| **Replaced by another feature?**   | Not currently, although we may consider adding presence from Teams in the future.|
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated. The **Skype enabled** setting was turned off starting in release 10.0.21. The removal of this setting is targeted for April 2022; however, the feature stops functioning after the Skype team shuts down the service. |
 
## Feature deprecation effective August 2021

### Microsoft Azure SQL reports in Lifecycle Services

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | All activities and monitoring are performed internally, by the platform, through automation. This change won't require any manual intervention.|
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL reports: Current DTU, Current DTU Details, Get Lock Details, List of Current Plan Guide, Get List of Query IDs, Get the SQL query plan for a given Plan ID, Get query plans and execution status, Get throttle config, Get wait stats, List most expensive queries |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Deprecated: Planned removal date is October 2021. |

### Azure SQL actions in Lifecycle Services

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating some SQL actions in Lifecycle Services. All activities and monitoring are performed internally, by the platform, through automation. This change won't require any manual intervention. |
| **Replaced by another feature?**   | Yes, there's now an automated system, which renders these capabilities obsolete. |
| **Product areas affected**         | SQL actions: Create a plan guide to force Plan ID, Create a plan guide to add table hints, Remove Plan guide, Disable/Enable page locks and lock escalation, Update statistics on a table, Rebuild Index, Create Index |
| **Deployment option**              | Cloud deployment: Affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | Deprecated: Planned removal date is October 2021. |

## Feature deprecation effective May 2021

### Globalization portal in Lifecycle Services

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We're deprecating the Globalization portal in Lifecycle Services as this feature was superseded by other Lifecycle Services-based services. |
| **Replaced by another feature?**   | Yes, Lifecycle Services [Issue search](../../dev-itpro/lifecycle-services/issue-search-lcs.md) and [Dynamics regulatory alert submission service](../../dev-itpro/lcs-solutions/submit-localization-alerts.md) replace this feature. |
| **Product areas affected**         | Globalization portal in Lifecycle Services|
| **Deployment option**              | Cloud deployment |
| **Status**                         | Deprecated: Planned removal date is May 2022. |


## Feature removed effective January 28, 2021

### Batch job to handle SQL index defragmentation

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In order to reduce the overhead of operating, monitoring, and maintaining the index management by customers, this feature was removed. |
| **Replaced by another feature?**   | After this update, Microsoft services performs the index maintenance. This maintenance happens continuously without affecting the user workloads. |
| **Product areas affected**         | Finance and operations apps|
| **Deployment option**              | Cloud deployment - affects Microsoft-managed production environments and Tier 2 through Tier 5 sandbox environments. |
| **Status**                         | This feature is removed. |


## Platform updates for version 10.0.17 of finance and operations apps


### Visual Studio 2015

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To support the latest versions of Visual Studio, some changes have to be made to the X++ extensions for Visual Studio. These changes are incompatible with Visual Studio 2015. |
| **Replaced by another feature?**   | Visual Studio 2017 replaces Visual Studio 2015 as the deployed and required version. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: After you update to version 10.0.17, the previous X++ tools are removed from Visual Studio 2015, and the updated tools won't install on Visual Studio 2015. There isn't an impact on hosted builds. For build virtual machines, the build pipeline (build definition) needs to be manually updated to change the dependency from MSBuild 14.0 (Visual Studio 2015) to MSBuild 15.0 (Visual Studio 2017) as described in [Update a legacy pipeline in Azure Pipelines](../../dev-itpro/dev-tools/pipeline-msbuild-update.md). |

### User avatar 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The user avatar that displays on the right side of the navigation bar was retrieved using an API from the Dynamics 365 header control, which was deprecated. |
| **Replaced by another feature?**   | Users see their initials in a circle in the navigation bar instead. This same visual is currently used on development machines. |
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
| **Status**                         | Deprecated: All EP code is removed in the October 2021 release. |

## Deprecation effective December 2020

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products and Dynamics Lifecycle Services is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This change impacts customers who use Dynamics 365 products and Lifecycle Services that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products and Lifecycle Services. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products and Lifecycle Services |
| **Deployment option**              | All|
| **Status**                         | Deprecated: Internet Explorer 11 won’t be supported after August 2021.|

## Platform updates for version 10.0.15 of finance and operations apps

### Visual Studio add-in to apply metadata hotfixes

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Metadata hotfixes are no longer supported with the [One Version](../../dev-itpro/get-started/one-version.md) service updates that were introduced in July 2018 with version 8.1. |
| **Replaced by another feature?**   | Individual metadata hotfixes aren't available for supported versions. Cumulative quality updates are applied instead. |
| **Product areas affected**         | Visual Studio add-ins |
| **Deployment option**              | Development virtual machines |
| **Status**                         | With version 10.0.15, the add-in is no longer included in the Visual Studio tools. |


## Platform updates for version 10.0.14 of finance and operations apps

### Online users page 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The Online users page is a legacy page that was built for previous client/server architecture. The information on this page isn't always accurate, which can be confusing and misleading. |
| **Replaced by another feature?**   | We'll provide a new page in a future update. As a workaround, use the table browser for the SysClientSessions table to view client sessions.|
| **Product areas affected**         | System Administration |
| **Deployment option**              | All |
| **Status**                         | This page will be removed in a future release.   |


## Platform updates for version 10.0.13 of finance and operations apps


### Custom code that's defined in SSRS report properties 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In general, custom code offers limited benefits while at the same time, requires significant resourcing and compute to support. Custom code is primarily used by report authors to call public methods from a custom code assembly. However, the cloud-hosted service doesn't support references to custom assemblies for SSRS reports. |
| **Replaced by another feature?**   | Report authors may choose to continue referencing public .NET APIs for Math, Conversion, and Format operations from any textbox expression. For more information, see [Add Code to a Report (SSRS)](/sql/reporting-services/report-design/add-code-to-a-report-ssrs).  |
| **Product areas affected**         | Subset of application report designs that are defined in RDL and contain custom code. |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13, the compiler begins issuing a warning for instances where custom code is detected in an SSRS report definition. To fix the issue, open the report design definition and remove all custom code artifacts. This warning will be replaced with a compiler error in a future update.   |

### Upgrade of three jQuery component libraries 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Three jQuery component libraries are being updated for security fixes and to maintain currency.   
| **Replaced by another feature?**   | The following libraries are being affected: jQuery (to version 3.5.0 from version 2.1.4), jQuery UI (to version 1.12.1 from version 1.11.4), jQuery qTip (to version 3.0.3 from 2.2.1). Migration guidance was provided online by jQuery.  |
| **Product areas affected**         | Extensible controls, custom JavaScript code utilizing deprecated or removed APIs. |
| **Deployment option**              | All |
| **Status**                         | With version 10.0.13/Platform update 37, customers can optionally move to the latest libraries by enabling the "Upgrade three jQuery component libraries" feature. Moving to the new libraries are mandatory with the April 2021 release to allow time for migration of affected APIs.   |

### Existing grid control/forceLegacyGrid() API

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The new grid control replaces existing grid control. |
| **Replaced by another feature?**   | The [new grid control](../../dev-itpro/get-started/grid-capabilities.md) |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | The new grid control is mandatory with the October 2022 release (version 10.0.29). The **forceLegacyGrid()** API is currently still being honored if the old grid is still needed; however, this API is deprecated in the October 2023 release. When the deprecation of this API is announced, it's available for at least 12 months before no longer being available. |

### Personalization without saved views 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The personalization subsystem was overhauled with the saved views feature, so that it has better performance and offers more capabilities. |
| **Replaced by another feature?**   | Saved views |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | In version 10.0.13/Platform update 37, the saved views feature is generally available, and customers can optionally turn on this feature. The saved views feature becomes mandatory in the October 2021 release. |


## Platform updates for version 10.0.12 of finance and operations apps

### Grid or group control from extensions containing invalid field references

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The data group property on grid or group controls is used to automatically show all the fields of a field group. A grid or group control added by extension could contain fields that are no longer defined on the field group, or it might be missing fields defined on the field group. This can cause inconsistent behavior at runtime. Platform updates for version 10.0.12 of finance and operations apps now categorize this issue as a compiler *warning*. To fix this issue, open the form extension and save it.
| **Replaced by another feature?**   | This compiler warning will be replaced with a compiler error in a future update. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | A compiler warning is introduced in platform updates for version 10.0.12 of finance and operations apps. |

## Platform updates for version 10.0.11 of finance and operations apps

### Explicit safe lists for self-service environments

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The process for moving IP to safe lists changed. Self-service no longer supports IP safe lists. |
| **Replaced by another feature?**   | For more information, see [Configuring Conditional Access](/appcenter/general/configuring-aad-conditional-access).|
| **Product areas affected**         | Security |
| **Deployment option**              | Cloud |
| **Status**                         | Deprecated: This feature is fully deprecated for self-service deployments. |

### Visual Studio 2015

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To support the latest versions of Visual Studio, some changes have to be made to the X++ extensions for Visual Studio. These changes are incompatible with Visual Studio 2015. |
| **Replaced by another feature?**   | Visual Studio 2017 replaces Visual Studio 2015 as the deployed and required version. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Virtual machines deployed on version 10.0.13 (Platform update 37) or later contain Visual Studio 2017. Version 10.0.16 (Platform update 40) is the final release with support for Visual Studio 2015. Virtual machines with only Visual Studio 2015 can't update to version 10.0.17 (Platform update 41). |

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
| **Reason for deprecation/removal** | The process for creating independent software vendor (ISV) licenses has changed. For more information, see [Independent software vendor (ISV) licensing](../../dev-itpro/dev-tools/isv-licensing.md#appendix-create-self-signed-certificates-for-test-purposes). |
| **Replaced by another feature?**   | Yes. Use Windows PowerShell to create licenses. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: ISV licenses that were created by using the SHA1 hashing algorithm. This algorithm depended on certificates that were created by using the MakeCert utility, and this utility was deprecated.<br><br>Deprecated: The use of SHA1 for security or hashing purposes. SHA1 ceases to function in early 2021. Therefore, it should no longer be used.<br><br>Removed: Support for Transport Layer Security (TLS) 1.0 and TLS 1.1 incoming or outgoing requests. |

## Platform update 32

### Workflow request change dialog box no longer includes user selection drop-down list

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The user selection drop-down list was a security issue because the request for change could be sent to an unintended user. This is a usability issue because it forced the user to determine who the workflow originator was and manually select them.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Workflow |
| **Deployment option**              | All |
| **Status**                         | The user selection drop-down list was removed from the request change dialog box in Platform update 32. Request change requests are automatically sent to the originator as intended. For more information about this functionality, see [Actions in workflow approval processes](../organization-administration/workflow-actions.md?toc=%2fdynamics365%2fcommerce%2ftoc.json#request-change). |

### Embedded drill-through links are no longer supported in paginated documents rendered by the cloud-hosted service 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Navigation URLs embedded in documents rendered by the service may contain sensitive business data. We're removing support for embedded drill-through links in documents as a security precaution to further protect customer's data. Users benefit from improved performance while interactively producing documents as a result of this change.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Reporting |
| **Deployment option**              | All |
| **Status**                         | This feature is actively being removed from the service.<br><br>The modern client offers numerous options for producing views that include auto generated links to help navigating the application. Paginated documents rendered by the service are recommended for external communications that are emailed, archived, and printed for recipients. We have improved the experience for previewing documents directly in the browser, which offers direct access to local printers. For more information, see [Preview PDF documents with an embedded viewer](../../dev-itpro/analytics/preview-pdf-documents.md). |

## Previous announcements about removed or deprecated features
To learn more about removed or deprecated features in previous releases, see [Removed or deprecated features in previous releases](../../dev-itpro/migration-upgrade/deprecated-features.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
