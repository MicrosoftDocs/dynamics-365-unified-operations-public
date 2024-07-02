---
# required metadata

title: Configure deductions
description: Use deductions in Microsoft Dynamics 365 Human Resources to determine how much, if any, to deduct from an employee’s paycheck for each benefit.
author: twheeloc
ms.date: 7/02/2024
ms.topic: article
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure deductions


Use deductions in Microsoft Dynamics 365 Human Resources to determine how much, if any, to deduct from an employee’s paycheck for each benefit. Deductions are date-effective, so you can keep a historical record of deduction information. 

1. In the **Benefits management** workspace, under **Setup**, select **Deductions**.
2. Select **New**.
3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Deduction** | A unique ID that is used to identify the benefit deduction. |
   | **Description** | A description for the deduction. |
   | **Effective** | The start date. The default value is the current system date. |
   | **Expiration** | The end date. The default value is 12/31/2154, which signifies never. |
   | **Heading** | The heading code from the payroll system that this deduction will use for the employee portion of the deduction when processing the benefits to payroll. This is used when you use a third-party payroll provider. |
   | **Employee payroll deduction reference** | The deduction code from the payroll system that this deduction will use for the employee portion of the deduction when processing the benefits to payroll. |
   | **Amount heading** | The heading code from the payroll system that this deduction amount will use for the employee portion of the deduction when processing the benefits to payroll. This is normally used when you use a third-party payroll provider. |
   | **Can delete** | Specifies whether an exported value from Dynamics 365 Finance can cause the value to be deleted in the payroll system. |
   | **Paired columns** | Specifies whether to export heading and deduction amount in paired adjacent columns to the payroll system. |
   | **Change effective date** | The date when the benefit deduction change will become effective. On this date, the benefit deduction changes and all benefit plans associated with this deduction are updated, as long as you run **Deduction change update** processing. |
   | **Deduction change completed** | The **Deduction change completed** check box will be automatically selected once the benefit deduction changes have been completed by Deduction update change processing. |
   
4. To track and maintain changes to the benefit rate setup, select **Actions**, and then select **Maintain versions**.

5. Select **Save**. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]

