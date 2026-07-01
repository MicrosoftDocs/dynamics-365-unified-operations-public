---
# required metadata

title: Distribute and schedule questionnaires
description: This article explains how to distribute the questionnaires that you design, so that they're available to the person or group of people who complete them. 
author: twheeloc
ms.date: 06/25/2026
ms.reviewer: twheeloc
ms.topic: article
# optional metadata

ms.search.form: KMConnectionType, KMKnowledgeCollectorPlanningTabel, SysEmailParameters, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: fd8d867a-2446-400a-b91f-ad4085427470
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Distribute and schedule questionnaires

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to distribute the questionnaires that you design, so that they're available to the person or group of people who complete them.

You can distribute a questionnaire in many ways:

- Mark the questionnaire as **Active**. The questionnaire is then available to all employees, unless a questionnaire group is set up to restrict access to it.
- Assign rights to a questionnaire group. All members of the selected group can access the questionnaire.
- Create planned answer sessions. Only a particular person can access the questionnaire.
- Create a schedule. Multiple people can access the questionnaire.

## Mark a questionnaire as active

When you set the **Active** field to **Yes** on the **Questionnaires** page, you make the questionnaire available for all employees to complete. Respondents can complete the questionnaire multiple times. This functionality is useful if you want to gather continual feedback throughout the year. For example, you can make a questionnaire that employees use to give feedback about the lunch service in the cafeteria.

## Questionnaire groups

Set up questionnaire groups and then include the respondents that a questionnaire should be distributed to.

Create questionnaire groups from the following pages:

- **Questionnaire groups** – Only individuals in a questionnaire group can complete a selected questionnaire. For example, your intended audience is contractors, so you create a questionnaire group that's specific to those respondents.
- **Questionnaire group members** – Add people to the questionnaire groups.

To assign a questionnaire group to a questionnaire, on the **Questionnaires** page, select **User rights**. After you save the questionnaire as active, the members of the questionnaire group can complete the questionnaire. This functionality is helpful if you want to test a questionnaire on a select group of people before you roll it out to a larger group, or if you want to target a questionnaire to a specific audience.

## Planned answer sessions in a questionnaire

Planned answer sessions are questionnaires that you design and select the respondents for.

> [!NOTE]
> Before you can set up planned answer sessions, you must design a questionnaire.

On the **Planned answer session** page, you can create a planned answer session for an individual employee. The list on the page displays all planned questionnaires.

Use planned answer sessions on the **Questionnaire schedules** page to plan questionnaires for multiple people:

- Employees
- Course participants
- Organizational units

Each person can answer the questionnaire only one time.

## Scheduling a questionnaire

You can optionally schedule a questionnaire for multiple respondents.

### Planning types

Use planning types when you want to schedule planned answer sessions for multiple respondents. Planning types classify questionnaire schedules. For example, you can schedule questionnaires for the following purposes:

- Evaluation
- Survey
- Testing

Specify planning types for a questionnaire schedule on the **Questionnaire schedules** page.

### Reference types for questionnaire

Use reference types to enter criteria for the respondents that you might select when you schedule a questionnaire.

Use the **Reference types** page to set up reference types for a questionnaire. Each reference type corresponds to a table in Microsoft Dynamics 365 Finance. When you create questionnaire schedules, you can specify individual records in the table or a range of records that the questionnaire associates with.

For example, if you select the Courses table, you can decide which specific course the questionnaire is for. When you set up a reference for the Courses table, some fields and buttons on the **Courses** page become available.

### Questionnaire schedules

Use questionnaire schedules to generate multiple planned answer sessions for a group of users, based on a reference type. Create a schedule on the **Questionnaire schedules** page. Select the planning type to categorize the schedule, and also select the reference type that should be used to query the system for specific users. For example, if you set the reference type to the Courses table, you can select a specific course in the **Reference** field.

Select **Setup details** to select the questionnaire and other criteria. For example, specify the instructor's name as a criterion if the questionnaire is an evaluation of the instructor. After you finish entering the setup details, the system generates planned answer sessions for the users that are included in the query.

Select **Planned answer sessions** to view the answer sessions for the schedule. You can then manually create additional planned answer sessions or delete planned answer sessions that aren't answered.

Select **Functions** &gt; **Start** to make the questionnaire available to the users in related planned answer sessions. Select **Answers** to view the completed responses to the questionnaire. You can optionally copy the questionnaire schedule settings, planned answer sessions, and answers to a new questionnaire schedule.

## Notifying respondents about available questionnaires

When you distribute a questionnaire, notify respondents that questionnaires are available to them.

### Notifying respondents about a planned answer session

If you use a planned answer session, notify the person directly, such as by telephone or email.

### Notifying respondents about a scheduling

Use the **Questionnaire schedules** page to prepare and send email to all respondents who are assigned to the questionnaire. Enter the email text on the **Email for employee self service** tab. After the schedule starts, select **Functions** &gt; **Send email** to generate and send the email to the respondents. Respondents can then sign in to the website and complete the questionnaire.

> [!NOTE]
> Before you can use the email functionality, your IT administrator must enter the email settings on the **Email parameters** page.

## Ending a scheduled questionnaire

You can end a scheduled questionnaire after all respondents complete their assigned answer sessions. After you end a scheduled questionnaire, you can't copy its settings to a new schedule.

> [!NOTE]
> If one or more respondents didn't complete the questionnaire, but you still want to end the scheduling, first delete those respondents from the list on the **Planned answer session** page. You can then end the schedule.

## Completing questionnaires

After you design and distribute a questionnaire, selected respondents can complete it. You can complete the questionnaires available to you from two locations:

- In the navigation pane, select **Questionnaires** > **Distribute** > **Complete a questionnaire**.
- In Employee self-service, select **Questionnaires to complete**.

You can make questionnaires available to specific users or groups of users, or to all users in a network.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
