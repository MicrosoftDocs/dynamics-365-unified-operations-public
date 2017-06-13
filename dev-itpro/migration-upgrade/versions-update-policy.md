---
# required metadata

title: Online service and on-premises software lifecycle policy
description: This topic outlines the lifecycle and support policies for the Dynamics 365 for Finance and Operations, Enterprise edition online service and on-premises software deployments.
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
# ms.reviewer: 71
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 69914
ms.assetid: cdc3fbe4-fa45-49fa-be97-caef16b58090
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---
# Online service and on-premises software lifecycle policy

[!include[banner](../includes/banner.md)]

This document outlines the lifecycle and support policies for the Dynamics 365 for Finance and Operations, Enterprise edition online service and the Dynamics 365 for Finance and Operations, Enterprise edition on-premises software deployments.

## Modern Lifecycle Policy

The Modern Lifecycle Policy covers products and services that are serviced and supported continuously. For more information about this policy, click [here](https://support.microsoft.com/en-us/help/30881).

The Finance and Operations online service and the Finance and Operations on-premises software is covered by the Modern Lifecycle Policy. Licensed customers must stay current with updates to the Finance and Operations online service or on-premises software in accordance with the following servicing and system requirements:

-   Application versions are supported for three years from the initial date of a major release as specified in Table 1 below; and

-   Platform versions are supported as follows and as further specified in Table 3:

    -   **Critical fixes:** One year from date Microsoft releases the cloud and on-premises platform version.

    -   **Non-critical updates:** Customers must update to the most current Finance and Operations platform version in order to deploy non-critical updates.

**Note:** Platform versions maintain backward compatibility.

## Online service update policies

-   **Finance and Operations platform updates** may be initiated by Microsoft or by the customer using Lifecycle Services. After the customer tests the updates and provides consent, the updates will be rolled out to production environments.

-   **Finance and Operations application updates** can be initiated by the customer using Lifecycle Services.

Before updates are applied to the customer’s production environment, they must be tested by the customer in a sandbox environment. For details about how the sandbox environment will be provided, see the [Dynamics 365 Licensing Guide-NEED LINK](https://www.microsoft.com/en-us/dynamics365/pricing).

**Important:** To help protect our customers and the online service, Microsoft may apply critical fixes directly to your Finance and Operations environments. If a critical fix must be applied, Microsoft will notify the customer of the required downtime window (if any) and apply the fix to the applicable environment. After fixes are applied, Microsoft will communicate completion to the customer.

## On-premises software update policies

The customer is in full control of its on-premises deployments and must follow this policy. The customer is in control of installing the updates in their on-premises environments. Microsoft will support the Finance and Operations on-premises software through December 31, 2027, at a minimum, but only if the customer keeps the deployed on-premises software current according to this policy.

The Finance and Operations on-premises software is licensed and supported under the [Modern Lifecycle Policy](https://support.microsoft.com/en-us/help/30881/modern-lifecycle-policy). This requires the customer to maintain Software Assurance (“SA”) or the Enhancement Plan and deploy updates as noted in Table 2 below. Customers who want to use the Fixed Support Lifecycle Policy (5+5), must downgrade to Microsoft Dynamics AX 2012 R3. If a customer lapses on SA or the Enhancement Plan, that customer will be eligible only for the perpetual license rights to Microsoft Dynamics AX 2012 R3 and must uninstall the Finance and Operations on-premises software.

The initial release of the on-premises software will be based on Platform update 8 and the July 2017 version of the applicaiton.

## Dates and versions for Finance and Operations application and platform releases

### Table 1: Application releases
-----------------------------

| Release              | Version   | Build Number | Availability  | Expiration date | Product life  |
|----------------------|-----------|--------------|---------------|-----------------|---------------|
|   Dynamics 365 for Finance and Operations, Entrprise edition  | July 2017 update | 7.2.XXXX | July 2017       | November 2019   | December 2027 |
| Dynamics 365 for Operations         | 1611      | 7.1.1541     | November 2016 | November 2019   | December 2027 |



### Table 2: Retail application release

| Release                | Version | Build Number | Availability | Expiration date | Product life  |
|------------------------|---------|--------------|--------------|-----------------|---------------|
| Dynamics 365 for Retail |   July 2017 update    | 7.2.XXXX   | July 2017         | ?               | December 2027 |

### Table 3: Platform releases

| Release           | Build Number    | Availability  | Expiration date  | Product Life  |
|-------------------|-----------------|---------------|------------------|---------------|
| Platform update 7 |  7.0.4542.16189 | May 2017      | May 31, 2018    | December 2027 |
| Platform update 6 |  7.0.4509.16180 | April 2017    | April 30, 2018     | December 2027 |
| Platform update 5 |  7.0.4475.16165 | March 2017    | March 31, 2018      | December 2027 |
| Platform update 4 |  7.0.4425.16161 | February 2017 | February 28, 2018   | December 2027 |
| Platform update 3 |  7.0.4307.16141 | November 2016 | November 30, 2017    | December 2027 |
| Platform update 2 | 7.0.4230.16130  | August 2016   | August 31, 2017  | December 2027 |
| Platform update 1 | 7.0.4127.16103  | May 2016      | May 31, 2017     | December 2027 |

## Dates for Finance and Operations on-premises releases

The initial release of the on-premises software will be based on Platform update 8 and the July 2017 update of the applicaiton.

Microsoft commits to support the deployments of the Finance and Operations on-premises software through calendar year 2027 at a minimum, provided that the customer keeps the deployed software current according to the Modern Lifecycle Policy.


| Release                                                                        | Version               | Build number | Availability      | Expiration date                     |
|--------------------------------------------------------------------------------|-----------------------|--------------|-------------------|-------------------------------------|
|  Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) | July 2017 update            | 7.2.x        | June 2017         |  ? |
