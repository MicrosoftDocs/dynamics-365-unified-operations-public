--- 
# required metadata 
 
title: Enter applicant and application data manually
description: This procedure shows how to manually maintain information about applicants and their application. 
author: andreabichsel
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: HcmApplicant, LogisticsContactInfoGrid, HRMApplication,  DirPartyTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: anbichse
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Enter applicant and application data manually

[!include [banner](../../includes/banner.md)]

This procedure shows how to manually maintain information about applicants and their application.   You can enter and maintain personal information, interview dates and times, references, competencies, and accommodation requests for applicants. You can also update the status of applicants' applications for employment and create letters or email messages to communicate with applicants. When you create an applicant record, a person record for that applicant is created in the global address book.       The demo data company used to create this procedure is USMF.


## Create a new applicant record
1. Go to Human resources > Recruitment > Applicants > Applicants.
2. Click New.
3. In the First name field, type a value.
4. In the Last name field, type a value.
    * You can enter additional applicant information if it's available. For example, information can include the applicant's highest degree, current job title, or previous employer.  
5. Toggle the expansion of the Contact information section.
6. Click Add.
7. In the Description field, type 'Communications email'.
8. In the Type field, select an option.
9. In the Contact number/address field, type a value.
    * This email address will be used to generate email communication with the applicant.  
10. Click Add.
11. In the Description field, type a value.
12. In the Contact number/address field, type a value.
    * Applicant personal information.  
    * You can enter additional personal information for the applicant, if needed. For example, this can include birth date, ethnic origin, gender, or marital status.  
13. On the Action Pane, click Competencies.
    * You can enter the applicant's competency profile, including their skills, professional experiences, education, tests, or certificates.  
    * This information can be used to map the applicant's skills to the skills associated with the jobs defined in your company's data.   

## Create an application for the applicant
1. Click Applications.
2. Click New.
3. In the Recruitment project field, click the drop-down button to open the lookup.
    * By selecting a recruitment project, the applicant will be associated with a specific opening included in that recruitment project.  
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
    * By default, the job and department are based on the selected recruitment project.  
6. Click Save.
    * After saving the application, you can attach documents to it, including the applicant's experience, awards, and cover letter.  

