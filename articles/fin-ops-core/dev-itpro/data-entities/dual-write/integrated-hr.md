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

[!include [](includes/JobFunction-cdm-jobfunctions.md)]

[!include [](includes/JobType-cdm-jobtypes.md)]

[!include [](includes/Employment-cdm-employments.md)]

[!include [](includes/EmploymentDetail-cdm-employments.md)]

[!include [](includes/Job-cdm-jobs.md)]

[!include [](includes/JobDetail-cdm-jobs.md)]

[!include [](includes/PositionDetail-cdm-jobpositions.md)]

[!include [](includes/PositionDuration-cdm-jobpositions.md)]

[!include [](includes/PositionHierarchy-cdm-jobpositions.md)]

[!include [](includes/PositionType-cdm-positiontypes.md)]

[!include [](includes/PositionWorkerAssignment-cdm-positionworkerassignmentmaps.md)]

[!include [](includes/Worker-cdm-workers.md)]

### Workers to CDS Workers
This template synchronizes data between Finance / Supply Chain Management apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
PERSONNELNUMBER | = | cdm_workernumber
FIRSTNAME | = | cdm_firstname
MIDDLENAME | = | cdm_middlename
LASTNAME | = | cdm_lastname
WORKERTYPE | >> | cdm_type
WORKERSTATUS | >> | cdm_status
PRIMARYCONTACTEMAIL | = | cdm_primaryemailaddress
PRIMARYCONTACTPHONE | = | cdm_primarytelephone
PRIMARYCONTACTFACEBOOK | = | cdm_facebookidentity
PRIMARYCONTACTTWITTER | = | cdm_twitteridentity
PRIMARYCONTACTLINKEDIN | = | cdm_linkedinidentity
PRIMARYCONTACTURL | = | cdm_websiteurl
GENDER | >< | cdm_gender
BIRTHDATE | = | cdm_birthdate
NAME | >> | cdm_fullname

### Employment to CDS Employment
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
PERSONNELNUMBER | = | cdm_workerid.cdm_workernumber
LEGALENTITYID | = | cdm_companyid.cdm_companycode
WORKERTYPE | >> | cdm_workertype
EMPLOYMENTSTARTDATE | = | cdm_employmentstartdate
EMPLOYMENTENDDATE | = | cdm_employmentenddate

### Employment details to CDS Employment
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
PERSONNELNUMBER | = | cdm_workerid.cdm_workernumber
LEGALENTITYID | = | cdm_companyid.cdm_companycode
ADJUSTEDWORKERSTARTDATE | = | cdm_adjustedworkerstartdate
EMPLOYERNOTICEAMOUNT | = | cdm_employernoticeamount
EMPLOYERUNITOFNOTICE | = | cdm_employerunitofnotice
EMPLOYMENTENDDATE | = | cdm_employmentenddate
EMPLOYMENTSTARTDATE | = | cdm_employmentstartdate
LASTDATEWORKED | = | cdm_lastdateworked
TRANSITIONDATE | = | cdm_transitiondate
EMPLOYMENTTYPE | = | cdm_workertype
VALIDFROM | = | cdm_validfrom
VALIDTO | = | cdm_validto
WORKERNOTICEAMOUNT | = | cdm_workernoticeamount
WORKERUNITOFNOTICE | = | cdm_workerunitofnotice

### Position types to CDS Position Type
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
POSITIONTYPEID | = | cdm_name
DESCRIPTION | = | cdm_description
CLASSIFICATION | >< | cdm_classification

### Position to CDS Job Position
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
POSITIONID | = | cdm_jobpositionnumber

### Position details to CDS Job Position
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
POSITIONID | = | cdm_jobpositionnumber
JOBID | = | cdm_jobid.cdm_name
DESCRIPTION | = | cdm_description
DEPARTMENTNUMBER | = | cdm_departmentid.cdm_departmentnumber
AVAILABLEFORASSIGNMENT | = | cdm_availableforassignment
VALIDFROM | = | cdm_validfrom
VALIDTO | = | cdm_validto
FULLTIMEEQUIVALENT | = | cdm_fulltimeequivalent
POSITIONTYPEID | = | cdm_positiontypeid.cdm_name

### Position duration to CDS Job Position
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
POSITIONID | = | cdm_jobpositionnumber
VALIDFROM | = | cdm_activation
VALIDTO | = | cdm_retirement

### Position Hierarchy to CDS Job Position
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
POSITIONID | = | cdm_jobpositionnumber
PARENTPOSITIONID | = | cdm_parentjobpositionid.cdm_jobpositionnumber
HIERARCHYTYPENAME | << | none
VALIDFROM | << | cdm_validfrom
VALIDTO | << | cdm_validto

### Position worker assignments to CDS Position Worker Assignment
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
PERSONNELNUMBER | = | cdm_workerid.cdm_workernumber
POSITIONID | = | cdm_jobpositionid.cdm_jobpositionnumber
VALIDFROM | = | cdm_validfrom
VALIDTO | = | cdm_validto

### Jobs to CDS Jobs
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
JOBID | = | cdm_name
MAXIMUMNUMBEROFPOSITIONS | = | cdm_maximumnumberofpositions
ALLOWUNLIMITEDPOSITIONS | >< | cdm_allowunlimitedpositions
DESCRIPTION | = | cdm_description
JOBDESCRIPTION | = | cdm_jobdescription
JOBTYPEID | = | cdm_jobtypeid.cdm_name
FUNCTIONID | = | cdm_jobfunctionid.cdm_name
EFFECTIVE | = | cdm_validfrom
EXPIRATION | = | cdm_validto
FULLTIMEEQUIVALENT | = | cdm_defaultfulltimeequivalent

### Job detail to CDS Jobs
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
JOBID | = | cdm_name
JOBTYPEID | = | cdm_jobtypeid.cdm_name
FUNCTIONID | = | cdm_jobfunctionid.cdm_name
VALIDFROM | = | cdm_validfrom
VALIDTO | = | cdm_validto
FULLTIMEEQUIVALENT | = | cdm_defaultfulltimeequivalent

### Compensation job function to CDS Job Function
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
JOBFUNCTIONID | = | cdm_name
DESCRIPTION | = | cdm_description

### Compensation job type to CDS Job type
This template synchronizes data between Finance and Operations apps and Common Data Service.

Source field | Map type | Destination field
---|---|---
JOBTYPEID | = | cdm_name
DESCRIPTION | = | cdm_description
EXEMPTSTATUS | >< | cdm_exemptstatus

[!include [symbols](../../includes/dual-write-symbols.md)]








