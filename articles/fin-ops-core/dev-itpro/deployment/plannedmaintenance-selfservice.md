---
# required metadata

title: Planned maintenance in self-service environments
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance in self-service environments.
author: sarvanis
manager: AnnBe
ms.date: 05/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2021-05-12
ms.dyn365.ops.version: AX 7.0.0

---
# What is planned maintenance?
Planned maintenance is any maintenance activity that Microsoft needs to perform on your environments either according to a published schedule or provides at least 5 days notice.

# What are the types of planned maintenance activities that are performed on an environment?
Some of the common planned maintenance activities performed by Microsoft are
- Operating System (OS) security updates
- Security hotfixes
- Microsoft package updates

# What are the planned maintenance windows?
The planned maintenance window is typically in the dark hours of the geographic region your environment is deployed in. The following list shows the maintenance windows for each geography in Coordinated Universal Time (UTC)
- Americas: 5 AM to 8 AM UTC
- EMEA: 2 AM to 5 AM UTC
- APAC: 6 PM to 9 PM UTC

# What is the schedule specifically for OS maintenance?
Month/Year | Americas (5 AM - 8 AM UTC) | EMEA (2 AM - 5 AM UTC) | APAC (6 PM - 9 PM UTC)
---------- | -------------------------- | ---------------------- | ----------------------
May 2021 | 05-23-2021 | 05-22-2021 | 05-22-2021
June 2021 | 06-20-2021 | 06-19-2021 | 06-19-2021
July 2021 | 07-25-2021 | 07-24-2021 | 07-24-2021
August 2021 | 08-22-2021 | 08-21-2021 | 08-21-2021
September 2021 | 09-26-2021 | 09-25-2021 | 09-25-2021

# How are OS maintenance updates applied?
Microsoft sends email notification to customers 5 days ahead of the OS maintenance, per above schedule. The email specifies the environments that will be updated and the downtime window. Customers are strongly encouraged to take the maintenance in the given window. In the event there is an unavoidable reason due to which customers cannot take the downtime, they can request to reschedule the maintenance. Instructions for requesting reschedule is included in the email.

# Can OS updates be applied in zero downtime?
Yes, Microsoft is rolling out near-zero downtime (nZDT) OS maintenance starting May 2021. Customers selected for near zero downtime OS upates will be notified through the email notifications sent 5 days prior to the maintenance per above schedule. 

# What does near-zero downtime (nZDT) maintenance mean?
Customers can continue to operate the system during the maintenance activity. The may experience brief interruptions or disconnects during this window, but will not need to take a full downtime.

# What is the experience during the nZDT maintenance window?
### Interactive usage
Users connected to the environment may experience a brief (up to 60 seconds) disconnect.

On recovery, users may experience one of the below.
- The session recovers gracefully  user either lands on the form he/she was working on or is redirected to the root/workspace/home page with info log message “Something went wrong. But we were able to recover your session”. 
- The session recovery fails  user working on a details page is redirected to the root/workspace/home page with the info log message “Something went wrong, and we were unable to recover your session. You've been redirected”

e.g. : User may be on a sales order creating lines or posting. After the interruption, user may land in home of Sales workspace, but order and lines should still be available is the system.(We recommend users to go back to main form and check).

### Batch
Batch service can be unavailable for up to 25 minutes.
- Any executing batch jobs will be terminated.
- Jobs that were killed will be automatically restarted when the batch service recovers. Set the max number of retries to zero for any jobs that should not be restarted automatically.
  - Check Printing 
  - Statement Posting

* We are working on reducing the downtime for Batch service to be few minutes. This will require customers to adopt Priority Based Scheduling of batch jobs.

### Known issues
- Classic MRP: MRP jobs are currently not recreated on restart.
  - Short-term : Ensure MRP jobs are not scheduled during the planned maintenance window.
  - Long-term : This will be fixed in a future Microsoft update.
- Recurring integration:  Messages that were in progress at the time of restart, will remain stuck in in-progress state.
  - Short-term : Review the integration message that were published during the planned maintenance window. If you find any that are hung with in-process status. This should be terminated and re-published.

# Is it possible to reschedule a nZDT OS maintenance?
No. In order to help with planning, the schedule of OS maintenance will be published in advance every 6 months. Please use the published schedule and plan important activities outside the OS update window.
© 2021 GitHub, Inc.
