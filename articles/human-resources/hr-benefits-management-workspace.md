---
# required metadata

title: Benefits management workspace
description: This topic describes the Benefits management workspace in Dynamics 365 Human Resources.
author: andreabichsel
ms.date: 02/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-24
ms.dyn365.ops.version: Human Resources

---

# Benefits management workspace

[!include [applies to](../includes/applies-to-hr.md)]

[!include [preview feature](./includes/preview-feature.md)]

This topic describes the **Benefits management** workspace in Dynamics 365 Human Resources.

> [!NOTE]
> To view the **Benefits management** workspace, you must first enable the **(Preview) Benefits management workspace** feature in Feature management. For more information about enabling preview features, see [Manage features](hr-admin-manage-features.md).<br><br>![Enable Benefits management workspace.](./media/hr-benefits-management-workspace-enable.png)

The **Benefits management** workspace gives you a quick view of benefits items that require your attention. On this page, you can see:

- Totals for items awaiting action
- Workers with unconfirmed selections
- Workers who recently enrolled in benefits
- Workers with future life events
- New hires who aren't enrolled
- Workers with active life events
- Workers with open enrollments who haven't opted for any plans

![Benefits management workspace.](./media/hr-benefits-management-workspace.png)

## View action items

You can view your action items by either selecting a tile or a tab. If you select a tab, you can view and select workers right on the workspace page.

![Action items.](./media/hr-benefits-management-workspace-action-items.png)

If you select a tile, you go to the page for that area. For example, selecting any of these tiles displays the **Worker benefits plans** page, filtered for employees you need to take action on:

- **Unconfirmed selections**
- **Open enrollments with no checked out plans**
- **Enrolled in benefits**
- **New hire not enrolled**

![Worker benefit plans.](./media/hr-benefits-management-workspace-plans.png)

Selecting the **Active life events** or **Future life events** tiles takes you to a list of active or future life events.

![Life events.](./media/hr-benefits-management-workspace-life-events.png)

## Processing

To process enrollment eligibility, life events, or rate change updates, select the appropriate item on the navigation bar.

![Processing.](./media/hr-benefits-management-workspace-processing.png)

To view process results, select **Process results** on the page.

![Process results.](./media/hr-benefits-management-workspace-process-results.png)

For more information about benefits processing, see:

- [Process enrollment eligibility](hr-benefits-process-enrollment-eligibility.md)
- [Process life event changes](hr-benefits-process-life-event-changes.md)
- [Process life event eligibility](hr-benefits-process-life-event-eligibility.md)
- [Process life events](hr-benefits-process-life-events.md)
- [Process rate changes](hr-benefits-process-rate-changes.md)

## Change period

To view a different benefits period, select it from the **Period** dropdown.

![Change period.](./media/hr-benefits-management-workspace-period.png)


## Open enrollment tab

You can view your action items by either selecting a tile or a tab. If you select a tab, you can view and select workers right on the workspace page.
The open enrollment tab provides key metrics for the open enrollment process. 

By default, information regarding open enrollment will be displayed 30 days before the **Enrollment start date** as defined in **Period Setup** in **Benefits management-links-Periods-Enrollment start **.  To change this setting, navigate to**Human Resource Shared parameters- Benefits management – Open enrollment options – Number of **.  

The following information is available in the open enrollment tab
 - Employees that have not started the open enrollment process
 - Employees that have elections in process
 - Employees that have completed the election process
 - Unconfirmed selections

**Summary Section**

**Not started tile** – The not started tile gives a count of employees that have not started the enrollment process.  The query is showing employees that do not have any plans selected, waived or checked out for the open enrollment plan period.  Mandatory plans are ignored and not included because they are selected by default for the employee.  Drilling into this tile will display the **Worker benefits plan** form with a list of employees that have not started the open enrollment process

> [!NOTE]
> If you do not want to track the open enrollment progress for a **Plan type**, you can exclude it by navigating to **Benefits management-Links-Employee self service parameters-Benefit plans tile setup-Track open enrollment progress**.  For example, you may plans created where **Plan type** = ‘Other’.  These plans might be optional plans that you don’t want to track enrollment progress for. If you uncheck this plan type, plans of these types will be ignored when tracking enrollment progress or completion in the open enrollment tab.  This setting applies to selected plan type for all periods and legal entities.

**Elections in progress tile** – The elections in progress tiles gives a count of employees that have elections in progress.  The query is showing employees that have plans that have at least one plan that is waived or selected.  Mandatory plans are ignored and not included because they are selected by default for the employee.  Drilling into this tile will display the **Worker Benefit Plans Bulk Update form**, with only selected and waived plans being displayed.

**Enrolled in benefits tile** – The enrolled in benefits tile gives a a count of employees that are fully enrolled in benefits.   The underlying query is showing employees where all plans have either been selected or waived.  The query will exclude plans that are not being tracked for open enrollment in the Employee self service parameters form.  Drilling into this tile will display the **Worker benefit plans** form with a list of employees based on the above query.

**Unconfirmed selections tile**– The unconfirmed selections tiles gives a count of employees that have plans that are selected or waived and need to be confirmed.  Drilling into this tile will display the **Worker Benefit Plans Bulk Update** form.


**Activity tab**

**Not started tab** - The not started tab gives a list of employees that have not started the enrollment process.  The query is showing employees that do not have any plans selected, waived or checked out for the open enrollment plan period.  Mandatory plans are ignored and not included because they are selected by default for the employee.  Drilling into the worker will display the **Worker benefit plans detail** form.

**Elections in progress tab**- The elections in progress tab gives a list of employees that have elections in progress.  The query is showing employees that have plans that have at least one plan that is waived or selected.  Mandatory plans are ignored and not included because they are selected by default for the employee.  Drilling into the worker will display the **Worker benefit plans detail** form .

## View more options

To view more information and actions you can take, select **Links**.

![Links.](./media/hr-benefits-management-workspace-links.png)

## See also

[Benefits management overview](hr-benefits-management-overview.md)
