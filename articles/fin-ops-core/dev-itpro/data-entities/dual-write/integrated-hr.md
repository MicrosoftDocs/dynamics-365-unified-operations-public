---
# required metadata

title: Integrated worker, job, and position
description: This topic provides information about integrated worker data in Microsoft Dynamics 365 apps.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramasri
ms.search.validFrom: 2020-01-08
ms.dyn365.ops.version: AX 7.0.0

---

# Integrated worker, job, and position

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]



While mastered in only one app, worker data can be synchronized across multiple Dynamics 365 apps. For example, human resources (HR) data can be mastered in Dynamics 365 Human Resources and synchronized with Dynamics 365 Commerce, Dynamics 365 Finance, and Dynamics 365 Supply Chain Management. The data is integrated seamlessly behind the scenes. The ability to integrate data about workers ensures you're working with the same data across all Dynamics 365 apps, providing you a comprehensive view of your information.

## Human resources

The integration of HR data involves just mapping the HR data between Finance and Operations apps and model-driven apps in Dynamics 365.

## Templates

HR data includes information about employees and contractors, positions, and jobs. A collection of table maps works together during data interaction, as shown in the following table.

| Finance and Operations apps | Model-driven apps in Dynamics 365 | Description |
|-----------------------------|----------------------------------|-------------|
| Compensation job function | cdm\_jobfunctions | |
| Compensation job type | cdm\_jobtypes | |
| Employment | cdm\_employments | |
| Employment detail | cdm\_employments | |
| Jobs | cdm\_jobs | |
| Job detail | cdm\_jobs | |
| Position details | cdm\_jobpositions | |
| Position durations | cdm\_jobpositions | |
| Position hierarchies | cdm\_jobpositions | |
| Position type | cdm\_positiontypes | |
| Position worker assignments | cdm\_positionworkerassignmentmaps | |
| Worker | cdm\_workers | In Dynamics 365 Finance and Supply Chain Management data, workers are classified as either employees or contractors. Dataverse can also classify workers as volunteers. Volunteers will become contractors when the data is transformed back into Finance and Supply Chain Management. |

[!include [symbols](../../includes/dual-write-symbols.md)]

[!include [job function](includes/JobFunction-cdm-jobfunctions.md)]

[!include [job type](includes/JobType-cdm-jobtypes.md)]

[!include [employment](includes/Employment-cdm-employments.md)]

[!include [employment detail](includes/EmploymentDetail-cdm-employments.md)]

[!include [job](includes/Job-cdm-jobs.md)]

[!include [job detail](includes/JobDetail-cdm-jobs.md)]

[!include [position detail](includes/PositionDetail-cdm-jobpositions.md)]

[!include [position duration](includes/PositionDuration-cdm-jobpositions.md)]

[!include [position hierarchy](includes/PositionHierarchy-cdm-jobpositions.md)]

[!include [position type](includes/PositionType-cdm-positiontypes.md)]

[!include [position worker assignment](includes/PositionWorkerAssignment-cdm-positionworkerassignmentmaps.md)]

[!include [worker](includes/Worker-cdm-workers.md)]


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
