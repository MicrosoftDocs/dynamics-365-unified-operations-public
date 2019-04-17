---
# required metadata

title: Process auditing 
description: The process auditing feature allows you to track when candidates, job openings, or job applications change for reporting or compliance reasons.
author: tracykeya
manager: AnnBe
ms.date: 04/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
# ms.custom: 7521
ms.search.region: Global
# ms.search.industry: 
ms.author: trkeya
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.1.0, Talent April 2019 update 

---
# Using process auditing

The process auditing feature allows you to track when candidates, job openings, or job applications change for reporting or compliance reasons.

You can view the tracked data in PowerBI by using the [OData connector] (https://docs.microsoft.com/en-us/power-bi/desktop-connect-odata)

- From the [PowerApps] (https://web.powerapps.com ) site with the appropriate environment selected, select Settings and choose Advanced Customizations. Then select Developer resources. 
- In the Developer Resources page, look for the Instance Web API value and copy it. It should look something like https://yourorgname.api.crm.dynamics.com/api/data/v9.1/

You can then query the data from one of the following entities:
- Job opening history (msdyn_jobopeninghistories)
- Job application history (msdyn_jobapplicationhistories) 
- Candidate history (msdyn_candidatehistories)

## What is the data available?

### Changed by (msdyn_ChangedbyId) 
  Reference to user

### Created on (createdon)
  Date & time in UTC when the change happened

### Change type (msdyn_changetype)
 What change happened

#### Common values for candidates, job openings, and job applications
- Created
- Updated

#### Job application history 
- Artifact added 
- Artifact removed

#### Job opening history 
- TODO: post added 
- TODO: post removed 
- TODO: post updated 
- TODO: participant added 
- TODO: participant removed

#### Candidate history
-	Artifact added 
-	Artifact removed 
-	Work experience added 
-	Work experience removed 
-	Education added 
-	Education removed 
-	Skill added 
-	Skill removed 
-	Tag added 
-	Tag removed 
-	Social network added 
-	Social network removed 
-	Personal details added 
-	Personal details updated

### Changed fields (msdyn_changedfields)
JSON object listing changed fields, may not store values for all fields.
-	For "Created" and "Updated" changes, it will list the fields on the created or modified record 
-	For "Foo added" change types, it will list the fields on the child record

#### Example:
{ 
"msdyn_applyurl": { "newValue": "" }, 
"msdyn_description": { "valueOmitted": true } 
}

### Other fields

#### Job application history 
-	Job application (msdyn_JobapplicatonId)
-	Status (msdyn_status) 
-	Status reason (msdyn_statusreason) 
-	Rejection reason (msdyn_rejectionreason)

#### Job opening history 
-	Job opening (msdyn_JobopeningId) 
-	Status (msdyn_jobopeningstatus) 
-	Status reason (msdyn_jobopeningstatusreason)

#### Candidate history 
-	Candidate (msdyn_CandidateId)
