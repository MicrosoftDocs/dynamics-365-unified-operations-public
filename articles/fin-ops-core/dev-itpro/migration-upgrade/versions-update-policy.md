---
# required metadata

title: Software lifecycle policy and cloud releases
description: This topic outlines the lifecycle and support policies for the Finance and Operations online service.
author: ShellyBakke
ms.date: 02/26/2020
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

- Customers purchasing subscriptions of Finance and Operations and operating on the following application versions will experience continuous updates of the Platform and Financial Reporting. Microsoft will continually update these components with the option to postpone up to 3 consecutive service updates.
    - Dynamics 365 for Operations version 1611 (November 2016)
    - Dynamics 365 for Finance and Operations, Enterprise edition (July 2017)
    - Dynamics 365 for Finance and Operations, Enterprise edition 7.3
    - Dynamics 365 for Finance and Operations, version 8.0 (April 2018)

- Platform versions maintain backward compatibility with the application versions that are supported at the time of the platform release within the application support lifecycle. For more information about platform versions, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

- Critical fixes and non-critical updates are handled in the following way:

    - **Critical fixes** – Critical fixes include security fixes and any fixes that are required to adhere to the availability service level agreement (SLA) that the service supports. Critical fixes will be made available in the latest platform update version and in the latest service update for customers operating on version 8.1. In addition, to help protect the customer and the online service, Microsoft might apply critical fixes directly to a customer's environment. If a critical fix must be applied, Microsoft will notify the customer about the required downtime window (if there will be any downtime) and apply the fix to the applicable environment. The critical fix will update the system to the latest update version.

    - **Non-critical updates** – Customers operating on the following application releases must update to the most current Finance and Operations platform and financial reporter version to deploy non-critical updates. 
    
       - Dynamics 365 for Operations version 1611 (November 2016)
       - Dynamics 365 for Finance and Operations, Enterprise edition (July 2017)
       - Dynamics 365 for Finance and Operations, Enterprise edition 7.3
       - Dynamics 365 for Finance and Operations, version 8.0 (April 2018)
     
      Customers operating on release 8.1 must update to the most current service update to deploy non-critical updates.

> [!NOTE]
> Application and platform releases expire at the end of the month of their software lifecycle.
>
> Microsoft will not provide any fixes to issues on versions that have reached end of service. Microsoft will also not investigate or troubleshoot any issue that you may encounter on an older version. If you encounter an issue on a version that has reached end of service, you will be required to update to the latest update and report the issue if it persists.
>
> All environments will continue to be operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, will also continue as is for supported versions.

## Dates and versions for application and platform releases

### Table 1: Continuous update releases

For information about the new features included in each release, click the links in the **Version** column.

| **Release**                             | **Major release or service update** | **Version**                                                                                                                       | **Build number** | **Availability** | **End of service**           |
|-----------------------------------------|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|------------------|------------------|------------------------------|
| Dynamics 365 for Finance and Operations | Major release                       | [10.0](../../fin-ops/get-started/whats-new-changed-10.md) | 10.0.8          | April 2019     | Not applicable (continuously updated)\* |
| Dynamics 365 for Finance and Operations | Major release                       | [8.1](../../fin-ops/get-started/whats-new-changed-8-1-october-2018.md) | 8.1.136          | October 2018     | Not applicable (continuously updated)\* |

\* Indicates a major release is required to be updated through service updates. Service updates are cumulative in nature and may include updates for some or all of the following components:  Platform, Application, Financial Reporting, Retail, and operating system updates.  You will be required to have an update that's no older than 3 service updates. The 8.1.x version series will be replaced by version 10.0, which is targeted for release in April 2019. For more information, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

### Table 2: Application releases

For information about the new features included in each release, select the links in the **Version** column.

| **Release**                                                 | **Major or minor release** | **Version**                                                                                                                                           | **Build number** | **Availability** | **End of Service** |
|-------------------------------------------------------------|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|------------------|--------------------|
| Dynamics 365 for Finance and Operations                     | Major release              | [8.0](../../fin-ops/get-started/whats-new-changed-8-0-april-2018.md)                       | 8.0.30           | April 2018       | April 30 2019         |
| Dynamics 365 for Finance and Operations, Enterprise edition | Major release              | [7.3](../../fin-ops/get-started/whats-new-application-7.3-update.md)                       | 7.3.11971.56116  | December 2017    | April 30 2019\*       |
| Dynamics 365 for Finance and Operations, Enterprise edition | Major release              | [July 2017](../../fin-ops/get-started/whats-new-application-july-2017-update.md)           | 7.2.11792.56024  | June 2017        | April 30 2019         |
| Dynamics 365 for Operations                                 | Major release              | [1611](../../fin-ops/get-started/whats-new-dynamics-365-operations-1611.md)                | 7.1.1541.3036    | November 2016    | April 30 2019         |
| Dynamics AX                                                 | Minor release              | [7.0.1](../../fin-ops/get-started/whats-new-changed-application-version-7-0-1-may-2016.md) | 7.0.1265.23014   | May 2016         | June 2017          |
| Dynamics AX                                                 | Major release              | [7.0](../../fin-ops/get-started/whats-new-changed-7-0-february-2016.md)                    | 7.0.1265.3015    | February 2016    | June 2017          |


\* All customers must be on the latest version of Finance and Operations by April 2019. However, we are making an exception for customers who have unfulfilled [extension requests](../extensibility/extensibility-home-page.md) that have been submitted to Microsoft. Those customers who submitted extensibility requests by January 1, 2019, will be supported on version 7.3 until their extensibility requests are fulfilled. Customers are expected to upgrade to the latest version within 90 days of the extensibility request being fulfilled. For more information, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

### Table 3: Platform releases

For information about the new features included in each release, select the links in the **Release** column.

| **Release**                                                                                                                                                  | **Build number** | **Availability** | **Expiration date**        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|------------------|----------------------------|
| [Platform update 31](../get-started/whats-new-platform-update-31.md)               | 7.0.5457        | January 2020   | N/A (Continuously updated) |
| [Platform update 30](../../fin-ops/get-started/whats-new-platform-update-30.md)               | 7.0.5407        | November 2019   | N/A (Continuously updated) |
| [Platform update 29](../../fin-ops/get-started/whats-new-platform-update-29.md)               | 7.0.5372        | October 2019   | N/A (Continuously updated) |
| [Platform update 28](../../fin-ops/get-started/whats-new-platform-update-28.md)               | 7.0.5314        | July 2019   | N/A (Continuously updated) |
| [Platform update 27](../../fin-ops/get-started/whats-new-platform-update-27.md)               | 7.0.5286        | June 2019   | N/A (Continuously updated) |
| [Platform update 26](../../fin-ops/get-started/whats-new-platform-update-26.md)               | 7.0.5257        | May 2019   | N/A (Continuously updated) |
| [Platform update 25](../../fin-ops/get-started/whats-new-platform-25.md)               | 7.0.5222        | April 2019   | N/A (Continuously updated) |
| [Platform update 24](../../fin-ops/get-started/whats-new-platform-update-24.md)               | 7.0.5179          | March 2019   | N/A (Continuously updated) |
| [Platform update 23](../../fin-ops/get-started/whats-new-platform-update-23.md)               | 7.0.5126          | January 2019   | N/A (Continuously updated) |
| [Platform update 22](../../fin-ops/get-started/whats-new-platform-update-22.md)               | 7.0.5095         | December 2018   | N/A (Continuously updated / Retired) |
| [Platform update 21](../../fin-ops/get-started/whats-new-platform-update-21.md)               | 7.0.5073         | October 2018   | N/A (Continuously updated / Retired) |
| [Platform update 20\*\*](../../fin-ops/get-started/whats-new-platform-update-20.md)               | 7.0.5030         | October 2018   | N/A (Continuously updated / Retired) |
| [Platform update 15\*](../../fin-ops/get-started/whats-new-platform-update-15.md)                 | 7.0.4841         | March 2018       | N/A (Continuously updated / Retired) |
| [Platform update 12](../../fin-ops/get-started/whats-new-platform-update-12.md)                   | 7.0.4709         | November 2017    | November 2018              |
| [Platform update 11](../../fin-ops/get-started/whats-new-platform-update-11.md)                   | 7.0.4679.35176   | October 2017     | October 2018               |
| [Platform update 10](../../fin-ops/get-started/whats-new-platform-update-10.md)                   | 7.0.4641.16233   | August 2017      | August 2018                |
| [Platform update 9](../../fin-ops/get-started/whats-new-platform-update-9.md)                     | 7.0.4612.35162   | July 2017        | July 2018                  |
| [Platform update 8](../../fin-ops/get-started/whats-new-platform-update-8.md)                     | 7.0.4565.16212   | June 2017        | June 2018                  |
| [Platform update 7](../../fin-ops/get-started/whats-new-platform-update-7.md)                     | 7.0.4542.16189   | May 2017         | May 2018                   |
| [Platform update 6](../../fin-ops/get-started/whats-new-platform-update-6.md)                     | 7.0.4509.16180   | April 2017       | April 2018                 |
| [Platform update 5](../../fin-ops/get-started/whats-new-platform-update-5.md)                     | 7.0.4475.16165   | March 2017       | March 2018                 |
| [Platform update 4](../../fin-ops/get-started/whats-new-platform-update-4.md)                     | 7.0.4425.16161   | February 2017    | February 2018              |
| [Platform update 3](../../fin-ops/get-started/whats-new-platform-update-3.md)                     | 7.0.4307.16141   | November 2016    | November 2017              |
| [Platform update 2](../../fin-ops/get-started/whats-new-platform-update-2.md)                     | 7.0.4230.16130   | August 2016      | August 2017                |
| [Platform update 1](../../fin-ops/get-started/whats-new-changed-platform-version-7-1-may-2016.md) | 7.0.4127.16103   | May 2016         | May 2017                   |
| [Platform 7.0](../../fin-ops/get-started/whats-new-changed-7-0-february-2016.md)                  | 7.0.4030.16079   | February 2016    | January 2017               |

\*\* Platform updates 16, 17, 18, and 19 have not been made generally available.

\* Platform updates 13 and 14 have not been made generally available.

### Table 4: Application updates

The application updates listed below consist of a small subset of application enhancements released on top of Finance and Operations versions 8.0, 7.3, and 7.2 (July 2017). These updates do not affect the support lifecycle of the release--support is in-line with the policies for each release.

Note that application updates are not cumulative. The individual packages only contain the enhancements that were included in that specific release. However, if there is a dependency between two packages, then both packages will be included.

For information about the new features included in each update, click the links in the **Version** column.

| **Release**                                                 | **Version**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | **Build number** | **Availability** |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|------------------|
| Dynamics 365 for Finance and Operations                     | 8.1.3: [KB 4470000 Microsoft Dynamics 365 for Finance and Operations version 8.1.3 with Platform update 23\*](https://go.microsoft.com/fwlink/?linkid=2049362)                                      | 8.1.227     | January 2019      |
| Dynamics 365 for Finance and Operations                     | 8.1.2: [KB 4470000 Microsoft Dynamics 365 for Finance and Operations version 8.1.2 with Platform update 22\*](https://go.microsoft.com/fwlink/?linkid=2049368)                                      | 8.1.195     | December 2018      |
| Dynamics 365 for Finance and Operations                     | 8.1.1: [KB 4470000 Microsoft Dynamics 365 for Finance and Operations version 8.1.1 with Platform update 21\*](https://go.microsoft.com/fwlink/?linkid=2038101)                                      | 8.1.170     | October 2018      |
| Dynamics 365 for Finance and Operations                     | 8.0.4: [KB 4458992 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.4 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4458992&bugId=239612&qc=70318005e232acfe98df16bf3ab4cdf8df463634e28ff3ce2ef1db29c8678863), [KB 4458993 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.4 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4458993&bugId=239610&qc=70318005e232acfe98df16bf3ab4cdf8df463634e28ff3ce2ef1db29c8678863)                                      | 8.0.35.15532     | August 2018      |
| Dynamics 365 for Finance and Operations                     | 8.0.3: [KB 4346176 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.3 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4346176&bugId=230723&qc=15b7470493e66efed8446f7ad2269bde9804da7174d135900c99b7318bb26e34), [KB 4346172 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.3 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4346172&bugId=230724&qc=15b7470493e66efed8446f7ad2269bde9804da7174d135900c99b7318bb26e34)                                      | 8.0.35.15342     | July 2018        |
| Dynamics 365 for Finance and Operations                     | 8.0.2: [KB 4340414 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.2 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4340414&bugId=219341&qc=0d87f4d28eb75753e9c4ceeb997ab6bf2a0ff5d0b58342ecd9512cc721e0cc80), [KB 4340413 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.2 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4340413&bugId=219344&qc=0d95ca5957e7b1288e6d56bcf3bc6c014baf9e916d976fd100ae24db3d2b1a14)                                      | 8.0.35.15211     | July 2018        |
| Dynamics 365 for Finance and Operations                     | 8.0.1: [KB 4295107 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.1 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4295107&bugId=192587&qc=70f6f8fbdd96b01197fedc9442b5c43c2e01e2748eb0d5a20d87bceb4c0b939d), [KB 4294515 Microsoft Dynamics 365 for Finance and Operations - Version 8.0.1 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4294515&bugId=194698&qc=70f6f8fbdd96b01197fedc9442b5c43c2e01e2748eb0d5a20d87bceb4c0b939d)                                      | 8.0.30.15107     | June 2018        |
| Dynamics 365 for Finance and Operations, Enterprise edition | 7.3.2: [KB 4093261 Microsoft Dynamics 365 for Finance and Operations - Version 7.3.2 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4093261&bugId=3937217&qc=848a3e7a82137b3ac4412537f1fdb4fafacab7d7565e0a7a6930b0c96406c96a), [KB 4093262 Microsoft Dynamics 365 for Finance and Operations - Version 7.3.2 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?kb=4093262&bugId=3937219&qc=848a3e7a82137b3ac4412537f1fdb4fafacab7d7565e0a7a6930b0c96406c96a)                                    | 7.3.11971.62687  | March 2018       |
| Dynamics 365 for Finance and Operations, Enterprise edition | 7.3.1: [KB 4093139 Microsoft Dynamics 365 for Finance and Operations - Version 7.3.1 (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Details?bugId=3933782&qc=419638525c20d4bcd818cd40be05a12876e4c00a39124d2e44a0d950af21be89), [KB 4091727 Microsoft Dynamics 365 for Finance and Operations - Version 7.3.1 (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Details?bugId=3933783&qc=419638525c20d4bcd818cd40be05a12876e4c00a39124d2e44a0d950af21be89)                                                          | 7.3.11971.62430  | March 2018       |
| Dynamics 365 for Finance and Operations, Enterprise edition | Application update 5: [KB 4053277 Application Update 5 for Microsoft Dynamics 365 for Finance and Operations (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4053277&bugId=3893141&qc=ee9db96dd13dc341e7019fad3d36d01c6dfc4edf631f752f66d87f2ebbd256f5), [KB 4053278 Application Update 5 for Microsoft Dynamics 365 for Finance and Operations (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4053278&bugId=3893143&qc=ee9db96dd13dc341e7019fad3d36d01c6dfc4edf631f752f66d87f2ebbd256f5) | 7.2.11792.62725  | November 2017    |
| Dynamics 365 for Finance and Operations, Enterprise edition | Application update 4: [KB 4047325 Application Update 4 for Dynamics 365 for Finance and Operations (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4047325&bugId=3866272&qc=dfcd40f8c5d0d863cc6ae10fe7dd3fb57450327d4f82f10c57886d579e6d4838), [KB 4047321 Application Update 4 for Dynamics 365 for Finance and Operations (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4047321&bugId=3866273&qc=dfcd40f8c5d0d863cc6ae10fe7dd3fb57450327d4f82f10c57886d579e6d4838)                     | 7.2.11792.62509  | October 2017     |
| Dynamics 365 for Finance and Operations, Enterprise edition | Application update 3: [KB 4043284 Application Update 3 for Dynamics 365 for Finance and Operations (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4043284&bugId=3857197&qc=e6921e68e9b9037bf91c26b3b553e479890731b4b4dd5e6dcb45b0ca13895d8d), [KB 4043285 Application Update 3 for Dynamics 365 for Finance and Operations (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4043285&bugId=3857199&qc=54ee2e988aace65d26834ced54cc11326f5d5e435520ccaf951d41bd1276f672)                     | 7.2.11792.62370  | September 2017   |
| Dynamics 365 for Finance and Operations, Enterprise edition | Application update 2: [KB 4039142 Application Update 2 for Dynamics 365 for Finance and Operations (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4039142&bugId=3850590&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df), [KB 4039487 Application Update 2 for Dynamics 365 for Finance and Operations (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4039487&bugId=3850591&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df)                     | 7.2.11792.62192  | September 2017   |
| Dynamics 365 for Finance and Operations, Enterprise edition | Application update 1: [KB 4035749 Application Update 1 for Dynamics 365 for Finance and Operations (Binary part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4035749&bugId=3845890&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df), [KB 4035751 Application Update 1 for Dynamics 365 for Finance and Operations (X++ part)\*](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4035751&bugId=3845891&qc=5339dbbd18aacbc8bdcbe4123d749d28803653d6c68f787bd8fc3337e97693df)                     | 7.2.11792.62089  | July 2017        |


\* The link points to a Knowledge Base (KB) article. You must sign in to Lifecycle Services (LCS) to view the KB article.

## Support matrix

Platform updates are compatible with all application versions that are supported at the time of release.

### Table 5: Downloadable virtual hard drive (VHD) releases

Use of the VHDs is subject to the [Software license terms](https://go.microsoft.com/fwlink/?linkid=851163).

| **Release**                                  | **VHD name**                 | **VHD expiration date** |
|----------------------------------------------|------------------------------|-------------------------|
| Platform update 12 / Application release 7.2 | FinandOps7.2PlatUpdate12.vhd | May 24, 2018            |
| Platform update 12 / Application release 7.3 | FinandOps7.3PlatUpdate12.vhd | June 05, 2018           |
| Platform update 15 / Application release 7.3 | FinandOps7.3withPlatUpdate15 | December 08, 2018       |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
