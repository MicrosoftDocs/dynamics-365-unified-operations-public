---
# required metadata

title: Configure deductions
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure deductions

[!include [banner](includes/preview-feature.md)]

Use deductions in Microsoft Dynamics 365 Human Resources to determine how much, if any, to deduct from an employee’s paycheck for each benefit. Deductions are date effective, so you can keep a historical record of deduction information. 

1. In the **Benefits management** workspace, under **Setup**, select **Deductions**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Deduction | A unique ID that is used to identify the benefit deduction. |
   | Description | A description for the deduction. |
   | Effective | The start date. The default value is the current system date. |
   | Expiration | The end date. The default value is 12/31/2154, which signifies never. |
   | Heading | The heading code from the payroll system that this deduction will use for the employee portion of the deduction when processing the benefits to payroll. This is used when you use a third party payroll provider. |
   | Employee payroll deduction reference | The deduction code from the payroll system that this deduction will use for the employee portion of the deduction when processing the benefits to payroll. |
   | Amount heading | The heading code from the payroll system that this deduction amount will use for the employee portion of the deduction when processing the benefits to payroll. This is normally used when you use a third party payroll provider. |
   | Can delete | Specifies whether an exported value from Dynamics 365 for Finance and Operations can cause the value to be deleted in the payroll system. |
   | Paired columns | Specifies whether to export heading and deduction amount in paired adjacent columns to the payroll system. |
   | Change effective date | The date when the benefit deduction change will become effective. On this date the system will automatically change the benefit deduction and update all benefit plans associated with this deduction, as long as you run Deduction change update processing. |
   | Deduction change completed | The Deduction change completed check box will be automatically selected once the benefit deduction changes have been completed by Deduction update change processing. |
   
4. To track and maintain changes to the benefit rate setup, select **Actions**, and then select **Maintain versions**.

5. Select **Save**. 
