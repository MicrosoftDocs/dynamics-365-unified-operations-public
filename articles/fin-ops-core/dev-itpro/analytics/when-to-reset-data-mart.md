---
# required metadata

title: Data mart resets FAQ
description: This topic provides answers to some frequently asked questions about data mart resets.
author: jinniew
ms.date: 03/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2021-05-06
ms.dyn365.ops.version: 10.0.15

---

# Data mart resets FAQ

This topic provides answers to some frequently asked questions about data mart resets. A reset of the data mart can be a time-consuming process and, depending on the circumstances, might not be the solution that is required. Therefore, this topic includes information about circumstances where a data mart reset might help and also circumstances where it's unlikely to help.

## What is a data mart reset?

A data mart reset will disable the integration tasks, delete all the data mart data, and then re-enable integration.

To ensure that old data isn't inserted, a data mart reset can be started only after existing tasks are completed. If you try to reset the data mart before all tasks are completed, you might receive a message such as, "The data mart reset was unable to be processed because of an active task. Please try again later."

## When do I have to do a data mart reset?

If one or more of the following statements apply to your situation, your organization can benefit from a data mart reset:

- **The application database was restored**
- **You opened a support ticket** - A support engineer instructed you to reset the data mart as part of a troubleshooting step.
- **Large percentage of stale records** - Stale records by themselves don't necessarily justify a data mart reset. High percentages of stale data can degrade the overall report generation and integration performance, and incur extra database space usage. We recommend that you complete a datamart reset to remove the stale data when there is more than 80% stale data in the data mart.
 
> [!NOTE]
> The process of resetting a data mart is affected by the number of general ledger and budget transactions in your database. Depending on the number of transactions in your system, a data mart reset can be completed in as little as 15 minutes, or it can take up to four hours. However, if your reset takes longer than four hours, we recommend that you contact Support.
 
## When is a data mart reset inappropriate?

Here are some of the circumstances where we don't recommend that you reset the data mart:

- You're experiencing data integration performance issues.
- Your Financial Reporter integration isn't enabled. 

    - This means that General Ledger data is no longer being synchronized to your Financial Reporting datamart. Your Financial Reporter may not be getting up-to-date numbers for your financial reports. This typically occurs if you have not use Financial Reporter for a long time.
    - You will be prompted to enable integration by resetting the data mart. You can proceed by selecting **Yes**. You may also choose to reset the data mart at a later time. After integration is enabled, your general ledger data is synchronized in Financial Reporter again. 
- You have a recurring reset pattern for any of the following reasons:

    - **Missing or unexpected data in the report** – If you notice that data is missing, open a support ticket with Microsoft to review your report format and possible data synchronization issues.
    - **Stuck integration state** - If you notice the integration status is stuck in running, this may be due to a large volume of transactions in the system. This state will resolve itself. However, if you notice the intregration status is stuck for more than four hours, open open a support ticket with Microsoft. 
   
## If I reset the data mart, will I lose reports that I've already designed?

No. Your reports are stored in SQL tables that aren't affected by a data mart reset. If you're concerned about losing reports that you've designed, you can back up the designs that you don't want to lose. To back up designs, open Report Designer, and go to **Company \> Companies \> Building Blocks \> Export**.
 
## Do all users have to exit the system before I can reset the data mart?

No. Users can continue to work in the system during a data mart reset. However, until the reset is completed, users won't be able to access any reports that were created by using Financial Reporter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
