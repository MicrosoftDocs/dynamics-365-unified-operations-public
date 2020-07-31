---
# required metadata

title: Commerce Data Exchange troubleshooting
description: This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.
author: jashanno
manager: AnnBe
ms.date: 08/01/2020
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
ms.search.validFrom: 2020-08-31
ms.dyn365.ops.version: Retail July 2017 update
---

# Commerce Data Exchange troubleshooting
[!include[banner](../includes/banner.md)]

This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment could become effectively useless.  As such, it is crucial to understand the process of troubleshooting any issue that arises in regards to data synchronization. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS (With or without an offline database) and other in-store components.  Reviewing this document should provide some general guidance on how to mitigate or fix some issues and highlight when it is best to create a support request and what data is most important to speed up a request for support.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the CDX implementation guide, the CDX best practices, and the Commerce architecture documents.

## Troubleshooting
If a error is not seen below, please create a Support Request as necessary to resolve the issue with Microsoft Support.  This article focuses on issues that are either directly able to be worked on without Microsoft Support or issues that can be directly seen but not solved without Microsoft Support.  

| Error | Description |
|-------------------------|--------------------------------------------------------------------------------------|
| **System.ArgumentNullException: Value cannot be null.Parameter name: connectionString at Microsoft.Dynamics.Retail.CommerceDataExchange.SqlTargetRequestHandler** | An error has occurred (Error seen in a failed download job in **Download sessions**) due to batch job statuses. Navigate to **System administration > Inquiries > Batch jobs** and find the data writing batch associated to your Commerce Scale Unit that the download job would have been applied to and change the batch job's status to **Withhold**. On environments prior to 10.0.12, it is recommended to additionally create a new **Legacy** channel database group, associate the **Default** channel database to this new group, and then do not include this new database group in any distribution schedules (The **Default** (Legacy) channel database should no longer have CDX jobs being generated for it. |
| Unable to **Run now** from the **Distribution schedule** without running as **Batch processing** | This change was made intentionally in 10.0.11 due to accidental creation of performance issues by running jobs during the busiest environment usage times.  Another change that was made as a part of this feature enhancement was to disallow **Recurrence** when running a **Full data sync** (Full job sync) from the **Channel database** form in Headquarters (Only a single occurrence may be executed). It is not recommended to change this behavior, however, if in a development environment, it is possible to change this by navigating to **Commerce shared parameters > Configuration parameters** and setting a new Name **CDX_DISABLE_FORCESCHEDULEINBATCH** with Value **1**. |
| **Microsoft.Dynamics.Retail.CommerceDataExchange.SqlWriteRequestRunException: Failed to run SqlWriteRequestRunner for table AX.\<TABLE NAME>** | An error has occurred (Error seen in a failed download job in **Download sessions**) due to extending one or more **DBO** tables to a longer length and thus requiring truncation of data which causes a failure, which has caused a truncation failure. Please generate a Support Request . See [Enable custom Commerce Data Exchange synchronization via extension](cdx-extensibility.md) for best practices, such as removing the EDT extension on the edited table field in question and using the CDX extension table to store the long (Full) value required.  |
| Download session is failing, stating **... tried too many times** | Navigate to **Retail and Commerce > Headquarters setup > Parameters > Commerce scheduler parameters** and set the **Try count** value to **3**.  Having this value too high could potentially cause a download session to fail during high usage times.  After performing this step, the job in question will next set itself to **Cancelled** and stop retrying.  It is recommended to review the [Commerce Data Exchange best practices](CDX-Best-Practices.md).  |
| Unable to cancel a running CDX job | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request.  |
| Use LCS (Lifecycle Services) to copy a Headquarters database between environments when that environment also uses Commerce Scale Unit (Cloud, formerly Retail Cloud Scale Unit) | Create a Support Request and specify whether it is acceptable to delete and reprovision the Commerce Scale Unit (Cloud) or if it is required to maintain the CSU (Commerce Scale Unit) as exists currently (Downtime will still be required). |
| CDX or environment issues after altering the **Days transactions exist** field in the **Functionality profile** | When this value is reduced by a large amount, it is possible to lock one or more tables while the purging occurs. It is recommended if this value is going to be highly reduced to generate a Support Request before changing the value.  Support will be able to remove the data prior to altering the value, minimizing database impact when the value is changed. |
| Download sessions are taking exceptional time or there is overall Headquarters slowness (After adding a number of POS terminals) | A new Modern POS offline database (Added to the relevant Channel database group) inherits all existing download sessions since the last full database sync occurred. The potentially exceptional data generation could be overly large and performance impacting at the best possible times and crippling to the environment performance at the worst (Busiest) times. It is highly recommended to either have a dummy Channel database group (Which is not associated to any distribution schedule job) to assign to the newly generated terminals or a special **Offline profile** where the configuration **Pause offline synchronization** is set to value **Yes**.  This will allow data generation to occur when required and when the system is most available to do so (Potentially pausing multiple times, as required).  If it is too late at this point, create a Support Request. |
| Normal, incremental (Delta) sync is taking far too long despite small number of rows effected | This can potentially occur when a new channel (Store) is created due to the necessity to create all the data once again for this new store. It is highly recommended to have a dummy Channel database (Which is associated to a dummy Channel database group) to assign to the newly generated channel (Store).  This will allow data generation to occur when required and when the system is most available to do so (By changing the ).  If it is too late at this point, please create a Support Request. |
| The **P-job** fails to create an upload session with error, **System.Data.SqlClient.SqlException (0x80131904): Violation of PRIMARY KEY constraint 'PK_UPLOADSESSION'. Cannot insert duplicate key in object 'crt.UPLOADSESSION'.** | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request. |
| When attempting to download an upload session package from the **Upload sessions** form in Headquarters, the error **Record for Id - \<Number> not found**  | Create a Support Request. |
| CDX download sessions failing to be applied with error message: **Failed to get download session package URI.** | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request. |
| No **Download sessions** are applied and no **Upload sessions** are being created | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request. |
| Upload sessions fail with an error where the upload session package contains multiple records in the **RetailListingStatusLog** table, which has the same **StatusDateTime** value: **Infolog for task Default:P-0001 (...) Error when bulk inserting data. Target table: RetailListingStatusLog** | If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request. |
| Cashier attempts to switch to offline or is forced offline and the switch fails | There are many possible causes. First, verify basic information. Does the computer have available hard drive space? If using SQL Express, is the offline database at the 10GB size limit? Are there pending download sessions for this register (Proving the register is no longer up to date, potentially (temporarily) disallowing offline switching)?  Beyond these questions, it is recommended to contact Support. If this occurs in a production environment, login to Lifecycle Services (LCS) and create a request for immediate support.  If in a non-production environment, create a Support Request. |

## Resources
| Links |
|---------------------------------------------------|
| [Best practices](CDX-Best-Practices.md) |
| [CDX best practices](implementation-considerations-cdx.md) |
| [Commerce Architecture](../commerce-architecture.md) |
| [Select an in-store topology](retail-in-store-topology.md) |
| [Device management implementation guidance](../implementation-considerations-devices.md) |
| [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md) |
| [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md) |
