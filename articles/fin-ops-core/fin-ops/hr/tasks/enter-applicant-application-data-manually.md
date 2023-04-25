--- 
# required metadata 
 
title: Enter applicant and application data manually
description: This procedure shows how to manually maintain information about applicants and their application. 
author: twheeloc
ms.date: 01/10/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HcmApplicant, LogisticsContactInfoGrid, HRMApplication,  DirPartyTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Enter applicant and application data manually

> [!NOTE]
> The recruiting functionality in this article will be referred to as Recruitment projects and focuses on applicants, applications, and recruitment projects.  


This procedure shows how to manually maintain information about applicants and their application. You can enter and maintain personal information, interview dates and times, references, competencies, and accommodation requests for applicants. You can also update the status of applicants' applications for employment, and create letters or email messages to communicate with applicants. When you create an applicant record, a person record for that applicant is created in the global address book. The **USMF** demo data company was used to create this procedure.

## Create a new applicant record

1. Go to **Human resources \> Recruitment \> Applicants \> Applicants**.
2. Select **New**.
3. In the **First name** field, enter a value.
4. In the **Last name** field, enter a value.

    You can enter additional applicant information if it's available. For example, this information can include the applicant's highest degree, current job title, or previous employer.

5. Expand the **Contact information** section.
6. Select **Add**.
7. In the **Description** field, enter **Communications email**.
8. In the **Type** field, select an option.
9. In the **Contact number/address** field, enter a value.

    This email address will be used to generate email communication with the applicant.

10. Select **Add**.
11. In the **Description** field, enter a value.
12. In the **Contact number/address** field, enter a value.

    Use this field to enter additional personal information about the applicant, as required. For example, this information can include the applicant's birth date, ethnic origin, gender, or marital status.

13. On the Action Pane, select **Competencies**.

    You can enter the applicant's competency profile, including their skills, professional experiences, education, tests, or certificates. This information can be used to map the applicant's skills to the skills that are associated with the jobs that are defined in your company's data.

## Create an application for the applicant

1. Select **Applications**.
2. Select **New**.
3. In the **Recruitment project** field, select the drop-down arrow to open the lookup.

    By selecting a recruitment project, you ensure that the applicant will be associated with a specific opening that is included in that recruitment project.

4. In the list, find and select the desired record.
5. In the list, select the link in the selected row.

    By default, the job and department are based on the selected recruitment project.

6. Select **Save**.

    After you save the application, you can attach documents to it. These documents might include the applicant's experience, awards, and cover letter.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
