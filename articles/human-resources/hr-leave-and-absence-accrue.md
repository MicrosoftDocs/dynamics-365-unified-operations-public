---
# required metadata

title: Accrue leave and absence plans
description: You can accrue leave and absence in Dynamics 365 Human Resources for multiple employees or for an individual.
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
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

3. The **Accrue leave and absence plans** dialog box appears. In **Accrue as of**, either select **Today's date** or select **Custom date** and enter a custom date.

4. If you want to run the accrual process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the accrual process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The accrual process will run with the parameters you set.

## Accrue leave and absence for an employee

1. On the employee's record, select **Leave**.

2. Select **Accrue leave and absence**.

3. The **Accrue leave and absence plans** dialog box appears. In **Accrue as of**, either select **Today's date** or select **Custom date** and enter a custom date.

4. If you want to run the accrual process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the accrual process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The accrual process will run with the parameters you set.

## Delete leave and absence accruals for multiple employees

Delete accrual records for a specific plan and date range. Accrual dates must be dated today or in the future.

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Manage leave**, select **Delete leave and absence plan accruals**.

3. In the **Delete leave and absence plan accruals** dialog box, select the **Leave plan**. 

4. If applicable, choose **Delete balance adjustments**.

5. Enter or select a **Leave accrual date**. This date has to be either today or in the future. 

6. Select **OK**. The accrual process will delete accruals with the parameters you set. 

## Delete leave and absence accruals for a single employee

1. On the employee's record, select **Leave**.

2. Select **Delete leave and absence plan accruals**.

3. In the **Delete leave and absence plan accruals** dialog box, select **Leave plan**. 

4. If applicable, choose **Delete balance adjustments**.

5. Enter or select a **Leave accrual date**. This date must be either today or in the future. 

6. Select **OK**. The accrual process will delete accruals with the parameters you set. 

## Review leave accrual and deletion processes

**Leave accrual audit** displays each time you run or delete an accrual for one or all employees. The date and person who performed the action also displays.

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Manage leave**, select **Delete leave accrual audit**.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)
