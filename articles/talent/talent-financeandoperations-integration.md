---
# required metadata

title: Integration from Dynamics 365 for Talent to Dynamics 365 for Finance and Operations
description: This topic describes the integration between Talent and Finance and Operations. 
author: jcart
manager: AnnBe
ms.date: 10/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope:  
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2018-10-8
ms.dyn365.ops.version: 
---

# Integration from Dynamics 365 for Talent to Dynamics 365 for Finance and Operations

[!include[banner](../includes/banner.md)]

This topic describes the functionality available for integration from Dynamics 365 for Talent and Dynamics 365 for Finance and Operations. The Talent to Finance and Operations template that is available with the [Data Integrator](https://docs.microsoft.com/en-us/powerapps/administrator/data-integrator) enables the flow of data for jobs, positions, and workers. The data flows from Talent into Finance and Operations. The template doesn't provide the ability for data to flow back from Finance and Operations into Talent. 

![Talent to Finance and Operations Integration Flow](./media/TalentFinOpsFlow.png)

The Talent to Finance and Operations solution provides the following types of data synchronization. 

- Maintain jobs in Talent and sync them from Talent to Finance and Operations.
- Maintain positions and position assignments in Talent and sync them from Talent to Finance and Operations.
- Maintain employments in Talent and sync them from Talent to Finance and Operations.
- Maintain workers and worker addresses in Talent and sync them from Talent to Finance and Operations.

## System requirements for Talent
The integration solution requires the following versions of the Talent and Finance and Operations apps. 
- Dynamics 365 for Talent on CDS for Apps.
- Dynamics 365 for Finance and Operations 7.2 and forward.

## Template and tasks

To access the template, do the following.
1. Open [PowerApps Admin Center](https://admin.powerapps.com/). 
1. Select **Projects**, and then, in the upper-right corner, select **New project** to select public templates. A new project will need to be created for each legal entity you want to integrate into in Finance and Operations.

The following template and underlying tasks are used to synchronize records from talent to Finance and Operations.

- **Name of the template in Data integration:** Core HR (Talent CDS to Fin and Ops)

  > [!NOTE]
  > The name of the task contains the entities uses in each application. The source (Talent) is on the left and the destination
(Finance and Operations) is on the right.

**Tasks in the Data integration project:** 
- Job Functions to Compensation Job Function.
- Departments to Operating Unit.
- Departments to Operating Unit.
- Job Types to Compensation Job Type.
- Jobs to Jobs.
- Jobs to Job Detail.
- Position Types to Position Type.
- Job Positions to Positions.
- Job Positions to Positions Parent Job Assignment.
- Workers to Worker.
- Employments to Employment.
- Employments to Employment Detail.
- Position Worker Assignment to Position Worker Assignments.
- Worker Addresses to Worker Postal Address V2.

## Integration considerations
When integrating data from Talent to Finance and Operations, the integration will attempt to match records based on the ID. If the match
occurs, the data in Finance and Operations will be overwritten with the values in Talent. However, an issue may occur if logically
these are different records and the same ID was generated in either Talent or Finance and Operations based on the respective number sequence.

The areas where this can occur are Worker, which uses Personnel number to make the match, and Positions. Jobs do not use number sequences, as a result, if the same job ID is present in both Talent and Finance and Operations, the Talent information will overwrite the Finance and Operations information. 

To keep the ID issue from occurring, you can either add a prefix on the [number sequence](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/organization-administration/number-sequence-overview?toc=/dynamics365/unified-operations/talent/toc.json), or set a beginning number on the number sequence that is beyond the range of the other system. 

The location ID used for worker address isn't part of a number sequence. When integrating worker address from Talent to Finance and Operations, if the worker address already exists in Finance and Operations, a duplicate address record may be created. 

The following illustration shows an example of a template mapping in Data Integrator. 

![Template Mapping](./media/IntegrationMapping.png)




