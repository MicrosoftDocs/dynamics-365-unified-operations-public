--- 
title: Enter applicant and application data manually
description: Learn about how to manually maintain information about applicants and their application, including outlines on creating new applicant records. 
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/26/2026
ms.custom:  
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.search.form: HcmApplicant, LogisticsContactInfoGrid, HRMApplication,  DirPartyTable   
ms.dyn365.ops.version: Version 7.0.0 
---
# Enter applicant and application data manually

> [!NOTE]
> This article refers to the recruiting functionality as Recruitment projects. It focuses on applicants, applications, and recruitment projects.  

This procedure shows how to manually maintain information about applicants and their applications. You can enter and maintain personal information, interview dates and times, references, competencies, and accommodation requests for applicants. You can also update the status of applicants' applications for employment, and create letters or email messages to communicate with applicants. When you create an applicant record, you also create a person record for that applicant in the global address book. This procedure uses the **USMF** demo data company.

## Create a new applicant record

1. Go to **Human resources > Recruitment > Applicants > Applicants**.
1. Select **New**.
1. In the **First name** field, enter a value.
1. In the **Last name** field, enter a value.

    Enter additional applicant information if it's available. For example, this information can include the applicant's highest degree, current job title, or previous employer.

1. Expand the **Contact information** section.
1. Select **Add**.
1. In the **Description** field, enter **Communications email**.
1. In the **Type** field, select an option.
1. In the **Contact number/address** field, enter a value.

    Use this email address to generate email communication with the applicant.

1. Select **Add**.
1. In the **Description** field, enter a value.
1. In the **Contact number/address** field, enter a value.

    Use this field to enter additional personal information about the applicant, as required. For example, this information can include the applicant's birth date, ethnic origin, gender, or marital status.

1. On the Action Pane, select **Competencies**.

    Enter the applicant's competency profile, including their skills, professional experiences, education, tests, or certificates. Use this information to map the applicant's skills to the skills that are associated with the jobs that are defined in your company's data.

## Create an application for the applicant

1. Select **Applications**.
1. Select **New**.
1. In the **Recruitment project** field, select the drop-down arrow to open the lookup.

    When you select a recruitment project, you ensure that the applicant is associated with a specific opening that is included in that recruitment project.

1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.

    By default, the job and department are based on the selected recruitment project.

1. Select **Save**.

    After you save the application, you can attach documents to it. These documents might include the applicant's experience, awards, and cover letter.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
