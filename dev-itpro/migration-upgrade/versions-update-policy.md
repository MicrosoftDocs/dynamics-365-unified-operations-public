---
# required metadata

title: Service and software lifecycle policy
description: This topic outlines the lifecycle and support policies for the Dynamics 365 for Finance and Operations, Enterprise edition online service and on-premises software deployments.
author: ryanCcarlson 
manager: AnnBe
ms.date: 05/31/2017
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

# Service and software lifecycle policy

[!include[banner](../includes/banner.md)]


This topic outlines the lifecycle and support policies for the Dynamics 365 for Finance and Operations, Enterprise edition online service and on-premises software deployments.

## Modern Lifecyle Policy
The [Modern Lifecycle Policy](https://support.microsoft.com/en-us/help/30881/modern-lifecycle-policy) covers products and services that are serviced and supported continuously. Under this policy, the product or service remains in support if the following criteria are met:

1.	Customers must stay current as per the servicing and system requirements published for the product or service.
2.	Customers must be licensed to use the product or service.
3.	Microsoft must currently offer support for the product or service.

The Microsoft Dynamics 365 for Finance and Operations, Enterprise edition cloud service and the Dynamics 365 for Finance and Operations, Enterprise edition on-premises software is covered by the Modern Lifecycle Policy. Licensed customer must stay current with updates based on the following support policies:

- Application versions are supported for three years from date of release.
- Cloud and on-premises platform versions are supported for one year from date of release for critical fixes. Non-critical updates requires customers to move to the most current certified Dynamics 365 for Finance and Operations, Enterprise edition platform version. Platform versions maintain backward compatibility.

**Note:** The most current certified platform may not be the most current release of the platform.

The customer is in control of installing updates in their environments. Microsoft commits to support the deployments of Dynamics 365 for Finance and Operations, Enterprise edition on-premises software, through calendar year 2027 at a minimum, provided that the customer keeps the deployed software current according to the Modern Lifecycle Policy. 

## Cloud service update policies

- Dynamics 365 for Finance and Operations, Enterprise edition cloud platform updates may be initiated by Microsoft or the customer. After the customer tests the updates and provides consent, the updates will be rolled out to production environments. Microsoft may update production environments with critical updates related to security and reliability without customer testing and consent.
- Dynamics 365 for Finance and Operations, Enterprise edition application updates will be initiated by the customer.

Application and cloud platform updates will be scheduled with the customer. Before updates are applied to production they must be tested in a sandbox environment. For details about how the sandbox environment will be provided, see the [licensing guide](http://aka.ms/s201h6).

**Important:** To help protect our customers and the service, Microsoft may apply critical updates directly to your Dynamics 365 for Finance and Operations, Enterprise edition environments. If a critical update needs to be applied, Microsoft will notify the customer of the required downtime window (if any) and apply the update to their environments. After updates are applied, Microsoft will communicate the completion of the customer.

## On-premises software update policies
The customer is in full control of the on-premises deployments and must follow the Modern Lifecycle Policy for production environments.

The Dynamics 365 for Finance and Operations, Enterprise edition on-premises model only offers licenses under the Modern Lifecycle Policy. This requires the customer to maintain Software Assurance or the Enhancement Plan and deploy updates as noted in the matrix below. Customers who wish to use the Fixed Support Lifecycle Policy (5+5), must downgrade to AX 2012.  If a customer lapses on Software Assurance or the Enhancement Plan, they are eligible for the perpetual rights only of AX 2012 and must uninstall Dynamics 365 for Finance and Operations, Enterprise edition.

## Application and platform releases

### Application releases

| Release | Version | Build number | Availability | Expiration date |
|---------|----------|--------------|--------------|-----------------|
|Microsoft Dynamics 365 for Finance and Operations, Enterprise edition | July 2017 update | X | June 2016 |  |
| Microsoft Dynamics 365 for Operations          | 1611              |  7.1.1541.3036   | November 2016    | November 30, 2019 |
| Microsoft Dynamics AX               | 7.0.1             | 7.0.1265.23014   | May 2016         | June 30, 2017 | 
| Microsoft Dynamics AX               | 7.0               | 7.0.1265.3015    | February 2016    | June 30, 2017 |

### Platform releases

| Release | Version | Build number | Availability | Expiration date |
|---------|----------|--------------|--------------|-----------------|
| Microsoft Dynamics 365 for Operations  | Platform update 7 |  7.0.4542.16189  | May 2017    | May 31, 2018 |
| Microsoft Dynamics 365 for Operations  | Platform update 6 |  7.0.4509.16180  | April 2017    | April 30, 2018 |
| Microsoft Dynamics 365 for Operations  | Platform update 5 |  7.0.4475.16165  | March 2017    | March 31, 2018 |  
| Microsoft Dynamics 365 for Operations  | Platform update 4 |  7.0.4425.16161  | February 2017    |February 28, 2018 | 
| Microsoft Dynamics 365 for Operations  | Platform update 3 |  7.0.4307.16141  | November 2016    | November 30, 2017 |
| Microsoft Dynamics AX                  | Platform update 2 | 7.0.4230.16130   | August 2016      | August 31, 2017 |
| Microsoft Dynamics AX                  | Platform update 1 | 7.0.4127.16103   | May 2016         |  May 31, 2017 |
| Microsoft Dynamics AX                  | 7.0               | 7.0.4030.16079   | February 2016    | January 31, 2017 | 

## On-premises releases
The initial release of the on-premises software will be based on Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update with platform update 8. Microsoft commits to support the deployments of the Dynamics 365 for Finance and Operations, Enterprise edition on-premises software through calendar year 2027 at a minimum, provided that the customer keeps the deployed software current according to the Modern Lifecycle Policy.

| Release | Version | Build number | Availability | Expiration date |
|---------|----------|--------------|--------------|-----------------|
|Microsoft Dynamics 365 for Finance and Operations, Enterprise edition | July 2017 update | X | June 2016 |  |

## Support matrix
The following table lists the recent releases of the application and platform for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and shows which versions are compatible.



|                       | Dynamics AX 7.0 | Dynamics AX application 7.0.1 | Dynamics 365 for Operations (1611) | Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update |
|-----------------------|--------------------------------|---------------------------------------------|--------------------------------------------------|------|
| **Platform update 8** | Compatible                      | Compatible                                   | Compatible                                        |  Compatible |
| **Platform update 7** | Compatible                      | Compatible                                   | Compatible                                        |   |
| **Platform update 6** | Compatible                      | Compatible                                   | Compatible                                        |   |
| **Platform update 5** | Compatible                      | Compatible                                   | Compatible                                        |   |
| **Platform update 4** | Compatible                      | Compatible                                   | Compatible                                        |   |
| **Platform update 3** | Compatible                      | Compatible                                   | Compatible                                        |   |
| **Platform update 2** | Compatible                      | Compatible                                   |                                                  |   |
| **Platform update 1** | Compatible                      | Compatible                                   |                                                  |   |
| **Platform 7.0**      | Compatible                      |                                             |                                                  |   |

