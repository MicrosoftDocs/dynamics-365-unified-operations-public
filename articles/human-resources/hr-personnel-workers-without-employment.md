--- 
# required metadata 
 
title: Workers without employment
description: Workers with no future, active, or historical employment with your organization appear on the Workers without employment page. 
author: twheeloc
ms.date: 11/03/2021
ms.topic: 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HcmWorkerV2, HRMMassHireProject, HRMMassHireLine, HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  
ms.search.scope: Human Resources
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-04-06
ms.dyn365.ops.version: Version 7.0.0 
---

# Workers without employment


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Workers who have no future, active, or historical employment with your organization appear on the **Workers without employment** page. Workers of this type can appear when you import workers who don't have an employment record, or when you delete a worker's employment via **Workers \> Employment history**.

By default, the **Workers without employment** page is available to the following roles:

- Human Resources Assistant
- Human Resources Manager
- Recruiter
- Comp and Benefits Manager
- Payroll Administrator
- Payroll Manager
- Training Manager

In the **Workers without employment** list, you can delete the individuals listed. By default, this privilege is given to the Human Resources Assistant role. You can give this privilege to other roles with the following steps:

1. Select **System administration**, and then select **Security configuration**.

2. In the **Privileges** tab, filter the **Privileges** list to **Maintain workers**.

   [![Filter Privileges list.](./media/hr-personnel-workers-without-employment-filter.png)](./media/hr-personnel-workers-without-employment-filter.png)

3. In the **References** column, select **Display menu items**.

4. In **Display menu items**, select **HcmWorkersWithoutEmployment**.

   [![Select form.](./media/hr-personnel-workers-without-employment-select.png)](./media/hr-personnel-workers-without-employment-select.png)

5. Set the **Delete** permission to **Grant**.

6. Select the **Unpublished objects** tab.

7. Select **Publish all**.

   [![Publish changes.](./media/hr-personnel-workers-without-employment-publish.png)](./media/hr-personnel-workers-without-employment-publish.png)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
