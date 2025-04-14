---
# required metadata

title: Set up the Interview schedule feature in Dynamics 365 Human Resources Recruiting add-on (preview)
description: This article describes the Interview schedule feature in Dynamics 365 Human Resources Recruiting add-on. 
author: twheeloc
ms.date: 04/14/2025
ms.topic: article
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

# Set up the Interview schedule feature in Dynamics 365 Human Resources Recruiting add-on (preview)
[This article is prerelease documentation and is subject to change.]

This article describes the Interview schedule feature in Dynamics 365 Human Resources Recruiting add-on.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Customers currently need to manually coordinate interview times among various parties, including candidates, hiring managers, and interviewers. This process is time-consuming and prone to errors, potentially
leading to scheduling conflicts, missed opportunities, and delays in the hiring process. Additionally, a poor candidate experience can negatively impact the employer's brand and discourage top talent from
pursuing opportunities with the company. 

We have developed an efficient and well-organized interview scheduling system that reduces the time spent on manual coordination and communication and provides candidates with a more positive experience. This
system enables recruiters to book panel members' calendars, share available slots with candidates, send notifications, and issue meeting invitations. 

>[Note]
> Outlook and MS Teams licenses are required. 

## Find time slots  

This functionality allows recruiters to book time slots for panel members based on their Outlook calendar availability. Recruiters can either confirm the time slot with the panel member or directly select an
available time slot for booking. 

### Find interview time slots for panel member 

To find time slots for a panel member, follow these steps:

### Book slot with confirmation 
1. Click **Interview scheduling** from left menu pane.
2. Click **+New**.
3. Select the job ad that the interview needs to be scheduled for.
4. After selecting the job ad, all the hiring members are visible as panel members.
5. Select one or more panel member.
6. Click **Find slots**. This opens a window to select the start date and end date of the interview.
7. Select the duration of the interview. 
8. Click **Search time slots**. This displays the availability of the selected panel members.
9. Select the time slots.
10. Click **Ask confirmation**. This sends a notification to the panel members Microsoft teams channel.
11. Panel members can select one or more slots from teams.
12. Based on the selection, time slots are booked for the interviewer. 
Once submitted, the slot status is updated to **Confirmed**. 

### Book time slot without confirmation 

To book a time slot without confirmation, follow these steps:
1. Click **Interview scheduling** from left menu pane.
2. Click **+New**.
3. Select the job ad that the interview needs to be scheduled for.
4. After selecting job ad, all the hiring members are displayed as a panel members.
5. Select one or more panel members.
6. Click **Find slots**.
7. This displays a window to select the start date and end date of the interview.
8. Select the duration of the interview.
9. Click **Search time slots**. This displays availability of the selected panel members.
10. Select the time slots.
11. Select the **Book slots without confirmation** checkbox.
12. Click **Book slots**. The selected time slots are booked for the interviewer. 
Once confirmed, the slot status is updated to **Confirmed**.

>[!Note:]
> Notifications aren't sent to the interviewers. 

### Share slots 

Recruiters can share confirmed interview slots with one or more applicants. These applicants receive an email notification containing these confirmed slots. Each applicant can only select one slot at a time. In cases where two applicants select the same slot simultaneously, the system determines which applicant applied first and an updated list of available slots is sent to the other applicant. 

To share slots with candidates, follow these steps:
1. Click **Interview Scheduling** on the left menu.
2. Choose the job ad for the interview.
3. Go to **Send meeting invite**.
4. Select the panel member ID.
5. (Optional) Select the stage and step.
6. Click **View applicants** to see applicants.
7. Select an applicant.
8. Click **Share slots**.
9. View confirmed slots booked for this interviewer.
10. Select and send time slots and a notification email with the selected time slots is sent.
11. The candidate selects a time slot from their email.
12. The confirmed time slot appears in the meeting invite section of the Dynamics 365 HR recruiting add-on.
The **Slot status** is updated to **Confirmed**.

### Send the meeting invite  
After the candidate books a time slot, the recruiter can send the meeting invitation. They can confirm the slot with the applicant and send the meeting invite by selecting an appropriate template for the content that needs to be sent to both the candidate and the interviewer. 

To send a meeting invite, follow these steps:
1. Click **Interview scheduling** in the left menu.
2. Select the job ad to schedule an interview for.
3. Go to **Send meeting invite** tab.
4. Select the applicant with a confirmed slot status and click **Send invite**.
5. A window opens showing the selected slot.
6. Go to the **Interviews email** tab and select an email template or write the subject and body manually.
7. Go to the **Candidate’s email** tab and select an email template or write the subject and body manually.
8. Click **Send meeting** invite. 
An email notification is sent to the candidate and a Teams notification is sent to the interviewer with a meeting invite link. 

### Provide feedback 

Interviewers can now send feedback directly from Microsoft Teams. During or after the interview, a feedback page is sent to the interviewer's Microsoft Teams. The interviewer can fill out the form and submit it. The feedback is updated in the HR recruiting add-on, which the recruiter can view to make decisions. 

To provide feedback, follow these steps:
1. Interviewer receives a feedback notification when the meeting starts.
2. Interviewer provides feedback on Microsoft Teams during or after the interview.
3. Recruiter views feedback in the HR recruiting add-on. 
Applicants are moved to the next stage or rejected based on feedback. 

>[!Note]
> The feedback page isn't sent if the meeting invitation is sent manually. The feedback page is only sent when the send meeting invite functionality is used in the recruiting add-on or interview scheduling. 


