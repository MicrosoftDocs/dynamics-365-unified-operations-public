--- 
# required metadata 
 
title: Workers without employment
description: Workers with no future, active, or historical employment with your organization appear on the Workers without employment page. 
author: twheeloc
ms.date: 06/11/2026
ms.topic: article

 
# optional metadata 
 
ms.search.form: HcmWorkerV2, HRMMassHireProject, HRMMassHireLine, HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-04-06
ms.dyn365.ops.version: Version 7.0.0 
---

# Workers without employment

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The **Workers without employment** page shows workers who don't have future, active, or historical employment with your organization. These workers can appear when you import workers who don't have an employment record, or when you delete a worker's employment through **Workers \> Employment history**.

By default, the following roles can access the **Workers without employment** page:

- Human Resources assistant
- Human Resources manager
- Recruiter
- Comp and Benefits manager
- Payroll administrator
- Payroll manager
- Training manager

In the **Workers without employment** list, you can delete the individuals listed. By default, the Human Resources assistant role has this privilege. To give this privilege to other roles, follow these steps:

1. Select **System administration**, and then select **Security configuration**.
1. In the **Privileges** tab, filter the **Privileges** list to **Maintain workers**.

   :::image type="content" source="./media/hr-personnel-workers-without-employment-filter.png" alt-text="Screenshot of the Privileges list filtered to Maintain workers." lightbox="./media/hr-personnel-workers-without-employment-filter.png":::

1. In the **References** column, select **Display menu items**.
1. In **Display menu items**, select **HcmWorkersWithoutEmployment**.
1. Set the **Delete** permission to **Grant**.
1. Select the **Unpublished objects** tab.

1. Select **Publish all**.

   :::image type="content" source="./media/hr-personnel-workers-without-employment-publish.png" alt-text="Screenshot of the Publish all option on the Unpublished objects tab." lightbox="./media/hr-personnel-workers-without-employment-publish.png":::

[!INCLUDE[footer-include](../includes/footer-banner.md)]
