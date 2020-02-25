---
# required metadata

title: Integrated worker, job, and position
description: 
author: ramasri
manager: AnnBe
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-01-08
ms.dyn365.ops.version: AX 7.0.0

---

# Integrated worker, job, and position

[!include [banner](../../includes/banner.md)]

[!include [preview banner](../../includes/preview-banner.md)]

Worker data can be mastered in more than one Dynamics 365 application. For example, Human Resource (HR) data can be managed in Dynamics 365 Human Resources, Dynamics 365 Commerce, and Dynamics 365 Supply Chain Management. Regardless of where the data originates, it is integrated behind the scenes. Integrated worker gives you the flexibility to master worker data in any Dynamics 365 application but provides a comprehensive view of the information in Dynamics 365 apps.

## Human Resources

HR data is well-defined in applications. Therefore, the integration of HR data just involves mapping the HR data between the two applications.

## Templates

Human Resource data includes information about employees and contractors, positions and jobs. A collection of entity maps work together during data interaction, as shown in the following table.

Finance and Operations apps | Model-driven app in Dynamics 365 | Description
-----------------------|--------------------------------|---
Compensation job function | cdm_jobfunctions |
Compensation job type | cdm_jobtypes |
Employment | cdm_employments |
Employment detail | cdm_employments |
Jobs | cdm_jobs |
Job detail | cdm_jobs |
Position details | cdm_jobpositions |
Position durations | cdm_jobpositions |
Position hierarchies | cdm_jobpositions |
Position type | cdm_positiontypes |
Position worker assignments | cdm_positionworkerassignmentmaps |
Worker | cdm_workers | Workers are classified in Finance and Supply Chain Management as employees or contractors. CDS can also classify workers as volunteers. Volunteers will become contractors when the data is transformed back into Finance and Supply Chain Management. |

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

