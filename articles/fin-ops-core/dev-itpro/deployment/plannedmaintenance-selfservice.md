---
# required metadata

title: Maintenance in self-service environments FAQ
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

# Upcoming changes to FnO servicing (OS patching, quality updates)
Due to the changing nature of technology and the continual appearance of new security threats, compliance requirements it is necessary to update the environment with all critical security and quality updates. Microsoft has built the framework to perform all maintenance activity (OS patching, security hotfixes, quality updates) during the dark hours of the geographic region that your environment is deployed. To minimize the application downtime, upgrades will take place in batches, most capacity is always online with only a subset upgrading at a time. This enables servicing with a small window of service degradation instead of complete downtime.

## Maintenance in self-service environments FAQ
Infrastructure maintenance is process of updating the environmnets with latest security updates, critical hotfixes that Microsoft must perform on your environments to ensure security, availability, reliability. This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.

> [!NOTE] 
> Effective July 22 – Sep 22, Microsoft will start rolling out updates to the environment during any weekend and outside normal business hours to help minimize any potential impact on your environments. All the maintenance activity (OS patching, Security hotfixes, quality updates) will be performed during the dark hour window in near zero downtime experience. As environments are onboarded to the new process prior notification will be sent to the message center.

## What are the types of planned maintenance activities that are performed on an environment?
Some of the common planned maintenance activities performed by Microsoft are:

- Operating system (OS) security updates
- Security hotfixes
- Microsoft quality updates

## What are the planned maintenance windows?
A planned maintenance window is typically during the dark hours of the geographic region that your environment is deployed in. The following list shows the maintenance windows for each geography in Coordinated Universal Time (UTC).

- Americas: 5:00 AM to 8:00 AM UTC
- EMEA: 2:00 AM to 5:00 AM UTC
- APAC: 6:00 PM to 9:00 PM UTC

Microsoft recommends avoiding the following activities during the maintenance window.
- Non-Retry-able batch jobs
- No servicing actions

## What is the schedule for operating system maintenance?

| Month and year | Americas (5:00 AM–8:00 AM UTC) | EMEA (2:00 AM–5:00 AM UTC) | APAC (6:00 PM–9:00 PM UTC) |
|----------|--------------------------|----------------------|----------------------|
| April 2022 | April 24, 2022 | April 23, 2022 | April 23, 2022 |
| May 2022 | May 22, 2022 | May 21, 2022 | May 21, 2022 |
| June 2022 | June 26, 2022 | June 25, 2022 | June 25, 2022 |

## How are operating system maintenance updates applied?
This service maintenance is planned outside normal business hours to help minimize any potential impact on your environment. For environments that have users in other parts of the world, we recognize that "outside normal business hours" might affect you differently. We are working hard to improve Microsoft Dynamics 365 and minimize the impact of these maintenance windows in the future. Going forward, infrastructure maintenance schedules will be posted here, and you won't receive future notifications for infrastructure maintenance.

## How are quality updates applied ?
TBD

## Can operating system updates be applied in zero downtime?
Yes, Microsoft began to roll out near-zero-downtime infrastructure maintenance in May 2021.

## What does near-zero-downtime maintenance mean?
Customers can continue to operate the system during the maintenance activity. They may experience brief interruptions or disconnects during this window, but will not need to take a full downtime.

## What is the experience during the near-zero-downtime maintenance window?
upgrades will take place in batches, most capacity is always online with only a subset upgrading at a time that helps eliminate complete downtime. We recommend customers adopt priority-based scheduling of batch jobs to eliminate the stickiness of batch jobs associated with a batch server and enable nZDT (near Zero Down Time) servicing security patching & quality updates. All tier2/3 environments by design may experience approx. 30 mins of downtime during the servicing.

### Interactive usage
Users connected to the environment may experience a brief disconnect of less than 60 seconds a few times during the servicing window. On recovery, users may experience one of the following:
- The session recovers gracefully and the user either lands on the form they were working on or is redirected to the root/workspace/home page with the info log message "Something went wrong. But we were able to recover your session."
- The session recovery fails and the user working on a details page is redirected to the root/workspace/home page with the info log message "Something went wrong, and we were unable to recover your session. You've been redirected."

For example, the user may be working on a sales order creating lines or posting. After the interruption, the user might return to the Sales workspace, but the new order and lines should still be available. We recommend that users to go back to the main form and check their work. 

### Batch service
Batch service can be unavailable for up to 25 minutes. The following activities will occur: 
- Any executing batch jobs will be terminated.
- Jobs that were terminated will be automatically restarted when the batch service recovers. Set the maximum number of retries to zero for any jobs that should not be restarted automatically.
  - Check printing 
  - Statement posting

### Priority-based scheduling:
- If PBS is enabled, then users will experience reduced AOS capacity during the maintenance window and batch jobs will be served with available AOS servers. So eventually there will be no complete downtime during the servicing window.
- If PBS is not enabled, then any batch groups configured with AOS servers will experience downtime until the associated AOS server is updated and back in rotation.


> [!NOTE] 
> We are working to reduce the downtime for batch service to be few minutes. This will require customers to adopt priority-based scheduling of batch jobs.

### Known issues
The following issues are known to occur during the near-zero-downtime maintenance window:
- Classic Material Resource Planning: Material Resource Planning jobs are currently not recreated on restart.
  - Ensure Material Resource Planning jobs are not scheduled during the planned maintenance window. This will be fixed in a future Microsoft update.
- Recurring integration: Messages that were in progress at the time of restart will remain stuck in an in-progress state.
  - Review the integration message that were published during the planned maintenance window. If you find any that are in an in-process state, these should be terminated and re-published.

## Is it possible to reschedule near-zero-downtime operating system maintenance?
In order to meet regulatory and security compliance standards, Microsoft will perform the planned maintenance during the dark hours of the geographic region that your environment is deployed. The main objective of planned maintenance is to patch environments regularly to remediate security vulnerabilities, critical quality updates and delaying updates will potentially risk data security, availability & reliability. 

