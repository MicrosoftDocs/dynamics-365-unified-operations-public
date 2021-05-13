---
# required metadata

title: Planned maintenance in self-service environments FAQ
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.
author: sarvanis
ms.date: 05/13/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sarvanis
ms.search.validFrom: 2021-05-13

---

# Planned maintenance in self-service environments FAQ
Planned maintenance is any maintenance activity that Microsoft needs to perform on your environments either according to a published schedule or Microsoft provides at least 5 days’ notice. This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.

## What are the types of planned maintenance activities that are performed on an environment?
Some of the common planned maintenance activities performed by Microsoft are:

- Operating system (OS) security updates
- Security hotfixes
- Microsoft package updates

## What are the planned maintenance windows?
A planned maintenance window is typically during the dark hours of the geographic region that your environment is deployed in. The following list shows the maintenance windows for each geography in Coordinated Universal Time (UTC).

- Americas: 5:00 AM to 8:00 AM UTC
- EMEA: 2:00 AM to 5:00 AM UTC
- APAC: 6:00 PM to 9:00 PM UTC

## What is the schedule for operating system maintenance?
Month and year | Americas (5:00 AM - 8:00 AM UTC) | EMEA (2:00 AM - 5:00 AM UTC) | APAC (6:00 PM - 9:00 PM UTC)
---------- | -------------------------- | ---------------------- | ----------------------
May 2021 | May 23, 2021 | May 22, 2021 | May 22, 2021
June 2021 | June 20, 2021 | June 19, 2021 | June 19, 2021
July 2021 | July 25, 2021 | July 24, 2021 | July 24, 2021
August 2021 | August 22, 2021 | August 21, 2021 | August 21, 2021
September 2021 | September 26, 2021 | September 25, 2021 | September 25, 2021

## How are operating system maintenance updates applied?
Microsoft sends email notification to customers 5 days ahead of the operating system maintenance, based on the preceding schedule. The email specifies the environments that will be updated and the downtime window. Customers are strongly encouraged to take the maintenance in the given window. In the event that there is an unavoidable reason that customers cannot take the downtime, they can request to reschedule the maintenance. Instructions for requesting to reschedule the maintenance is included in the email.

## Can operating system updates be applied in zero downtime?
Yes, Microsoft is rolling out near-zero downtime operating system maintenance starting May 2021. Customers selected for near-zero downtime operating system updates will be notified through the email notifications sent 5 days prior to the maintenance based on the preceding schedule.

## What does near-zero downtime maintenance mean?
Customers can continue to operate the system during the maintenance activity. They may experience brief interruptions or disconnects during this window, but will not need to take a full downtime.

## What is the experience during the near-zero downtime maintenance window?
### Interactive usage
Users connected to the environment may experience a brief (up to 60 seconds) disconnect. On recovery, users may experience one of the following:
- The session recovers gracefully and the user either lands on the form they were working on or is redirected to the root/workspace/home page with the info log message “Something went wrong. But we were able to recover your session.”
- The session recovery fails and user working on a details page is redirected to the root/workspace/home page with the info log message “Something went wrong, and we were unable to recover your session. You've been redirected.”

For example, the user may be working on a sales order creating lines or posting. After the interruption, the user might return to the Sales workspace, but the new order and lines should still be available. We recommend that users to go back to the main form and check their work. 

### Batch service
Batch service can be unavailable for up to 25 minutes. The following activities will occur: 
- Any executing batch jobs will be terminated.
- Jobs that were teriminated will be automatically restarted when the batch service recovers. Set the maximum number of retries to zero for any jobs that should not be restarted automatically.
  - Check printing 
  - Statement posting

> [!NOTE] 
> We are working to reduce the downtime for batch service to be few minutes. This will require customers to adopt priority-based scheduling of batch jobs.

### Known issues
The following issues are known to occur during the near-zero downtime maintenance window:
- Classic Material Resource Planning: Material Resource Planning jobs are currently not recreated on restart.
  - Ensure Material Resource Planning jobs are not scheduled during the planned maintenance window. This will be fixed in a future Microsoft update.
- Recurring integration: Messages that were in progress at the time of restart will remain stuck in an in-progress state.
  - Review the integration message that were published during the planned maintenance window. If you find any that are in an in-process state, these should be terminated and re-published.

## Is it possible to reschedule near-zero downtime operating system maintenance?
No. In order to help with planning, the schedule for operating system maintenance will be published in advance every 6 months. Always refer to the published schedule, and be sure to plan important activities outside the operating system update window.
