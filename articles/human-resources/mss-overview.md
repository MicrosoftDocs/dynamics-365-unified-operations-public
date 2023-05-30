---
# required metadata

title: Manager self service overview
description: This article provides an overview of the Manager self service workspace.
author: twheeloc
ms.date: 03/10/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Manager self service overview

[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article provides an overview of the **Manager self service** workspace.

**Manager self service** enables people managers to access personnel data for their direct reports, such as leave, time-off, performance, and learning information. These capabilities let managers perform limited human resources (HR) tasks, maintain compliance reporting, access real-time data, and save time. At the same time, the capabilities help reduce HR administrative tasks.

**Manager self service** has the same navigation as **Employee self service**, except a **My team** tab is added next to the **My information** tab. The **My team** tab is visible and accessible only to managers.

## Configure Employee self service

To configure **Employee self service**, go to **Human resources \> Employee self service**. You can configure the following options to enable managers to make changes on behalf of their direct reports:

- Certificates
- Courses
- Loan items
- Project experience
- Skills
- Add leave and absence requests

## Configure Manager self service

To configure **Manager self service**, go to **Human resources \> Manager self service**. In the **Manager self service** workspace, managers can set up, view, and access the following information:

- View emergency contacts

    - None (default)
    - Direct reports only
    - Extended reports (includes direct reports and extended reports)

- View expiring records option

    - None
    - Direct reports only
    - Extended reports (includes direct reports and extended reports)

- Open positions

    - Direct reports only
    - Extended reports
    - Both
    - None

- Exiting workers

    - None
    - Direct reports only
    - Extended reports

### Configure personnel actions

To configure personnel actions, go to **Human resources \> Shared parameters**, and then, on the **Human resources shared parameters**, select the **Personnel actions** tab.

**Enable worker actions** shows the following options:

- Request new employee
- Request new contractor
- Request worker reassignment
- Request termination
- Request compensation change

**Enable position actions** shows the following options:

- Request new position
- Request change to position details

The **My team** tab is divided into two sections: **Summary** and **My team information**.

### Summary section

Information in the **Summary** section depends on the options that are selected on the **Human resources parameters** page. On the **Manager self service** tab of the **Human resources parameters** page, you can configure options for the display of expiring records and open positions. The configuration of these options determines what managers see in the **Summary** section.

You can configure the following tiles for managers:

- Certificates expiring for my team
- Identification numbers expiring for my team
- Probations expiring for my team
- Screenings expiring for my team
- Tests expiring for my team
- Open positions for direct and/or extended reports
- Pending time off requests for my team
- Team skills assessment
- Skill gap analysis
- Team performance journals
- Team performance goals
- Team performance reviews
- Exiting workers

### My team information section

The **My team** section lets managers view and update direct and extended reports. To access extended reports, select the employee who has direct reports, and then select **View team** on the tile. All the same options apply to extended reports and direct reports.

#### Summary tab

The **Summary** tab provides a quick view of your direct reports. If one of your direct reports also has workers who report to them, the upper part of the card shows the number of direct reports and a **View team** button. Options above each tile apply to the selected employee. For example, if you want to enter a leave request on behalf of an employee, you select the employee and then select **Request time off**.

If you select **Details** after you select an employee, the following options appear:

- Certificates
- Compensation
- Courses
- Reviews
- Time off
- Loaned items
- Performance goals
- Project experience
- Skills
- Send feedback
- Signing limits

Depending on your organization's settings, you can either make changes to the details or only view them.

#### Position tab

The **Position** tab provides a summary view of employees in their primary position. **Name**, **Title**, and **Department** values appear in the heading area of each tile. Each tile includes the following information:

- **Seniority date** – The date is taken from the worker summary section of the **Worker** page.
- **Years of service** – The number is calculated based on the employee's employment start date.
- **Number of previous positions** – Depending on the position history, you can select the number to open a detailed view of all previously held positions.
- **Birth date** – The month and day of the employee's birth date.

You can view position data for both direct reports and extended reports.

#### Compensation tab

The **Compensation** tab shows the employee's annual salary. A company identifier appears under the salary amount. An employee who has more than one employment and is getting paid from multiple legal entities will have multiple compensation plans. To view all compensation plans across all legal entities without switching companies, you must enable cross-company compensation by setting the **Enable cross company compensation** option on the **Advanced access** tab of the **Human resources shared parameters** page.

To view compensation history, select the **Salary amount** value to open the **Details** page. Only current and historical fixed and variable compensation records appear on the **Compensation** page. If an employee has more than one employment, you can switch between companies to view compensation history in each company. Alternatively, you can enable cross-company compensation on the **Human resources shared parameters** page to view all compensation plans.

You can view compensation for both direct reports and extended reports.

#### Leave and absence tab

The **Leave and absence** tab shows the top balances for employees that have activity. To take action or view a full list of activities, select **Details**, and then select **Time off**. On the **Time off** page, you can view balances, requests, approved time off, and forecast balances to help employees better manage time. Depending on your organization's settings, you can also request time off for your direct and extended reports.

#### Performance goals tab

The **Performance goals** tab summarizes performance goals by status. Select a number for a status, or select performance goals from the **Details** page to view all goals for an employee. Managers and employees can update goals as required over their duration.

Managers can view all goals for their team through the **Team performance goals** tile in the **Summary** section of the **My team** tab.

#### Reviews tab

The **Reviews** tab summarizes the reviews that the employee has in each state (**In progress**, **Ready for review**, and **Final review**). To access an employee's reviews, select **Details**, and then select reviews to collaborate on. Depending on a review's location in the workflow process, you can see whether the review is available for updates.

You can view all reviews for your team through the **Team performance reviews** tile in the **Summary** section of the **My team** tab.

#### Learning tab

The **Learning** tab provides an overview of courses that have been assigned to employees. The courses are categorized as **All assigned courses**, **Overdue**, and **Due soon**. Select the **Course ID** value to drill into all the details of a course.

Managers can assign a course to one of their employees by selecting **Assign course**. The manager can either create a new course or assign a previously created course to the employee. This functionality helps managers drive a culture of continuous learning and development that can, in turn, drive employee engagement, retention, and business success.
