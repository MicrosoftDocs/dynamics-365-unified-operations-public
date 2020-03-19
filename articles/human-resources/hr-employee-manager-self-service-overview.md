---
# required metadata

title: Employee and Manager self-service
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

# Employee and Manager self service

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

The **Time Off Balances** card displays the balances for any enrolled plans. This card forecasts your balance based on your accrual method. You can enter and submit time-off requests, which will then go through and approval workflow process. For more information abouth Leave and absence, see [Leave and absence overview](hr-leave-and-absence-overview).

The **Tasks** card displays tasks that are assigned to you and lets you view and manage them.

The **Next Registered Course** card displays the next course you're registered for. You can view and register for any open courses. All courses that are open for sign up, have a status of started and allow employees to self register appear on this card. Depending on your organization's settings, your course registration might go through and approval process.

The **Certificates** card displays the certificate and expiration date of the certificate expiring closest to the current date. You can update, add, or remove certificates. Depending on your organization's settings, certificate updates might go through an approval process.

The **Next Scheduled Review** card displays your next performance review. A number of actions can be initiated from this card. You can start a new review from this card. Your manager or HR representative can also initiate reviews. Depending on your organization's settings, you might also be able to view, update, and submit exit reviews from this card.

You can manage your goals with the **Performance Goals** card. This card displays the number of goals you have in each status (**Not started**, **On track**, and **Needs improvement**). You can create, update, and remove goals, depending on your assigned role-based security. New goals can be added from groups or templates, or they can be created ad hoc. Managers and HR can also create goals on behalf of employees and determine how detailed each goal will be. Managers and employees can collaborate on goals and update activities, measurements, and status. You can also include attachments.

You can view your existing skills on the **Skills** card. You can update skills, add new ones, or remove any that are no longer relevant. Depending on your organization's settings, changes to your skills might go through an approval process.

You can view your current compensation through the **Compensation** card. Select **Show** to view your annual pay and last increase amount. If you're employed in more than one company, each annual amount displays on the card. To view your detailed compensation history, select the annual salary amount to open the **Fixed and variable compensation history** form. Future compensation don't display in this form. If you have more than one employment, you can switch between companies within this form to view your compensation history without logging into each company.

View and manage documents with the **Attachments** card. You can manage all **External** attachments. Both HR and employees can add attachments through Employee self service or the **Worker** form. Attachments are set to **External** by default.

### Additional information

This section provides links to other Employee self service areas, similar to the **My Career Information** section.

Sign up for benefits through the **Benefits** link. For more information about benefits management, see [Benefits overview](hr-benefits-management-overview)

Under **Performance**, you can can select **Performance journals** to create performance journal entries to use on both performance goals and reviews. You can select **Send feedback** to provide feedback for other employees within your organization. Depending on your organization's settings, emails might be sent to the recipient, sender, and managers. Feedback can be sent to all employees within the organization. This isn't restricted by company.

Under **Competencies**, you can make changes to **Courses**, **Education**, **Positions of trust**, and **Professional experience**. Depending on your organization's settings, updates to these competencies might go through an approval process.




### Organization

In this section, Employees can view job details including the skills, certificates, areas of responsibility for their primary position. In addition, any loaned equipment the employee has "checked out" or has been assigned will be visible. Any changes to the loaned equipment can optionally be routed through an approval workflow.

### Questionnaire

This section allows employees to view any completed questionnaires in the system. An option is also available to see company wide questionnaires that have not been completed and to also make them anonymous. Employees can choose to complete a questionnaire at any time. The author of the questionnaire can determine the time frame and for whom the questionnaire is applicable.

### User defined links

New sections are available if User defined links are configured in Human Resource Parameters. New groups and links can be defined and they will display in a section labeled by the group name used. Typical examples may be to link to pay statements or year end documentation or external solutions. These links will appear at the bottom of this section but can be moved using personalization.

### Embedding external apps

Additional tabs can also be created by embedding PowerApps within the ESS workspace. If you have a power app defined, use the Settings menu to personalize the page. In the menu you can choose to add a PowerApp, complete the details and insert. The power app will be inserted in the selected location. By default the PowerApp will be inserted as the first tab in the sequence. This can be moved using standard personalization.

## My team (Manager self-service)

### Personnel actions

A number of options will display based on configuration options within Human resource shared parameters and Human resource parameters. Personnel actions, when enabled for **Workers** will enable new menu option including: Request new employee, Request new contractor, Request worker reassignment, Request termination and Request compensation change. All of these options when enabled can go through an optional review/approval workflow.

When enabling Position actions in the same setup, the following options will also be available: Request new position and Request change to position details. These options when enabled can also go through a review/approval workflow.

## Summary section

To have access to the my team page you must be in the manager role.
The summary section will contain more or less information based on the options HR has selected in Human resource parameters. On the Manager self-service tab of the Human Resource Parameters page, options are available for displaying expiring records and for displaying open positions. Enabling these options will determine what appears for managers.

The following tiles can be configured for managers:

- Certificates expiring for my team
- Identification numbers expiring for my team
- Probations expiring for my team
- Screenings expiring for my team
- Tests expiring for my team
- Open positions for direct and/or extended reports

Additional options are available for managers:

- Pending time off requests for my team - this inquiry gives managers a view of all time off requests made by direct reports. From this form, managers can see the details and approve or reject any requests.
- Team skills assessment
- Skill gap analysis
- Team performance journals
- Team performance goals
- Team performance reviews
- Exiting workers

### Work on Behalf

Work on behalf options can also be configured in Human resources parameters->Employee self-service. Option include: Certificates, Courses, Loan Items, Skills and Leave and Absence requests. When these items are selected, managers will be able to make changes or add leave requests on behalf of their direct report. When these options are not marked these forms will be view only.

## My team information

My team information allows for viewing and updating of direct and extended reports. To access extended reports, select the employee within your organization that has directs themselves and choose the **View team** option on the card. All of the same options apply to extended reports as direct reports. 

### Summary tab

The summary tab allows for a quick view of the managers direct reports. If a direct reports also has workers reporting to them the card will display the number of direct report in the upper section and a view team button will be available within the card. Options above each card apply to the selected employee, for example if the manager would like to enter a leave request on behalf of an employee, they can select the employee and then choose the request time off option above the cards. 

A details button is also available on each card. (All tabs in this area will have the same details and view team buttons) Once the employee is selected the details button will appear and the following options will appear:

- Certificates
- Compensation
- Courses
- Reviews
- Time off
- Loaned items
- Performance goals
- Registered courses
- Skills
- Send feedback

Based on work on behalf options, managers will be allowed to make changes or these will be view only.

### Position tab

The positions tab provides a summary view of the employee in their primary position. Name, tile and department will display in the heading area of each card. This card includes:

- Seniority date - Displayed from the worker summary section of the worker form
- Years of service - Calculated based on the employees employment start date
- Number of previous positions - Based on position history, this number when selected will open the details view of all previously held positions
- Birth date - This is the month and day of the employees birth date

Position data can be viewed for both direct and extended reports.

### Compensation tab

The compensation card displays the employees annual salary for the company they are employed. A company identifier will display under the salary amount. If an employee has more than one employment and is getting paid out of multiple legal entities then that employee will have multiple compensation cards. The last increase amount and percentage will display based on the company where employment exists.

To view compensation history, simply click on the salary amount and the details form will open. Only current and historical fixed and variable compensation records will display in the compensation form. (no future changes) If an employee has more than one employment, an option will be available to switch between companies to view compensation history in each company.

Compensation can be viewed for both direct and extended reports.

### Leave and absence tab

The leave and absence cards display the top balances for an employee that have activity. This is a display only card. To take action or view a full list of activity, select the details button and select "Time off". This option brings you to the time off form where managers can view balance, requests, approved time off and forecast balances to help employees better manage time. If managers are granted work on behalf rights, they will also be able to make time off requests for there directs and extended reports.

### Performance goals tab

Performance goals summarized by status are displayed in this card. Each value, Not started, On track, and Needs improvement will display with the number of goals in each state. If you click on the number or select performance goals from the details button, you will see all the goals for the employee. Managers and employees can update the goals as needed over the duration of the goal.

Managers can see all goals for their team through the "Team performance goals" tile in the summary section of My team.  

### Reviews tab

Similar to goals, the reviews tab will summarize the reviews the employee has in each state: In progress, Ready for review and Final review. To access the employees review, select the details button and select reviews to collaborate on upcoming or in progress reviews. Based on where a review is with in the workflow process will determine the details the manager can see and if the review is available for updating. 

Managers can see all reviews for their team through the "Team performance reviews" tile in the summary section of My team.

## Related links

The related links section on the my team page will only display if Personnel actions is turned on with "Human resource shared parameters". In the personnel actions section of this form if you turn on Worker and Position actions the following options will appear in the Related Links area.

- My worker actions - This form will display all the managers requests for, new hire, termination, transfer and compensation changes.
- My position actions - This form will display all the manager requests for new positions and changes to existing positions.