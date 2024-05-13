---
title: Virtual entities auto create and auto refresh
description: Learn about auto create and auto refresh of virtual entities for finance and operations to Dataverse
ms.author: mkannapiran
ms.topic: auto create and refresh
ms.date: 05/06/2024
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-05-31
---

# Virtual Entities Auto Create and Refresh


[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> Supported Release Information

**Auto Refresh :** Supported platform versions - PU62 (7.0.7120.170) or PU63 (7.0.7198.123) or PU64 (7.0.7279.31) or later 

**Auto Create :** Supported platform versions - PU63 (7.0.7198.123) or PU64 (7.0.7279.31) or later


## Overview

Changes made in Microsoft Dynamics 365 Finance and Operations on Data entity are visible to Dataverse through a manual refresh in Dataverse. The Auto Create and Refresh capability in Finance and Operations enables automatic metadata creation or modification in Dataverse immediately, reliably and efficiently. Automatic refresh of metadata ensures timely updates in Dataverse from Finance and Operations (F&O). Enabling Automatic Create and Refresh capability eliminates the need to manually refresh F&O entity into Dataverse. This capability paves way for automatically creating virtual tables in Dataverse for Microsoft Dynamics 365 Finance and Operations Data entities.

## Details
![Architecture of virtual entities for auto create and refresh.](media/AutoCreate_Refresh_Overview.png)

**Auto Refresh:**
* Virtual Table Auto Refresh feature is activated when the supported version of package is deployed. Supported platform versions are - PU62 (7.0.7120.170) or PU63 (7.0.7198.123) or PU64 (7.0.7279.31) or later.
* The package when deployed in Microsoft Dynamics 365 Finance and Operations will trigger an an X++ batch job (CDSVirtualEntityRefreshBatch). This batcj job is triggered thirty (30) minutes after successful deployment of feature package.

**Auto Create:**
* Auto create capability is activated when the supported version of the feature is deployed. Supported platform versions - PU63 (7.0.7198.123) or PU64 (7.0.7279.31) or later.
* In Microsoft Dynamics 365 Finance and Operations, the user has to set "Dataverse.AutoCreate" metadata property value to "Yes" to enable automatic creation of Virtual Table in the linked Dataverse environment.
* The automatic virtual table creation in Dataverse from F&O is managed through a batch job (CDSVirtualEntityAutoCreateBatch). This batch is triggered ninety (90) minutes after successful deployment of feature package.

** Failure ** arising due to automatic create or refresh has an automatic retry process. The automatic retry is currently fixed at 3 times and cannot be configured. 

## Monitoring

* The status of the auto create or auto refresh batch jobs can be monitored using the existing Batch Jobs form.
* Additionally, the status of Automatic Metadata Synchronizations can be checked using a newly created form.
* To view the results of automatic metadata synchronizations, navigate to the new Finance and Operations form named "Virtual entity metadata sync status"
* All automatically created and refreshed F&O entities will be displayed within this form.
  * In case of successful synchronization, the "Last refresh time" field will indicate the time of the successful synchronization.
  * In case of a failed synchronization:
    * Personalize the grid within this form by adding the "IsTransientFailure" field for enhanced visibility and troubleshooting.
    * The "Failure message" field will provide details about the error.
    * The "IsTransientFailure" field will indicate whether the failure is transient and if a retry will be attempted.
    * For entities marked as failed with Refresh Needed unchecked, manual refreshing from Dataverse is required after resolving the issue. Please note that this action must be taken by the user as the system does not automatically address these issues.  You can refer to [Web service error codes](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/reference/web-service-error-codes) for understanding any error codes in the failure message.
![Virtual entity metadata sync status form](media/VEMetadataSyncStatus.png)


## Notes
* **Refresh Batch Job History Limitation:** With each package deployment, the Refresh batch job is recreated, limiting the availability of refresh job history to the last package deployment only. This behavior persists in the current version. We are aware of this limitation and plan to address it in future releases.
* **Auto Delete Feature:** Please note that there is currently no Auto Delete feature implemented. If an Microsoft Dynamics 365 Finance and Operations Data Entity that is already enabled in the linked Dataverse environment is deleted, no action is taken automatically. Administrators are required to manually delete the Virtual Table in Dataverse.
