---
# required metadata

title: Recruit job candidates
description: This topic shows how to recruit candidates in Dynamics 365 Human Resources.
author: andreabichsel
manager: tfehr
ms.date: 12/01/2020
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
ms.search.validFrom: 2020-11-18
ms.dyn365.ops.version: Human Resources

---

# Recruit job candidates

[!include [banner](includes/preview-feature.md)]

Dynamics 365 Human Resources helps you to manage recruiting requests and seamlessly transition job candidates to employees. Human Resources allows your organization to integrate with third-party recruiting applications, so your recruiting process might include the following steps:

- Enter your recruiting request in Human Resources
- Receive candidate referrals in Human Resources from the recruiting application
- Complete the candidate approval process in Human Resources

<include graphic>

If you aren't using a separate recruiting application, you can also manually manage candidates in Human Resources.

>[!NOTE]
>If you're an admin or developer and want to integrate Human Resources with a third-party recruiting application, see <link to topics>. You can also find a recruiting integration app on AppSource.

Add a recruiting request

If you're a manager, you can submit a recruiting request in Human Resources. If you use a separate recruiting application, completing these steps will send a recruiting request to that application and start the recruiting process. Otherwise, complete this procedure to begin the workflow for your own internal recruiting process.

1. Select **Employee self service**.
2. Select the **My team** tab.
3. Select  **Request to recruit**.
4. In **Description**, enter a description for the position.
5. In **Job**, enter the job title for the position.
6. In **Estimated start date**, enter a start date for the position.
7. Select **Continue**. The recruiting request for your position appears.
8. Under **General**, select a recruiter from the **Recruiter** dropdown, and then select a location from the **Recruiting request location** dropdown.
9. Under **Job**, change any information as needed, and then select **Create details from job**. This populates the rest of the recruiting request with the default information for the job you entered.
10. Under **Position**, select a position for this recruiting request.
11. Customize the information under **External description**, **Skills**, **Educational requirements** as needed.
12. When your recruiting request is complete and you're ready to start the recruiting process, under **General** change **Status** from **Draft** to **Active**.


View and edit your recruiting requests

If you're a manager and want to view your requests:

1. Select **Employee self service**.
2. Select the **My team** tab.
3. Under **My team information**, select the **Recruiting requests** tab.
4. To view or edit a recruiting request, select it in the grid.

If you're an HR pro and want to view all recruiting requests:

1. Select **Personnel management**.
2. Select **Recruiting requests**.
3. To view or edit a recruiting request, select it in the grid.

Add or edit a candidate profile

If your organization has integrated with another application to manage recruiting requests, recruiting requests are forwarded to that application. In turn, the recruiting application sends candidate information back to Human Resources. Otherwise, you can follow your own internal recruiting processes and enter candidate information manually.

1. Select **Personnel management**.
2. Select **Links**.
3. Under **Recruiting**, select **Candidates**.
4. To add a candidate, select **New**. To edit an existing candidate, select the candidate from the list and then select **Edit**. The candidate profile appears.
5. Under **Candidate summary**, enter or edit the candidate information as necessary.
6. Under **Recruiting request**, select a recruiting request to link the candidate to. Then complete the **Estimated start date**, **Hiring manager**, **Position**, and **Description fields** as appropriate.
7. Complete all the information in the following areas that you want to include in the candidate's record:
   - **Comments**
   - **Professional experience**
   - **Contact information**
   - **Education**
   - **Skills**
   - **Certificates**
   - **Screenings**

Hire a candidate

When you're ready to hire a candidate, follow this procedure to transition the candidate to an employee.

1. On the candidate form, select **Hire**.
2. On the **Hire new worker** form, under **Details**, enter the following information:
   - **SSN** - the employee's social security number
   - **Employment start date** - defaults to today's date
   - **Employment end date** - defaults to **Never**
   - **Employment category** - select an option from the dropdown box
   - **Employment type** - select an option from the dropdown box
3. Under **Position details**, verify and change information as necessary.
4. Under **Onboarding checklists**, select the relevant onboarding checklists for this employee.
5. Select **Hire and add details** to create the employee record.
   >[!NOTE]
   >Depending on your organization's workflows, the candidate record may go through additional approval steps before becoming an employee record.

Decide not to hire a candidate

If you decide not to hire a candidate, follow this procedure to remove them from the vetting process. 

1. On the candidate form, select **Do not hire**.
2. Select a **Reason code** and include any comments.
3. Select **OK**.

Dismiss a candidate

If needed, you can dismiss a candidate after hiring them. For example, a candidate might reject your offer or not show up on their first day.

1. On the candidate form, select **Dismiss candidate**.
2. Select a **Reason code** and include any comments.
3. Select **OK**.

See also
(link to virtual entities)
(link to other topics related to setting up reason codes, workflows, etc)



