---
# required metadata

title: Track changes in recruiting data 
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
ms.author: anbichse
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.1.0, Talent April 2019 update 

---
# Track changes in recruiting data

[!include [banner](includes/banner.md)]

You can track changes made to candidates, job openings, or job applications by using audit processing. This is useful for reporting or compliance reasons.

You can view the tracked data in Power BI by using the OData connector. For more information, see [Connect to OData feeds in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-connect-odata).

## Track changes
To set up track changes in recruiting data, follow these steps:

1. In [Power Apps](https://web.powerapps.com), select the appropriate environment.

2. Select **Settings** (the gear icon), choose **Advanced customizations**, and then select **Resources** under **Developer resources**. 

3. On the **Developer Resources** page, copy the value in the **Instance Web API value** field. For example, the value could look like: https://yourorgname.api.crm.dynamics.com/api/data/v9.1/.

4. You can then query the data from one of the following entities:
  - Job opening history (msdyn_jobopeninghistories)
  - Job application history (msdyn_jobapplicationhistories) 
  - Candidate history (msdyn_candidatehistories)

## Data reported

The following data is available with process auditing.

| Data reported | Description |
| --- | --- |
| Changed by (msdyn_ChangedbyId) | Reference to user |
| Created on (createdon) |  Date and time in UTC when the change happened |
| Change type (msdyn_changetype) | What change happened |
| Common values for candidates, job openings, <br></br>and job applications | Created<br></br>Updated |
| Job application history | Artifact added <br></br>Artifact removed |
| Job opening history | TODO: post added <br></br>TODO: post removed <br></br>TODO: post updated <br></br>TODO: participant added <br></br>TODO: participant removed |
| Candidate history | Artifact added <br></br>Artifact removed <br></br>Work experience added <br></br>Work experience removed <br></br>Education added <br></br>Education removed <br></br>Skill added <br></br>Skill removed <br></br>Tag added <br></br>Tag removed <br></br>Social network added <br></br>Social network removed <br></br>Personal details added <br></br>Personal details updated<br></br> |
| Changed fields (msdyn_changedfields) | JSON object listing changed fields, might not store values for all fields.<br></br><br></br>For "Created" and "Updated" changes, it will list the fields on the created or modified record.<br></br><br></br>For "Added" change types, it will list the fields on the child record.<br></br><br></br>**Example:**<br></br><br></br>{<br></br>  "msdyn_applyurl": { "newValue": "" },<br></br>  "msdyn_description": { "valueOmitted": true } <br></br>} |
|Job application history | Job application (msdyn_JobapplicatonId)<br></br>Status (msdyn_status) <br></br>Status reason (msdyn_statusreason) <br></br>Rejection reason (msdyn_rejectionreason) |
| Job opening history | Job opening (msdyn_JobopeningId) <br></br>Status (msdyn_jobopeningstatus) <br></br>Status reason (msdyn_jobopeningstatusreason) |
| Candidate history | Candidate (msdyn_CandidateId) |
