---
# required metadata

title: Employee and Manager self-service overview
description: This article provides an overview of the employee and manager self service workspace.
author: andreabichsel
manager: AnnBe
ms.date: 03/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: HRMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Human Resources
# ms.tgt_pltfrm: 
ms.custom: 51941
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Employee and Manager self service overview

This article provides an overview of the employee and manager self service workspace.

## Edit personal details

If you need to add or change any personal information, see [Edit personal information](hr-employee-manager-self-service-edit-personal-information.md).

## Employee self service

The **My information** tab displays the following information for Employee self service.  

### Summary

**Work items assigned to me** displays all approvals and workflow items that are assigned to the employee. You can configure workflow items to send emails to the user.

**Questionnaires assigned to me** display all scheduled questionnaires assigned directly to the employee or group.

**Company directory** lets employees look up information related to individuals in the organization. Public contact information is available to all employees. The company directory is restricted to the company that the employee has signed into.

**Team calendar** shows your team's calendar information. For more information, see [View team and company calendars](hr-employee-self-service-calendar.md).

### My career information

The **My career information** section of Employee self-service contains cards related to Leave and Absence, Performance Management, Competencies, Benefits, Tasks, and Attachments.

The **Time Off Balances** card displays the balances for any enrolled plans. This card forecasts your balance based on your accrual method. You can enter and submit time-off requests, which will then go through an approval workflow process. For more information about Leave and absence, see [Leave and absence overview](hr-leave-and-absence-overview).

The **Tasks** card displays tasks that are assigned to you and lets you view and manage them.

The **Next Registered Course** card displays the next course you're registered for. You can view and register for any open courses. All courses that are open for sign-up have a status of **Started**, and allow employees to self-register appear on this card. Depending on your organization's settings, your course registration might go through an approval process.

The **Certificates** card displays the certificate and expiration date of the certificate expiring closest to the current date. You can update, add, or remove certificates. Depending on your organization's settings, certificate updates might go through an approval process.

The **Next Scheduled Review** card displays your next performance review. You can start a new review from this card. Your manager or HR representative can also initiate reviews. Depending on your organization's settings, you might also be able to view, update, and submit exit reviews from this card.

You can manage your goals with the **Performance Goals** card. This card displays the number of goals you have in each status (**Not started**, **On track**, and **Needs improvement**). You can create, update, and remove goals, depending on your assigned role-based security. If you want, you can add new goals from groups or templates. Managers and HR can also create goals on behalf of employees and determine how detailed each goal will be. Managers and employees can collaborate on goals and update activities, measurements, and status. You can also include attachments.

You can view your existing skills on the **Skills** card. You can update skills, add new ones, or remove any that are no longer relevant. Depending on your organization's settings, changes to your skills might go through an approval process.

You can view your current compensation through the **Compensation** card. Select **Show** to view your annual pay and last increase amount. If you're employed in more than one company, each annual amount displays on the card. To view your detailed compensation history, select the annual salary amount to open the **Fixed and variable compensation history** form. Future compensation doesn't display in this form. If you have more than one employment, you can switch between companies within this form to view your compensation history without logging into each company.

View and manage documents with the **Attachments** card. You can manage all **External** attachments. Both HR and employees can add attachments through Employee self service or the **Worker** form. Attachments are set to **External** by default.

### Additional information

This section provides links to other Employee self service areas, similar to the **My Career Information** section.

Sign up for benefits through the **Benefits** link. For more information about Benefits management, see [Benefits overview](hr-benefits-management-overview)

Under **Performance**, you can select **Performance journals** to create performance journal entries to use on both performance goals and reviews. You can select **Send feedback** to provide feedback for other employees within your organization. Depending on your organization's settings, emails might be sent to the recipient, sender, and managers. You can send feedback to all employees within the organization. Sending feedback isn't restricted by company.

Under **Competencies**, you can make changes to **Courses**, **Education**, **Positions of trust**, and **Professional experience**. Depending on your organization's settings, updates to these competencies might go through an approval process.

You can view job details under **Organization**. Job details include skills, certificates, and areas of responsibility for your primary position. You can also see any loaned equipment checked out to you. Depending on your organization's settings, changes to loaned equipment might go through an approval process.

Under **Questionnaire**, you can see completed questionnaires. You can also see company-wide questionnaires that haven't been completed. You can choose to complete a questionnaire at any time. The author of the questionnaire can determine the time frame and for whom the questionnaire is applicable.

You can configure user-defined links in **Human Resources parameters**. For example, you can define links to pay statements, year-end documentation, or external solutions. These links display at the bottom of this section, but you can move them by using personalization.

You can also create additional tabs by embedding Power Apps within the Employee self service workspace. Use the **Settings** menu to personalize the page with any Power Apps. In the **Settings** menu, you can choose to add a Power App, complete the details, and insert the app. By default, Power Apps appears as the first tab in the sequence. You can change the order by using standard personalization.

## My team

The **My team** tab displays the following information for Manager self service. Only managers can access the **My team** tab.

### Personnel actions

Personnel actions display based on configuration options within **Human resources shared parameters** and **Human resources parameters**. When enabled for **Workers**, personnel actions enable new menu options, including:

- **Request new employee**
- **Request new contractor**
- **Request worker reassignment**
- **Request termination**
- **Request compensation change**

You can configure these options to go through an optional review and approval workflow.

Enabling **Position actions** enable the following options:

- **Request new position**
- **Request change to position details**

You can also configure these options to go through an optional review and approval workflow.

### Summary

Information in the **Summary** section depends on the options HR has selected in **Human resource parameters**. On the **Manager self service** tab of the **Human Resources parameters** page, you can configure options for displaying expiring records and open positions. Enabling these options determines what managers can see in the **Summary** section.

You can configure the following tiles for managers:

- **Certificates expiring for my team**
- **Identification numbers expiring for my team**
- **Probations expiring for my team**
- **Screenings expiring for my team**
- **Tests expiring for my team**
- **Open positions for direct and/or extended reports**
- **Pending time off requests for my team**
- **Team skills assessment**
- **Skill gap analysis**
- **Team performance journals**
- **Team performance goals**
- **Team performance reviews**
- **Exiting workers**

You can configure the following options for managers to make changes or add leave requests on behalf of their direct reports:

- Certificates
- Courses
- Loan items
- Skills
- Leave and absence requests

### My team information

My team information allows managers to view and update direct and extended reports. To access extended reports, select the employee who has directs, and then choose **View team** on the card. All of the same options apply to extended reports as direct reports. 

#### Summary tab

The **Summary** tab provides a quick view of your direct reports. If a direct report also has workers reporting to them, the card displays the number of direct reports in the upper section, along with a **View team** button. Options above each card apply to the selected employee. For example, if you want to enter a leave request on behalf of an employee, you select the employee and then choose **Request time off** above the cards. 

If you select the **Details** button after selecting an employee, the following options display:

- **Certificates**
- **Compensation**
- **Courses**
- **Reviews**
- **Time off**
- **Loaned items**
- **Performance goals**
- **Registered courses**
- **Skills**
- **Send feedback**

Depending on your organization's settings, you can either make changes or view only.

#### Position tab

The **Positions** tab provides a summary view of employees in their primary position. Name, tile, and department displays in the heading area of each card. This card includes:

- **Seniority date** - Displayed from the worker summary section of the worker form
- **Years of service** - Calculated based on the employee's employment start date
- **Number of previous positions** - Based on position history, selecting this number opens the detailed view of all previously held positions
- **Birth date** - The month and day of the employee's birth date

You can view position data for both direct and extended reports.

#### Compensation tab

The **Compensation** tab displays the employee's annual salary. A company identifier displays under the salary amount. If an employee has more than one employment and is getting paid from multiple legal entities, the employee will have multiple compensation cards. The last increase amount and percentage displays, based on the company of employment.

To view compensation history, select the salary amount to open the **Details** form. Only current and historical fixed and variable compensation records display in the **Compensation** form. If an employee has more than one employment, you can switch between companies to view compensation history in each company.

You can view compensation for both direct and extended reports.

#### Leave and absence tab

The **Leave and absence** tab displays the top balances for employees that have activity. To take action or view a full list of activities, select **Details** and then select **Time off**. On the **Time off** form, you can view balances, requests, approved time off, and forecast balances to help employees better manage time. Depending on your organization's settings, you can also request time off for your directs and extended reports.

#### Performance goals tab

The **Performance goals** tab summarizes performance goals by status. Select a number for a status or select performance goals from the **Details** to see all goals for an employee. Managers and employees can update goals as needed over the duration of the goal.

Managers can see all goals for their team through the **Team performance goals** tile in the **Summary** section of **My team**.

#### Reviews tab

The **Reviews** tab summarizes the reviews the employee has in each state: **In progress**, **Ready for review**, and **Final review**. To access an employee's review, select the **Details** button and then select reviews to collaborate on. Based on where a review is within the workflow process, you can see if the review is available for updating. 

You can see all reviews for your team through the **Team performance reviews** tile in the **Summary** section of **My team**.