---
# required metadata

title: Commerce Data Exchange troubleshooting
description: This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.
author: jashanno
manager: AnnBe
ms.date: 05/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Retail July 2017 update
---

# Commerce Data Exchange troubleshooting
This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment could become effectively useless.  As such, it is crucial to understand the process of troubleshooting any issue that arises in regards to data synchronization. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS (With or without an offline database) and other in-store components.  Reviewing this document should provide some general guidance on how to mitigate or fix some issues and highlight when it is best to create a support request and what data is most important to speed up a request for support.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the CDX implementation guide, the CDX best practices, and the Commerce architecture documents.

## Troubleshooting
Possible error messages to see
| Error | Description |
|----------------------------------|--------------------------------------------------------------------------------------|
| **System.ArgumentNullException: Value cannot be null.Parameter name: connectionString at Microsoft.Dynamics.Retail.CommerceDataExchange.SqlTargetRequestHandler** | An error has occurred (Error seen in a failed download job in **Download sessions**) due to batch job statuses. Navigate to **System administration > Inquiries > Batch jobs** and find the data writing batch associated to your Commerce Scale Unit that the download job would have been applied to and change the batch job's status to **Withhold**. On environments prior to 10.0.12, it is recommended to additionally create a new **Legacy** channel database group, associate the **Default** channel database to this new group, and then do not include this new database group in any distribution schedules (The **Default** (Legacy) channel database should no longer have CDX jobs being generated for it. |
| Unable to **Run now** from the **Distribution schedule** without running as **Batch processing** | This change was made intentionally in 10.0.11 due to accidental creation of performance issues by running jobs during the busiest environment usage times.  Another change that was made as a part of this feature enhancement was to disallow **Recurrence** when running a **Full data sync** (Full job sync) from the **Channel database** form in Headquarters (Only a single occurrence may be executed). It is not recommended to change this behavior, however, if in a development environment, it is possible to change this by navigating to **Commerce shared parameters > Configuration parameters** and setting a new Name **CDX_DISABLE_FORCESCHEDULEINBATCH** with Value **1**. |
| **Microsoft.Dynamics.Retail.CommerceDataExchange.SqlWriteRequestRunException: Failed to run SqlWriteRequestRunner for table AX.\<TABLE NAME>** | An error has occurred (Error seen in a failed download job in **Download sessions**) due to extending one or more **DBO** tables to a longer length and thus requiring truncation of data which causes a failure, which has caused a truncation failure. Please generate a Support Request . See [CDX extensibility](cdx-extensibility.md) for best practices, such as removing the EDT extension on the edited table field in question and using the CDX extension table to store the long (Full) value required.  |
| Download session is failing, stating **... tried too many times** | Navigate to **Retail and Commerce > Headquarters setup > Parameters > Commerce scheduler parameters** and set the **Try count** value to **3**.  Having this value too high could potentially cause a download session to fail during high usage times.  After performing this step, the job in question will next set itself to **Cancelled** and stop retrying.  It is recommended to review the [Commerce Data Exchange best practices](..\CDX-Best-Practices.md).  |
| Unable to cancel a running CDX job | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request.  |
| Use LCS (Lifecycle Services) to copy a Headquarters database between environments when that environment also uses Commerce Scale Unit (Cloud, formerly Retail Cloud Scale Unit) | Create a Support Request and specify whether it is acceptable to delete and reprovision the Commerce Scale Unit (Cloud) or if it is required to maintain the CSU (Commerce Scale Unit) as exists currently (Downtime will still be required). |


## Resources
[Commerce Architecture](../commerce-architecture.md)
[Select an in-store topology](retail-in-store-topology.md)
[CDX best practices](../implementation-considerations-CDX.md)
[Device management implementation guidance](../implementation-considerations-devices.md)
*Link to MPOS installer* LINK PENDING

*Link to CSU (Self-hosted) installer* LINK PENDING

