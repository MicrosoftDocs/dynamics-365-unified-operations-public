--- 
# required metadata 
 
title: Benefit eligibility process
description: This procedure shows how the benefit eligibility process works. 
author: twheeloc
ms.date: 08/19/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: SysPolicySourceDocumentRuleType, SysPolicyListPage, SysPolicy, HcmBenefitEligibilityPolicy, HcmBenefit, BenefitWorkspace, HcmBenefitSummaryPart   
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Version 7.0.0, Human Resources
---

# Benefit eligibility process

[!INCLUDE [banner](../includes/banner.md)]


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This procedure shows how the benefit eligibility process works. When the process is complete, you can view the results. The demo data company used to create this procedure is USMF.

1. Go to **Human resources** > **Benefits** > **Benefits**.
1. In the list, find and select the record you want.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. In the **Eligibility** field, select **Rule based**.
1. In the **Rule type** field, select the benefit policy rule to apply to the benefit.
1. On the Action Pane, select **Benefit**.
1. Select **Create eligibility event**.
1. In the drop-down dialog box, enter a value in the **Event** field.
1. In the **Description** field, enter a value.
1. In the **Event type** field, select **Open enrollment**.
1. Enter a date and time in the **Coverage start date** field.
1. Enter a date and time in the **Enrollment period start date** field.
1. Enter a number in the **Days to enroll** field.
1. Select **Create event**.
1. On the **Workers** FastTab, select **Add**.
1. In the **Show by type** field, select **Employees**.
1. In the **Show by legal entity** field, select **Current legal entity**.
1. Mark or unmark all rows in the list.
1. Select **OK**.
1. Select **Process**.
1. Select **OK**.
1. Refresh the page.
1. Select **Show results**.
1. Open the **Status** column filter.
1. Sort the column from A to Z.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
