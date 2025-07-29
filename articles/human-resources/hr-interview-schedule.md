---
# required metadata

title: Set up the Interview schedule feature in the Dynamics 365 Human Resources Recruiting add-on (preview)
description: Learn about the Interview schedule feature in the Microsoft Dynamics 365 Human Resources Recruiting add-on.
author: twheeloc
ms.date: 04/14/2025
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up the Interview schedule feature in the Dynamics 365 Human Resources Recruiting add-on (preview)

[This article is prerelease documentation and is subject to change.]

This article describes the **Interview schedule** feature in Microsoft Dynamics 365 Human Resources Recruiting add-on.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Currently, customers must manually coordinate interview times among various parties, including candidates, hiring managers, and interviewers. This process is time consuming and prone to errors. Therefore, it can lead to scheduling conflicts, missed opportunities, and delays in the hiring process. Additionally, a poor candidate experience can negatively affect the employer's brand and discourage top talent from pursuing opportunities with the company.

To meet these challenges, Microsoft developed an efficient and well-organized interview scheduling system. This system reduces the time that must be spent on manual coordination and communication, and gives candidates a more positive experience. Recruiters can use the system to book time slots on panel members' calendars, share available slots with candidates, send notifications, and issue meeting invites.

> [!IMPORTANT]
> Outlook and Microsoft Teams licenses are required.

## Find interview time slots for panel members

Recruiters can use this functionality to book time slots for panel members, based on their availability in their Outlook calendar. Recruiters can confirm time slots with panel members before they book them. Alternatively, they can select available time slots for booking without waiting for confirmation from panel members.

### Book a slot with confirmation

1. In the left pane, select **Interview scheduling**.
1. Select **New**.
1. Select the job ad that the interview must be scheduled for.

    All the hiring members are shown as panel members.

1. Select one or more panel members.
1. Select **Find slots**.
1. Select the start date and end date of the interview.
1. Select the duration of the interview.
1. Select **Search time slots**.

    The availability of the selected panel members is shown.

1. Select time slots.
1. Select **Ask confirmation**.

    A notification is to the Teams channel for panel members.

1. Panel members select one or more slots in Teams. 

    Based on their selections, time slots are booked for the interviewer.

After the booking is submitted, the slot status is updated to **Confirmed**.

### Book time slot without confirmation

1. In the left pane, select **Interview scheduling**.
1. Select **New**.
1. Select the job ad that the interview must be scheduled for.

    All the hiring members are shown as panel members.

1. Select one or more panel members.
1. Select **Find slots**.
1. Select the start date and end date of the interview.
1. Select the duration of the interview.
1. Select **Search time slots**.

    The availability of the selected panel members is shown.

1. Select time slots.
1. Select the **Book slots without confirmation** checkbox.
1. Select **Book slots**.

    The selected time slots are booked for the interviewer.

After confirmation is received, the slot status is updated to **Confirmed**.

> [!NOTE]
> Notifications aren't sent to interviewers.

## Share slots

Recruiters can share confirmed interview slots with one or more applicants. Those applicants receive an email notification that contains the confirmed slots. Each applicant can select only one slot at a time. If two applicants select the same slot simultaneously, the system determines which applicant applied first. An updated list of available slots is then sent to the other applicant.

To share slots with candidates, follow these steps.

1. In the left pane, select **Interview scheduling**.
1. Select the job ad that the interview must be scheduled for.
1. Go to **Send meeting invite**.
1. Select the panel member ID.
1. Optional: Select the stage and step.
1. Select **View applicants**.
1. Select an applicant.
1. Select **Share slots**.
1. Review the confirmed slots that are booked for the interviewer.
1. Select and send time slots.

    An email notification that contains the selected time slots is sent.

1. The candidate selects a time slot in the email.

The confirmed time slot appears in the meeting invite section of the Dynamics 365 Human Resources Recruiting add-on. The slot status is updated to **Confirmed**.

## Send a meeting invite

After a candidate books a time slot, the recruiter can confirm the slot with them. They can then send a meeting invite by selecting an appropriate template for the content that must be sent to both the candidate and the interviewer.

To send a meeting invite, follow these steps.

1. In the left pane, select **Interview scheduling**.
1. Select the job ad that the interview must be scheduled for.
1. On the **Send meeting invite** tab, select the applicant who has a **Confirmed** slot status, and then select **Send invite**.
1. In the dialog box for the selected slot, on the **Interviews email** tab, select an email template for the notification that should be sent to the interviewer. Alternatively, manually enter the subject and body of the notification.
1. On the **Candidate's email** tab, select an email template for the notification that should be sent to the candidate. Alternatively, manually enter the subject and body of the notification.
1. Select **Send meeting invite**.

An email notification is sent to the candidate, and a Teams notification is sent to the interviewer. Both notifications include a meeting invite link.

## Provide feedback

Interviewers can now send feedback directly from Teams. Either during or after an interview, the interviewer can fill out and submit a feedback form that is sent to them in Teams. The feedback is updated in the Recruiting add-on, where the recruiter can review it. Based on the feedback, the recruiter can decide whether the applicant should be moved to the next stage of the hiring process or rejected.

To provide feedback, follow these steps.

1. The interviewer receives a feedback notification when the meeting begins.
1. The interviewer provides feedback in Teams during or after the interview.
1. The recruiter reviews the feedback in the Recruiting add-on.

> [!NOTE]
> The feedback form is sent only if the **Send meeting invite** functionality in the Recruiting add-on or the **Interview scheduling** feature is used to send the meeting invite. The feedback form isn't sent if the meeting invite is manually sent.
