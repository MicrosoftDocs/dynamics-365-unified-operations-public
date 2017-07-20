---
# required metadata

title: Online service and on-premises software lifecycle policy
description: This topic outlines the lifecycle and support policies for both the Dynamics 365 for Finance and Operations, Enterprise edition online service and for Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) software deployments.
author: ryanCcarlson 
manager: AnnBe
ms.date: 06/16/2017
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

# Online service and on-premises software lifecycle policy

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

| Release          |Major or minor release         | Version          | Build number | Availability  | Expiration date | 
|------------------|----------------------|------------------|--------------|---------------|-----------------|
| Microsoft Dynamics 365 for Finance and Operations, Enterprise edition | Major release | July 2017 update | 7.2.11792.56024| June 2017     | June 2020  | 
| Microsoft Dynamics 365 for Operations     | Major release | 1611             | 7.1.1541.3036| November 2016 | November 2019   | 
| Microsoft Dynamics AX |Minor release  | 7.0.1 | 7.0.1265.23014 | May 2016 | June 2017 |
| Microsoft Dynamics AX | Major release | 7.0 | 7.0.1265.3015 | February 2016 | June 2017 |

### Table 2: Platform releases

| Release           | Build number   | Availability  | Expiration date   |
|-------------------|----------------|---------------|-------------------|
| Platform update 8 | 7.0.4565.16212 | June 2017     | June 2018     |
| Platform update 7 | 7.0.4542.16189 | May 2017      | May 2018      |
| Platform update 6 | 7.0.4509.16180 | April 2017    | April 2018    |
| Platform update 5 | 7.0.4475.16165 | March 2017    | March 2018    |
| Platform update 4 | 7.0.4425.16161 | February 2017 | February 2018 |
| Platform update 3 | 7.0.4307.16141 | November 2016 | November 2017 |
| Platform update 2 | 7.0.4230.16130 | August 2016   | August 2017   | 
| Platform update 1 | 7.0.4127.16103 | May 2016      | May 2017      | 
| Platform 7.0      | 7.0.4030.16079 | February 2016 | January 2017  |

## Dates for Finance and Operations (on-premises) releases

The initial release of the Finance and Operations (on-premises) software will be based on Platform update 8 and the July 2017 update of the application.

Microsoft is committed to supporting the deployments of the Finance and Operations (on-premises) software through calendar year 2027, at a minimum, provided that the customer keeps the deployed software current according to the Modern Lifecycle Policy.

| Release                                                                             | Version          | Build number | Availability | Expiration date | Product life  |
|-------------------------------------------------------------------------------------|------------------|--------------|--------------|-----------------|---------------|
| Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) | July 2017 update | 7.2.11792 | June 2017    |  November 2019   | December 2027 |

## Support matrix
The following table provides information about the recent releases of the application and platform for Finance and Operations, and shows which versions are compatible.

|                       | **Dynamics AX 7.0** | **Dynamics AX application 7.0.1** | **Dynamics 365 for Operations (1611)** | **Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update** |
|-----------------------|---------------------|-----------------------------------|----------------------------------------|----------------------------------------------------------------------------------|
| **Platform update 8** | Compatible          | Compatible                        | Compatible                             | Compatible                                                                       |
| **Platform update 7** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 6** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 5** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 4** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 3** | Compatible          | Compatible                        | Compatible                             |                                                                                  |
| **Platform update 2** | Compatible          | Compatible                        |                                        |                                                                                  |
| **Platform update 1** | Compatible          | Compatible                        |                                        |                                                                                  |
| **Platform 7.0**      | Compatible          |                                   |                                        |                                                                                  |



