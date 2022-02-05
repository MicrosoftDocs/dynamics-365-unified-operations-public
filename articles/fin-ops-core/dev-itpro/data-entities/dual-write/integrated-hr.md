---
title: Integrated worker, job, and position
description: This topic provides information about integrated worker data in Microsoft Dynamics 365 apps.
author: RamaKrishnamoorthy
ms.date: 01/08/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2020-01-08
ms.dyn365.ops.version: AX 7.0.0
---

# Integrated worker, job, and position

[!include [banner](../../includes/banner.md)]



While mastered in only one app, worker data can be synchronized across multiple Dynamics 365 apps. For example, human resources (HR) data can be mastered in Dynamics 365 Human Resources and synchronized with Dynamics 365 Commerce, Dynamics 365 Finance, and Dynamics 365 Supply Chain Management. The data is integrated seamlessly behind the scenes. The ability to integrate data about workers ensures you're working with the same data across all Dynamics 365 apps, providing you a comprehensive view of your information.

## Human resources

The integration of HR data involves just mapping the HR data between finance and operations apps and customer engagement apps.

## Templates

HR data includes information about employees and contractors, positions, and jobs. A collection of table maps works together during data interaction, as shown in the following table.

Finance and operations apps | Customer engagement apps     | Description
|-----------------------------|----------------------------------|-------------|
[Compensation job function](mapping-reference.md#105) | cdm_jobfunctions | |
[Compensation job type](mapping-reference.md#108) | cdm_jobtypes | |
[Employment job functions](mapping-reference.md#225) | msdyn_employmentjobfunctions | |
[Employment per company](mapping-reference.md#104) | cdm_employments | |
[Jobs](mapping-reference.md#107) | cdm_jobs | |
[Positions V2](mapping-reference.md#106) | cdm_jobpositions | |
[Position type](mapping-reference.md#110) | cdm_positiontypes | |
[Position worker assignments](mapping-reference.md#111) | cdm_positionworkerassignmentmaps | |
[Worker](mapping-reference.md#113) | cdm_workers | In Dynamics 365 Finance and Supply Chain Management data, workers are classified as either employees or contractors. Dataverse can also classify workers as volunteers. Volunteers will become contractors when the data is transformed back into Finance and Supply Chain Management. |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
