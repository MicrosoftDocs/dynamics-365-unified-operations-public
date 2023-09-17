---
# required metadata

title: Maintenance in self-service environments FAQ
description: This article provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.
author: matapg007
ms.date: 09/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2021-05-13

---

# Maintenance in self-service environments FAQ
Because of the changing nature of technology, the continual appearance of new security threats, and compliance requirements, environments must be updated with all critical security and quality updates. Microsoft has built the framework for performing all maintenance activity, such as operating system patching, deployment of security hotfixes, and deployment of quality updates, during the dark hours of the geographic region where your environment is deployed. To minimize application downtime, upgrades will occur in batches. Therefore, most capacity is always online, and only a subset is upgraded at a time. This approach enables servicing that involves a small window of service degradation instead of complete downtime.

## Infrastructure maintenance in self-service environments
Infrastructure maintenance is the process of updating the environments with the latest security updates and critical hotfixes. Microsoft must complete this process on your environments to ensure security, availability, reliability. This article provides answers to frequently asked questions about Microsoft planned maintenance in self-service environments.

## What are the types of planned maintenance activities that are performed on an environment?
Some of the common planned maintenance activities performed by Microsoft are:

- Operating system (OS) security updates
- Security hotfixes
- Microsoft quality updates

## <a name="windows"></a>What are the planned maintenance windows?
A planned maintenance window is typically during the dark hours of the geographic region that your environment is deployed in. The following table lists the maintenance windows for each geography in Coordinated Universal Time (UTC).

|Geo |Start time | Days |Maintenance window|
|----|--------------------|---------|--------|
|Australia |13:00 UTC|Friday, Saturday|Six hours|
|Asia   |16:00 UTC|Friday, Saturday|Six hours|
|Brazil |04:00 UTC |Saturday, Sunday|Six hours|
|Canada	|04:00 UTC |Saturday, Sunday|Six hours|
|China	|16:00 UTC|Friday, Saturday|Six hours|
|Europe	|22:00 UTC|Friday, Saturday|Six hours|
|France	|16:00 UTC|Friday, Saturday|Six hours|
|India	|18:30 UTC|Friday, Saturday|Six hours|
|Japan	|16:00 UTC|Friday, Saturday|Six hours|
|Norway	|22:00 UTC|Friday, Saturday|Six hours|
|South Africa	|22:00 UTC|Friday, Saturday|Six hours|
|Switzerland	|22:00 UTC|Friday, Saturday|Six hours|
|United Arab Emirates	|18:00 UTC|Friday, Saturday|Six hours|
|United Kingdom	|22:00 UTC|Friday, Saturday|Six hours|
|United States	|04:00 UTC |Saturday, Sunday|Six hours|

## What is the schedule for proactive quality updates?

For information on the upcoming proactive quality update schedule, see the [Release schedule for proactive quality updates](../../fin-ops/get-started/quality-updates-schedule.md).

> [!NOTE] 
> Effective August 2022 through October 2022, Microsoft will start to roll out updates to the production environment during any weekend, and outside of normal business hours, to help minimize any potential impact on your environments. All sandbox environments will be updated during any night, outside of business hours.
> 
> All the maintenance activity (system updates, security hotfixes, and quality updates) will be performed during the dark-hour window to provide a near-zero-downtime experience.

## What does near-zero-downtime maintenance mean?
Customers can continue to operate the system during the maintenance activity. They may experience brief interruptions or disconnects during this window, but won't need to take a full downtime.

## What is the experience during the near-zero-downtime maintenance window?
Upgrades will occur in batches. Therefore, most capacity is always online, and only a subset is upgraded at a time to help eliminate complete downtime. We recommend that customers adopt [priority-based scheduling](../sysadmin/priority-based-batch-scheduling.md) of batch jobs. Priority-based scheduling eliminates the stickiness of batch jobs that are associated with a batch server and enable near-zero-downtime servicing for security patching and quality updates. By design, all Tier 2 and Tier 3 environments might experience approximately 30 minutes of downtime during the servicing or maintenance operations.

### Interactive usage
Users who are connected to the environment might experience a brief disconnection of less than 60 seconds a few times during the servicing window. After recovery, users might experience one of the following outcomes:

- The session recovers gracefully, and the user either goes to the page that they were working on, or redirects to the root/workspace/home page and receives the following message: "Something went wrong. But we were able to recover your session."
- Session recovery fails, and the user who is working on a details page is redirected to the root/workspace/home page and receives the following message: "Something went wrong, and we were unable to recover your session. You've been redirected."

For example, the user may be working on a sales order creating lines or posting. After the interruption, the user might return to the Sales workspace, but the new order and lines should still be available. We recommend that users go back to the main form and check their work. 

### Batch service
Individual batch servers won't be available for up to 30 minutes. The following activities will occur: 

- Any executing batch jobs will be terminated.
- Jobs that were terminated will be automatically restarted when the batch service recovers. Set the maximum number of retries to zero for any jobs that shouldn't be restarted automatically.
  - Check printing 
  - Statement posting


For more information, see [Retry the batch job task, regardless of the error type](../sysadmin/retryable-batch.md#retry-the-batch-job-task-regardless-of-the-error-type) to learn more about batch retry.

### Priority-based scheduling
- If priority-based scheduling is enabled, users will experience reduced Application Object Server (AOS) capacity during the maintenance window. Batch jobs are served by the available AOS instances. Therefore, there will eventually be no complete downtime during the servicing window.
- If priority-based scheduling isn't enabled, any batch groups that are configured with AOS instances will experience downtime until the associated AOS instance is updated and back in rotation.

> [!NOTE] 
> We are working to reduce the downtime for batch service to a few minutes. This will require customers to adopt priority-based scheduling of batch jobs.

## Is it possible to reschedule near-zero-downtime operating system maintenance?
No. To meet regulatory and security compliance standards, Microsoft will perform the planned maintenance during the dark hours of the geographic region where your environment is deployed. The main objective of planned maintenance is to regularly patch environments to remediate security vulnerabilities and apply critical quality updates. If you delay updates, you'll put data security, availability, and reliability at risk. 

