---
# required metadata

title: Distribute and schedule questionnaires
description: This article explains how distribute the questionnaires that you design, so that they are available to the person or group of people who will complete them. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KMConnectionType, KMKnowledgeCollectorPlanningTabel, SysEmailParameters, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: fd8d867a-2446-400a-b91f-ad4085427470
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Distribute and schedule questionnaires


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how distribute the questionnaires that you design, so that they are available to the person or group of people who will complete them. 

There are multiple ways to distribute a questionnaire:

-   Mark the questionnaire as **Active**. The questionnaire is then available to all employees, unless a questionnaire group is set up to restrict access to it.
-   Assign rights to a questionnaire group. The questionnaire is then available to all members of the selected group.
-   Create planned answer sessions. The questionnaire is then available only to a particular person.
-   Create a schedule. The questionnaire can then be available to multiple people.

## Marking a questionnaire as active

By setting the **Active** field to **Yes** on the **Questionnaires** page, you make the questionnaire available for all employees to complete. Respondents can complete the questionnaire multiple times. This functionality is useful if you want to gather continual feedback throughout the year. For example, you can make a questionnaire that employees use to give feedback about the lunch service in the cafeteria.

## Questionnaire groups

You can set up questionnaire groups and then include the respondents that a questionnaire should be distributed to. 

You can create questionnaire groups from the following pages:

-   **Questionnaire groups** – Only individuals in a questionnaire group can complete a selected questionnaire. For example, your intended audience is contractors, so you create a questionnaire group that is specific to those respondents.
-   **Questionnaire group members** – You can add people to the questionnaire groups.

To assign a questionnaire group to a questionnaire, on the **Questionnaires** page, click **User rights**. After the questionnaire is saved as active, the members of the questionnaire group can complete the questionnaire. This functionality is helpful if you want to test a questionnaire on a select group of people before you roll it out to a larger group, or if you want to target a questionnaire to a very specific audience.

## Planned answer sessions in a questionnaire

Planned answer sessions are questionnaires that you've designed and selected the respondents for. 

> [!NOTE]
> Before you can set up planned answer sessions, you must design a questionnaire. 

On the **Planned answer session** page, you can create a planned answer session for an individual employee. The list on the page displays all planned questionnaires. 

Planned answer sessions are also used on the **Questionnaire schedules** page, where you can plan questionnaires for multiple people:

-   Employees
-   Course participants
-   Organizational units

Each person can answer the questionnaire only one time.

## Scheduling a questionnaire

You can optionally schedule a questionnaire for multiple respondents.

### Planning types

Planning types are required if you want to schedule planned answer sessions for multiple respondents. Planning types are used to classify questionnaire schedules. For example, you can schedule questionnaires for the following purposes:

-   Evaluation
-   Survey
-   Testing

You can specify planning types for a questionnaire schedule on the **Questionnaire schedules** page.

### Reference types for questionnaire

You can use reference types to enter criteria for the respondents that you might select when you schedule a questionnaire. 

Use the **Reference types** page to set up reference types for a questionnaire. Each reference type corresponds to a table in Microsoft Dynamics 365 Finance. When you create questionnaire schedules, you can specify individual records in the table or a range of records that the questionnaire will be associated with. 

For example, if you select the Courses table, you can decide which specific course the questionnaire will be for. When you set up a reference for the Courses table, some fields and buttons on the **Courses** page become available.

### Questionnaire schedules

You can use questionnaire schedules to generate multiple planned answer sessions for a group of users, based on a reference type. Create a schedule on the **Questionnaire schedules** page. Select the planning type to categorize the schedule, and also select the reference type that should be used to query the system for specific users. For example, if you set the reference type to the Courses table, you can select a specific course in the **Reference** field. 

Click **Setup details** to select the questionnaire and other criteria. For example, specify the instructor's name as a criterion if the questionnaire is an evaluation of the instructor. After you've finished entering the setup details, the system generates planned answer sessions for the users that are included in the query. 

Click **Planned answer sessions** to view the answer sessions for the schedule. You can then manually create additional planned answer sessions or delete planned answer sessions that haven't been answered. 

Click **Functions** &gt; **Start** to make the questionnaire available to the users in related planned answer sessions. Click **Answers** to view the completed responses to the questionnaire. You can optionally copy the questionnaire schedule settings, planned answer sessions, and answers to a new questionnaire schedule.

## Notifying respondents about questionnaires that are available to them
When you distribute a questionnaire, you must notify respondents that questionnaires are available to them. 

### Notifying respondents about a planned answer session

If you use a planned answer session, you must notify the person directly, such as by telephone or email.

### Notifying respondents about a scheduling

Use the **Questionnaire schedules** page to prepare and send email to all respondents who are assigned to the questionnaire. Enter the email text on the **Email for employee self service** tab. After the schedule has been started, click **Functions** &gt; **Send email** to generate and send the email to the respondents. Respondents can then sign in to the website and complete the questionnaire. 

> [!NOTE]
> Before you can use the email functionality, your IT administrator must enter the email settings on the **Email parameters** page.

## Ending a scheduled questionnaire

You can end a scheduled questionnaire after all respondents have completed their assigned answer sessions. After a scheduled questionnaire is ended, you can't copy its settings to a new schedule. 

> [!NOTE]
>   If one or more respondents haven't completed the questionnaire, but you still want to end the scheduling, you must first delete those respondents from the list on the **Planned answer session** page. You can then end the schedule.

## Completing questionnaires

After you've designed and distributed a questionnaire, the questionnaire can be completed by selected respondents. You can complete the questionnaires that are available to you from two locations:

-   In the navigation pane, click **Questionnaires** &gt; **Distribute** &gt; **Complete a questionnaire**.
-   In Employee self-service, click **Questionnaires to complete**.

Questionnaires can made be available to specific users or groups of users, or to all users in a network.




[!INCLUDE[footer-include](../includes/footer-banner.md)]
