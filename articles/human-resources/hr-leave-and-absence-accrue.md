---
# required metadata

title: Accrue leave and absence plans
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

# Accrue leave and absence plans

You can accrue leave and absence in Dynamics 365 Human Resources for multiple employees or for an individual.

## Accrue leave and absence for multiple employees

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Manage leave**, select **Accrue leave and absence plans**.

3. In the **Accrue leave and absence plans** dialog box, in **Accrue as of**, either select **Today's date** or select **Custom date** and enter a custom date.

4. If you want to run the accrual process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the accrual process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The accrual process will run with the parameters you set.

## Accrue leave and absence for an employee

1. On the employee's record, select **Leave**.

2. Select **Accrue leave and absence**.

3. In the **Accrue leave and absence plans** dialog box, in **Accrue as of**, either select **Today's date** or select **Custom date** and enter a custom date.

4. If you want to run the accrual process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the accrual process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The accrual process will run with the parameters you set.

## Preview features for Leave and absence

[!include [banner](includes/preview-feature-leave-absence.md)]

You can enable the following preview features for Leave and absence:

- **Delete leave and absence accruals**. Delete accrual records for a specific plan and date range. Accrual dates must be dated today or in the future.

- **Leave accrual audit**. Displays each time someone runs or deletes an accrual for one or all employees, along with the date and who performed the action.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)