---
# required metadata

title: Set up the Interview schedule feature in Dynamics 365 Human Resources (preview)
description: This article describes the Interview schedule feature in Dynamics 365 Human Resources. 
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

# Set up the Interview schedule feature in Dynamics 365 Human Resources (preview)
[This article is prerelease documentation and is subject to change.]

This article describes the Interview schedule feature in Dynamics 365 Human Resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Customers currently need to manually coordinate interview times among various parties, including candidates, hiring managers, and interviewers. This process is time-consuming and prone to errors, potentially
leading to scheduling conflicts, missed opportunities, and delays in the hiring process. Additionally, a poor candidate experience can negatively impact the employer's brand and discourage top talent from
pursuing opportunities with the company. 

We have developed an efficient and well-organized interview scheduling system that reduces the time spent on manual coordination and communication and provides candidates with a more positive experience. This
system enables recruiters to book panel members' calendars, share available slots with candidates, send notifications, and issue meeting invitations. 

Note: Outlook and MS Teams licenses are required. 

## Find slots  

This functionality allows recruiters to book time slots for panel members based on their Outlook calendar availability. Recruiters can either confirm the slot with the panel member or directly select an
available slot for booking. 

### How to find slots for panel member 

Book slot with confirmation 

Click on interview scheduling from left menu pane. 
Click on +new. 
Select the job at for which interview needs to be schedule. 
On selecting job ad, all the hiring members will be visible as a panel member below. 
Select one or more panel member. 
Click on find slots 
This will open window. Select the start date and end date of the interview. 
Select the duration of the interview. 
Click on search time slots. 
This will show the availability of the selected panel members. 
Select the slots. 
Click on Button ‘Ask confirmation’. 
This will trigger a notification to Panel members Microsoft teams channel. 
Panel members can select one or more slots from teams. 
Based on the selection, slots will be booked for the interviewer. 
Once submitted, the slot status will be changed to confirmed. 

### Book slot without confirmation 

Click on interview scheduling from left menu pane. 
Click on +new. 
Select the job at for which interview needs to be schedule. 
On selecting job ad, all the hiring members will be visible as a panel member below. 
Select one or more panel member. 
Click on find slots 
This will open window. Select the start date and end date of the interview. 
Select the duration of the interview. 
Click on search time slots. 
This will show the availability of the selected panel members. 
Select the slots. 
Check the checkbox ‘Book slots without confirmation’ 
Click on Button ‘book slots. 
Selected slots will be booked for the interviewer. 
Once confirmed, the slot status will be changed to confirmed. 
Note: There will not be any notification to interviewer. 

### Share slots 

Recruiters can share confirmed interview slots with one or more applicants. These applicants will receive an email notification containing these confirmed slots. Each applicant is permitted to select only one
slot at a time. In cases where two applicants select the same slot simultaneously, the system will determine which applicant applied first and will send an updated list of available slots to the other applicant. 

### Share slots with candidates 
Click "Interview Scheduling" on the left menu. 
Choose the job ad for the interview. 
Go to "Send Meeting Invite". 
Select the panel member ID. 
(Optional) Select the stage and step. 
Click "View Applicants" to see those who applied. 
Select an applicant. 
Click "Share Slots". 
View confirmed slots booked for this interviewer. 
Select and send timeslots. 
Notification email with slots is sent. 
Candidate selects a slot in their email. 
Confirmed slot appears in the meeting invite section Hindi recruiting add-on. 
Slot status shows as confirmed. 
Send meeting invite 
Once the candidate books a slot, the recruiter can proceed to send the meeting invitation. They can confirm the slot with the applicant and send the meeting invite by selecting an appropriate template for the 
content that needs to be sent to both the candidate and the interviewer. 

### Send meeting invite 

Click on interview scheduling in the left menu. 
Select the job ad for which to schedule an interview. 
Go to the 'send meeting invite' tab. 
Choose the applicant with a confirmed slot status. 
Click Send invite. 
A window will open showing the selected slot. 
Go to the interviews email tab. 
Choose an email template or write the subject and body manually. 
Go to the candidate’s email tab. 
Choose an email template or write the subject and body manually. 
Click send meeting invite. 
This sends an email notification to the candidate and a Teams notification to the interviewer with a meeting invite link. 

### Provide feedback 

Interviewers can now send feedback directly from Microsoft Teams. During or after the interview, a feedback form will be sent to the interviewer's Microsoft Teams. The interviewer can fill out the form and 
submit it. The feedback will be updated in the recruiting add-on, which the recruiter can view to make decisions. 

To provide feedback, follow these steps:
Interviewee receives a feedback notification when the meeting starts. 
Interviewer provides feedback on Microsoft Teams during or after the interview. 
Recruiter views feedback in the recruiting add-on. 
Applicants are moved to the next stage or rejected based on feedback. 

Note: The feedback form will not be triggered if the meeting invitation is sent manually. The feedback form will only be sent when the "send meeting invite" functionality is used in the recruiting add-on or 
interview scheduling. 


