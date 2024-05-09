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

Today, any changes in F&O Data entity are not visible to Dataverse until there is a manual refresh from Dataverse. This feature aims to automatically refresh all virtual entity metadata reliably and efficiently, ensuring timely updates in the Dataverse. This would remove the requirement of manually refreshing the entity from Dataverse.
This also paves way for automatically creating virtual entities in Dataverse for F&O Data entities.

## Details
![Architecture of virtual entities for auto create and refresh.](media/AutoCreate_Refresh_Overview.png)

**Auto Refresh:**
* This feature activates upon package deployment.
* If modifications to an existing Dataverse F&O Virtual Entity are included in the deployed package, an X++ batch job (CDSVirtualEntityRefreshBatch) is triggered. This job executes approximately thirty minutes after the package deployment.

**Auto Create:**
* This feature is activated after Auto Refresh package deployment.
* Any designated F&O Data Entity with Dataverse.AutoCreate metadata property set to Yes will automatically be enabled as a Virtual Entity in the linked Dataverse environment.
* The enabling process is managed by another batch job (CDSVirtualEntityAutoCreateBatch), which runs approximately ninety minutes following the package deployment.

Each failed entity refresh will be automatically retried up to 3 times. This retry limit is fixed and cannot be configured.

## Monitoring

* The status of the new batch jobs can be monitored using the existing Batch Jobs form.
* Additionally, the status of Automatic Metadata Synchronizations can be checked using a newly created form.
* To view the results of automatic metadata synchronizations, navigate to the new Finance and Operations form named "Virtual entity metadata sync status"
* All automatically created and refreshed entities will be displayed within this form.
  * In case of successful synchronization, the "Last refresh time" field will indicate the time of the successful synchronization.
  * In case of a failed synchronization:
    * Personalize the grid within this form by adding the "IsTransientFailure" field for enhanced visibility and troubleshooting.
    * The "Failure message" field will provide details about the error.
    * The "IsTransientFailure" field will indicate whether the failure is transient and if a retry will be attempted.
    * For the failed entities with Refresh Needed = unchecked, manual refresh would be needed from Dataverse after fixing the issue.
![Virtual entity metadata sync status form](media/VEMetadataSyncStatus.png)


## Notes
* **Refresh Batch Job History Limitation:** With each package deployment, the Refresh batch job is recreated, limiting the availability of refresh job history to the last package deployment only. This behavior persists in the current version. We are aware of this limitation and plan to address it in future releases.
* **Auto Delete Feature:** Please note that there is currently no Auto Delete feature implemented. If an F&O Data Entity that is already enabled in the linked Dataverse environment is deleted, no action is taken automatically. Administrators are required to manually delete the Virtual Table in Dataverse.
