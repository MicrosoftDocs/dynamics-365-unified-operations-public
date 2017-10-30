---
# required metadata

title: Software lifecycle policy and list of releases
description: This topic outlines the lifecycle and support policies for both the Dynamics 365 for Finance and Operations, Enterprise edition online service and for Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) software deployments.
author: ryanCcarlson 
manager: AnnBe
ms.date: 09/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 69914

ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Software lifecycle policy and list of releases

[!include[banner](../includes/banner.md)]

This topic outlines the lifecycle and support policies for both the Microsoft Dynamics 365 for Finance and Operations, Enterprise edition online service and for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) software deployments.

> [!NOTE]
> Dynamics 365 for Operations (on-premises) is currently being renamed. You will see Dynamics 365 for Operations (on-premises) referenced throughout communications and licensing guides. The in-product name that you will see when deploying the product is Dynamics 365 for Finance and Operations, Enterprise edition. Both of these names refer to the same product.

## Modern Lifecycle Policy

The Modern Lifecycle Policy covers products and services that are serviced and supported continuously. For more information about this policy, see [Modern Lifecycle Policy](https://support.microsoft.com/en-us/help/30881).

The Finance and Operations online service and the Finance and Operations (on-premises) software are covered by the Modern Lifecycle Policy. Licensed customers must stay current with updates to the Finance and Operations online service or the Finance and Operations (on-premises) software in accordance with the following servicing and system requirements:

- Starting with the release of Microsoft Dynamics 365 for Operations version 1611, application versions are supported for three years from the initial date of a major release, as specified in Table 1 later in this topic.
- Platform versions are supported for one year as specified in Table 3 later in this topic. Platform versions maintain backward compatibility. See the support matrix table below for more detail. Critical fixes and non-critical updates are handled in the following way:

    - **Critical fixes** – Microsoft may provide a customer with a hotfix for their current platform version of Finance and Operations, or a fix may be provided in the latest platform version of Finance and Operations, at its discretion.
    - **Non-critical updates** – Customers must update to the most current Finance and Operations platform version to deploy non-critical updates.    
    For more information about platform versions, see [Finance and Operations cloud platform monthly updates FAQ](../sysadmin/faq-platform-monthly-updates.md).

## Online service update policies

- **Finance and Operations platform updates** can be initiated by Microsoft, or they can be initiated by the customer through Microsoft Dynamics Lifecycle Services (LCS).
- **Finance and Operations application updates** can be initiated by the customer through LCS.

Before updates are applied to the customer’s production environment, the customer must test them in a sandbox environment. After the customer tests the updates and provides consent, the updates will be rolled out to production environments. For information about how the sandbox environment will be provided, see the [Microsoft Dynamics 365 Licensing Guide](https://www.microsoft.com/en-us/dynamics365/pricing).

> [!IMPORTANT]
> To help protect our customers, and the Finance and Operations online service, Microsoft might apply critical fixes directly to a customer's Finance and Operations environments. If a critical fix must be applied, Microsoft will notify the customer about the required downtime window (if there will be any downtime) and apply the fix to the applicable environment. After fixes are applied, Microsoft will communicate completion to the customer.

## On-premises software update policies

The customer is in full control of its on-premises deployments and must follow this policy. The customer is in control of installing updates in its on-premises environments. Microsoft will support the Finance and Operations (on-premises) software through December 31, 2027, at a minimum, but only if the customer keeps the deployed software current according to this policy.

The Finance and Operations (on-premises) software is licensed and supported under the [Modern Lifecycle Policy](https://support.microsoft.com/en-us/help/30881/modern-lifecycle-policy). This policy requires that the customer maintain Software Assurance (SA) or the Enhancement Plan, and that it deploy updates as noted later in this topic. Customers who want to use the Fixed Support Lifecycle Policy (5+5) must downgrade to Microsoft Dynamics AX 2012 R3. If a customer lapses on SA or the Enhancement Plan, it will be eligible only for the perpetual license rights to AX 2012 R3 and must uninstall the Finance and Operations (on-premises) software.

The initial release of the Finance and Operations (on-premises) software will be based on Platform update 8 and the July 2017 update of the application.

## Dates and versions for Finance and Operations application and platform releases

### Table 1: Application releases

For information about the new features included in each release, click the links in the **Version** column.

| Release          |Major or minor release         | Version          | Build number | Availability  | Expiration date | 
|------------------|----------------------|------------------|--------------|---------------|-----------------|
|  Dynamics 365 for Finance and Operations, Enterprise edition | Major release | [July 2017](../../fin-and-ops/get-started/whats-new-application-july-2017-update.md) | 7.2.11792.56024| June 2017     | June 2020  | 
|  Dynamics 365 for Operations     | Major release | [1611](../../fin-and-ops/get-started/whats-new-dynamics-365-operations-1611.md) | 7.1.1541.3036| November 2016 | November 2019   | 
|  Dynamics AX |Minor release  | [7.0.1](../../fin-and-ops/get-started/whats-new-changed-application-version-7-0-1-may-2016.md) | 7.0.1265.23014 | May 2016 | June 2017 | 
|  Dynamics AX | Major release | [7.0](../../fin-and-ops/get-started/whats-new-changed-7-0-february-2016.md) | 7.0.1265.3015 | February 2016 | June 2017 | 

### Table 2: Application updates

The application updates listed below consist of a small subset of application enhancements released on top of Dynamics 365 for Finance and Operations, Enterprise edition (July 2017). These updates don't affect the support lifecycle of the release--support is in-line with the policies for the July 2017 release.

For information about the new features included in each update, click the links in the **Version** column.

| Release          | Version          | Build number | Availability  |  
|------------------|------------------|--------------|---------------|
|  Dynamics 365 for Finance and Operations, Enterprise edition | Application update 4: [KB 4047325Application Update 4 for Dynamics 365 for Finance and Operations (Binary part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4047325&bugId=3866272&qc=dfcd40f8c5d0d863cc6ae10fe7dd3fb57450327d4f82f10c57886d579e6d4838), [KB 4047321Application Update 4 for Dynamics 365 for Finance and Operations (X++ part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4047321&bugId=3866273&qc=dfcd40f8c5d0d863cc6ae10fe7dd3fb57450327d4f82f10c57886d579e6d4838) | 7.2.11792.62370 | September 2017     ||  Dynamics 365 for Finance and Operations, Enterprise edition | Application update 3: [KB 4043284Application Update 3 for Dynamics 365 for Finance and Operations (Binary part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4043284&bugId=3857197&qc=e6921e68e9b9037bf91c26b3b553e479890731b4b4dd5e6dcb45b0ca13895d8d), [KB 4043285Application Update 3 for Dynamics 365 for Finance and Operations (X++ part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4043285&bugId=3857199&qc=54ee2e988aace65d26834ced54cc11326f5d5e435520ccaf951d41bd1276f672) | 7.2.11792.62370 | September 2017     | 
|  Dynamics 365 for Finance and Operations, Enterprise edition | Application update 2: [KB 4039142Application Update 2 for Dynamics 365 for Finance and Operations (Binary part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4039142&bugId=3850590&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df), [KB 4039487Application Update 2 for Dynamics 365 for Finance and Operations (X++ part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4039487&bugId=3850591&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df) | 7.2.11792.62192 | September 2017     | 
|  Dynamics 365 for Finance and Operations, Enterprise edition | Application update 1: [KB 4035749Application Update 1 for Dynamics 365 for Finance and Operations (Binary part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4035749&bugId=3845890&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df), [KB 4035751Application Update 1 for Dynamics 365 for Finance and Operations (X++ part)*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4035751&bugId=3845891&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df) | 7.2.11792.62089 | July 2017     | 

\* The link points to a Knowledge Base (KB) article. You must log in to Lifecycle Services (LCS) to view the KB article.

### Table 3: Platform releases

For information about the new features included in each release, click the links in the **Release** column.

| Release           | Build number   | Availability  | Expiration date   |
|-------------------|----------------|---------------|-------------------|
| [Platform update 11](../../fin-and-ops/get-started/whats-new-platform-update-11.md)| 7.0.4679.35176 | October 2017   | October 2018   |
| [Platform update 10](../../fin-and-ops/get-started/whats-new-platform-update-10.md)| 7.0.4641.16233 | August 2017   | August 2018   |
| [Platform update 9](../../fin-and-ops/get-started/whats-new-platform-update-9.md) | 7.0.4612.35162 | July 2017     | July 2018     |
| [Platform update 8](../../fin-and-ops/get-started/whats-new-platform-update-8.md) | 7.0.4565.16212 | June 2017     | June 2018     |
| [Platform update 7](../../fin-and-ops/get-started/whats-new-platform-update-7.md) | 7.0.4542.16189 | May 2017      | May 2018      |
| [Platform update 6](../../fin-and-ops/get-started/whats-new-platform-update-6.md) | 7.0.4509.16180 | April 2017    | April 2018    |
| [Platform update 5](../../fin-and-ops/get-started/whats-new-platform-update-5.md) | 7.0.4475.16165 | March 2017    | March 2018    |
| [Platform update 4](../../fin-and-ops/get-started/whats-new-platform-update-4.md) | 7.0.4425.16161 | February 2017 | February 2018 |
| [Platform update 3](../../fin-and-ops/get-started/whats-new-platform-update-3.md) | 7.0.4307.16141 | November 2016 | November 2017 |
| [Platform update 2](../../fin-and-ops/get-started/whats-new-platform-update-2.md) | 7.0.4230.16130 | August 2016   | August 2017   | 
| [Platform update 1](../../fin-and-ops/get-started/whats-new-changed-platform-version-7-1-may-2016.md) | 7.0.4127.16103 | May 2016      | May 2017      | 
| [Platform 7.0](../../fin-and-ops/get-started/whats-new-changed-7-0-february-2016.md)      | 7.0.4030.16079 | February 2016 | January 2017  |

## Dates for Finance and Operations (on-premises) releases

The initial release of the Finance and Operations (on-premises) software will be based on Platform update 8 and the July 2017 update of the application.

Microsoft is committed to supporting the deployments of the Finance and Operations (on-premises) software through calendar year 2027, at a minimum, provided that the customer keeps the deployed software current according to the Modern Lifecycle Policy.

| Release                                                                             | Version          | Build number | Availability | Expiration date | Product life  |
|-------------------------------------------------------------------------------------|------------------|--------------|--------------|-----------------|---------------|
| Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) | July 2017  | 7.2.11792 | June 2017    |  June 2020   | December 2027 |

## Support matrix
The following table provides information about the recent releases of the application and platform for Finance and Operations, and shows which versions are compatible.

|                       | **Dynamics AX 7.0** | **Dynamics AX application 7.0.1** | **Dynamics 365 for Operations (1611)** | **Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) and later** |
|-----------------------|---------------------|-----------------------------------|----------------------------------------|----------------------------------------------------------------------------------|
| **Platform update 11** | Compatible          | Compatible                        | Compatible                             | Compatible                                                                       |
| **Platform update 10** | Compatible          | Compatible                        | Compatible                             | Compatible                                                                       |
| **Platform update 9** | Compatible          | Compatible                        | Compatible                             | Compatible                                                                       |
| **Platform update 8** | Compatible          | Compatible                        | Compatible                             | Compatible                                                                       |
| **Platform update 7** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 6** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 5** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 4** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 3** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 2** | Compatible          | Compatible                        |                                        |                                                                                  |
| **Platform update 1** | Compatible          | Compatible                        |                                        |                                                                                  |
| **Platform 7.0**      | Compatible          |                                   |                                        |                                                                                  |

Related topics: 
- [Finance and Operations cloud platform monthly updates FAQ](../sysadmin/faq-platform-monthly-updates.md)
- [Modern Lifecycle Policy](https://support.microsoft.com/en-us/help/30881/modern-lifecycle-policy)

