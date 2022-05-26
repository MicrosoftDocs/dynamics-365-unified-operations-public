---
# required metadata

title: Maintenance in self-service environments FAQ
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.
author: rashmansur
ms.date: 05/26/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: rashmim
ms.search.validFrom: 2021-05-13

---

# Maintenance in self-service environments FAQ
Because of the changing nature of technology, the continual appearance of new security threats, and compliance requirements, environments must be updated with all critical security and quality updates. Microsoft has built the framework for performing all maintenance activity, such as operating system patching, deployment of security hotfixes, and deployment of quality updates, during the dark hours of the geographic region where your environment is deployed. To minimize application downtime, upgrades will occur in batches. Therefore, most capacity is always online, and only a subset is upgraded at a time. This approach enables servicing that involves a small window of service degradation instead of complete downtime.

## Infrastructure maintenance in self-service environments
Infrastructure maintenance is the process of updating the environments with the latest security updates and critical hotfixes. Microsoft must complete this process on your environments to ensure security, availability, reliability. This topic provides answers to frequently asked questions about Microsoft planned maintenance in self-service environments.

## What are the types of planned maintenance activities that are performed on an environment?
Some of the common planned maintenance activities performed by Microsoft are:

- Operating system (OS) security updates
- Security hotfixes
- Microsoft quality updates

## What are the planned maintenance windows?
A planned maintenance window is typically during the dark hours of the geographic region that your environment is deployed in. The following list shows the maintenance windows for each geography in Coordinated Universal Time (UTC).

- US, BR, CA: 4:00 AM to 10:00 AM UTC 
- CH, FR, EU, GB: 10:00 PM to 4:00 AM UTC
- AE, NO, ZA: 6:00 PM to 12:00 AM UTC
- CN, JP: 4:00 PM to 10:00 PM UTC
- AU: 1:00 PM to 7:00 PM UTC
- IN: 6:30 PM to 00:30 AM UTC

Please refer here for Geo https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-geographic-regions

Microsoft recommends that you avoid the following activities during the maintenance window:

- Non-retryable batch jobs
- No servicing actions

## What is the schedule for operating system maintenance?

| Month and year | Americas (5:00 AM–8:00 AM UTC) | EMEA (2:00 AM–5:00 AM UTC) | APAC (6:00 PM–9:00 PM UTC) |
|----------|--------------------------|----------------------|----------------------|
| April 2022 | April 24, 2022 | April 23, 2022 | April 23, 2022 |
| May 2022 | May 22, 2022 | May 21, 2022 | May 21, 2022 |
| June 2022 | June 26, 2022 | June 25, 2022 | June 25, 2022 |

> [!NOTE] 
> Effective July 2022 through September 2022, Microsoft will start to roll out updates to the production environment during any weekend, and outside of normal business hours, to help minimize any potential impact on your environments. All sandbox environment will be updated during any night, outside of business hours.
> 
> All the maintenance activity (operating system patching, security hotfixes, and quality updates) will be performed during the dark hour window to provide a near-zero-downtime experience. 

## Can operating system updates be applied in zero downtime?
Yes, Microsoft began to roll out near-zero-downtime infrastructure maintenance in May 2021.

## What does near-zero-downtime maintenance mean?
Customers can continue to operate the system during the maintenance activity. They may experience brief interruptions or disconnects during this window, but will not need to take a full downtime.

## What is the experience during the near-zero-downtime maintenance window?
Upgrades will occur in batches. Therefore, most capacity is always online, and only a subset is upgraded at a time to help eliminate complete downtime. We recommend that customers adopt [priority-based scheduling](../sysadmin/priority-based-batch-scheduling.md) of batch jobs. In this way, they can eliminate the stickiness of batch jobs that are associated with a batch server and enable near-zero-downtime servicing for security patching and quality updates. By design, all Tier 2 and Tier 3 environments might experience approximately 30 minutes of downtime during the servicing.

### Interactive usage
Users who are connected to the environment might experience a brief disconnection of less than 60 seconds a few times during the servicing window. After recovery, users might experience one of the following outcomes:

- The session is gracefully recovered, and the user either goes to the page that they were working on, or is redirected to the root/workspace/home page and receives the following message: "Something went wrong. But we were able to recover your session."
- Session recovery fails, and the user who is working on a details page is redirected to the root/workspace/home page and receives the following message: "Something went wrong, and we were unable to recover your session. You've been redirected."

For example, the user may be working on a sales order creating lines or posting. After the interruption, the user might return to the Sales workspace, but the new order and lines should still be available. We recommend that users go back to the main form and check their work. 

### Batch service
Individual batch servers will not be available for up to 30 minutes.The following activities will occur: 

- Any executing batch jobs will be terminated.
- Jobs that were terminated will be automatically restarted when the batch service recovers. Set the maximum number of retries to zero for any jobs that should not be restarted automatically.
  - Check printing 
  - Statement posting

For more information, see [Can I change the maximum number of retries and the retry interval?](../sysadmin/retryable-batch.md#can-i-change-the-maximum-number-of-retries-and-the-retry-interval) to leran more about batch retry.

### Priority-based scheduling
- If priority-based scheduling is enabled, users will experience reduced Application Object Server (AOS) capacity during the maintenance window. Batch jobs will be served by the available AOS instances. Therefore, there will eventually be no complete downtime during the servicing window.
- If priority-based scheduling isn't enabled, any batch groups that are configured with AOS instances will experience downtime until the associated AOS instance is updated and back in rotation.

> [!NOTE] 
> We are working to reduce the downtime for batch service to be a few minutes. This will require customers to adopt priority-based scheduling of batch jobs.

## Is it possible to reschedule near-zero-downtime operating system maintenance?
To meet regulatory and security compliance standards, Microsoft will perform the planned maintenance during the dark hours of the geographic region where your environment is deployed. The main objective of planned maintenance is to regularly patch environments to remediate security vulnerabilities and apply critical quality updates. If you delay updates, you will put data security, availability, and reliability at risk. 

