---
# required metadata

title: Software lifecycle policy and cloud releases
description: This topic outlines the lifecycle and support policies for the Finance and Operations online service.
author: ShellyBakke
ms.date: 05/04/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysAbout
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 69914
ms.search.region: Global
# ms.search.industry: 
ms.author: smiller
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Software lifecycle policy and cloud releases

[!include [banner](../includes/banner.md)]

This topic outlines the lifecycle and support policies for the Finance and Operations online service.

## Modern Lifecycle Policy
The Finance and Operations online service is covered by the Modern Lifecycle Policy. The Modern Lifecycle Policy covers products and services that are serviced and supported continuously. For more information about this policy, see [Modern Lifecycle Policy](https://support.microsoft.com/help/30881). Licensed customers must stay current with updates to the Finance and Operations online service in accordance with the following servicing and system requirements:

- Customers purchasing subscriptions of Finance and Operations apps and operating on the following application versions will experience continuous updates of the platform and Financial Reporting. Microsoft will continually update these components. Customers have the option to postpone up to 3 consecutive service updates.
    - Finance and Operations apps, version 10.0+ (April 2019)
    - Finance and Operations apps, version 8.0 (April 2018)
    - Dynamics 365 for Finance and Operations, Enterprise edition 7.3 (December 2017)   
    - Dynamics 365 for Finance and Operations, Enterprise edition (June 2017)
    - Dynamics 365 for Operations version 1611 (November 2016)
    

- Platform versions maintain backward compatibility with the application versions that are supported at the time of the platform release within the application support lifecycle. For more information about platform versions, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

- Critical fixes and non-critical updates are handled in the following way:

    - **Critical fixes** – Critical fixes include security fixes and any fixes that are required to adhere to the availability service level agreement (SLA) that the service supports. Critical fixes will be made available in the latest platform update version and in the latest service update for customers operating on version 8.1. In addition, to help protect the customer and the online service, Microsoft might apply critical fixes directly to a customer's environment. If a critical fix must be applied, Microsoft will notify the customer about the required downtime window (if there will be any downtime) and apply the fix to the applicable environment. The critical fix will update the system to the latest update version.

    - **Non-critical updates** – Customers operating on the following application releases must update to the most current Finance and Operations platform and financial reporter version to deploy non-critical updates. 
    
      - Finance and Operations apps, version 10.0+ (April 2019)
      - Finance and Operations apps, version 8.0+ (April 2018)
      - Dynamics 365 for Finance and Operations, Enterprise edition 7.3 (December 2017)   
      - Dynamics 365 for Finance and Operations, Enterprise edition (June 2017)
      - Dynamics 365 for Operations version 1611 (November 2016)          

> [!NOTE]
> Application and platform releases expire at the end of the month of their software lifecycle.
>
> Microsoft will not provide any fixes to issues on versions that have reached end of service. Microsoft will also not investigate or troubleshoot any issue that you may encounter on an older version. If you encounter an issue on a version that has reached end of service, you will be required to update to the latest update and report the issue if it persists.
>
> All environments will continue to be operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, will also continue as is for supported versions.

## Dates and versions for application and platform releases

To see more details on dates and versions for application and platform releases, please visit the [What's new or changed in Finance and Operations apps home page](../../fin-ops/get-started/whats-new-changed).

> [!NOTE]
> -  Service updates are cumulative in nature and may include updates for some or all of the following components:  Platform, Application, Financial Reporting, Commerce, and operating system updates. 
> -  Customers can pause, delay, or opt out of a service update via the update settings in Microsoft Dynamics Lifecycle Services (LCS) projects, provided that all their sandbox and production environments are no more than three versions behind the latest available update. For more information, see [Can the updates be delayed? What is the policy?](../../fin-ops/get-started/one-version.md#can-the-updates-be-delayed-what-is-the-policy)
> -  All customers were required to be on the latest version of Finance and Operations by April 2019, except for those with unfulfilled [extension requests](../extensibility/extensibility-home-page.md) submitted to Microsoft. Customers who submitted extensibility requests by January 1, 2019, are supported on version 7.3 until their extensibility requests are fulfilled. Customers are expected to upgrade to the latest version within 90 days of the extensibility request being fulfilled. For more information, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md). 

## Downloadable virtual hard drive (VHD) releases

Use of the VHDs is subject to the [Software license terms](https://go.microsoft.com/fwlink/?linkid=851163).

| **Release**                                  | **VHD name**                 | **VHD expiration date** |
|----------------------------------------------|------------------------------|-------------------------|
| Platform update 12 / Application release 7.2 | FinandOps7.2PlatUpdate12.vhd | May 24, 2018            |
| Platform update 12 / Application release 7.3 | FinandOps7.3PlatUpdate12.vhd | June 05, 2018           |
| Platform update 15 / Application release 7.3 | FinandOps7.3withPlatUpdate15 | December 08, 2018       |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
