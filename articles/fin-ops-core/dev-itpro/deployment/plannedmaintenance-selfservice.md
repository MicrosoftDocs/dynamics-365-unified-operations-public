---
# required metadata

title: Planned maintenance in self-service environments FAQ
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.
author: rashmansur
ms.date: 01/03/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: rashmim
ms.search.validFrom: 2021-05-13

---

# Planned maintenance in self-service environments FAQ
Planned maintenance is any maintenance activity that Microsoft must perform on your environments according to a published schedule. This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.

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

| Month and year | Americas (5:00 AM–8:00 AM UTC) | EMEA (2:00 AM–5:00 AM UTC) | APAC (6:00 PM–9:00 PM UTC) |
|----------|--------------------------|----------------------|----------------------|
| December 2021 | January 9, 2022 | January 8, 2022 | January 8, 2022 |
| January 2022 | January 23, 2022 | January 22, 2022 | January 22, 2022 |
| February 2022 | February 20, 2022 | February 19, 2022 | February 19, 2022 |
| March 2022 | March 20, 2022 | March 19, 2022 | March 19, 2022 |
| April 2022 | April 24, 2022 | April 23, 2022 | April 23, 2022 |
| May 2022 | May 22, 2022 | May 21, 2022 | May 21, 2022 |
| June 2022 | June 26, 2022 | June 25, 2022 | June 25, 2022 |

## How are operating system maintenance updates applied?
This service maintenance is planned outside normal business hours to help minimize any potential impact on your environment. For environments that have users in other parts of the world, we recognize that "outside normal business hours" might affect you differently. We are working hard to improve Microsoft Dynamics 365 and minimize the impact of these maintenance windows in the future. Going forward, infrastructure maintenance schedules will be posted here, and you won't receive future notifications for infrastructure maintenance.

## Can operating system updates be applied in zero downtime?
Yes, Microsoft began to roll out near-zero-downtime infrastructure maintenance in May 2021.

## What does near-zero-downtime maintenance mean?
Customers can continue to operate the system during the maintenance activity. They may experience brief interruptions or disconnects during this window, but will not need to take a full downtime.

## What is the experience during the near-zero-downtime maintenance window?
### Interactive usage
Users connected to the environment may experience a brief (up to 60 seconds) disconnect. On recovery, users may experience one of the following:
- The session recovers gracefully and the user either lands on the form they were working on or is redirected to the root/workspace/home page with the info log message "Something went wrong. But we were able to recover your session."
- The session recovery fails and user working on a details page is redirected to the root/workspace/home page with the info log message "Something went wrong, and we were unable to recover your session. You've been redirected."

For example, the user may be working on a sales order creating lines or posting. After the interruption, the user might return to the Sales workspace, but the new order and lines should still be available. We recommend that users to go back to the main form and check their work. 

### Batch service
Batch service can be unavailable for up to 25 minutes. The following activities will occur: 
- Any executing batch jobs will be terminated.
- Jobs that were terminated will be automatically restarted when the batch service recovers. Set the maximum number of retries to zero for any jobs that should not be restarted automatically.
  - Check printing 
  - Statement posting

> [!NOTE] 
> We are working to reduce the downtime for batch service to be few minutes. This will require customers to adopt priority-based scheduling of batch jobs.

### Known issues
The following issues are known to occur during the near-zero-downtime maintenance window:
- Classic Material Resource Planning: Material Resource Planning jobs are currently not recreated on restart.
  - Ensure Material Resource Planning jobs are not scheduled during the planned maintenance window. This will be fixed in a future Microsoft update.
- Recurring integration: Messages that were in progress at the time of restart will remain stuck in an in-progress state.
  - Review the integration message that were published during the planned maintenance window. If you find any that are in an in-process state, these should be terminated and re-published.

## Is it possible to reschedule near-zero-downtime operating system maintenance?
No. To help with planning, the schedule for infrastructure maintenance will be published in advance every six months. Always refer to the published schedule, and be sure to plan important activities outside the operating system update window.
