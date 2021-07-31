---
# required metadata

title: Data mart resets FAQ
description: This topic provides answers to some frequently asked questions about data mart resets.
author: jinniew
ms.date: 07/16/2021
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

- The application database was restored.
- You opened a support ticket, and a Support engineer instructed you to reset the data mart as part of a troubleshooting step.
 
> [!NOTE]
> The process of resetting a data mart is affected by the number of general ledger and budget transactions in your database. Depending on the number of transactions in your system, a data mart reset can be completed in as little as 15 minutes, or it can take up to four hours. However, if your reset takes longer than four hours, we recommend that you contact Support.
 
## When is a data mart reset inappropriate?

Here are some of the circumstances where we don't recommend that you reset the data mart:

- You're experiencing performance issues that are associated with data synchronization.
- You have a recurring reset pattern for any of the following reasons:

    - **Missing data** – If you notice that data is missing, open a support ticket with Microsoft to review your report format and possible data synchronization issues.
    - **Stuck integration state**
    - **Stale records** – Stale records by themselves don't necessarily justify a data mart reset. If you have a large data set, the reset process will take some time to run but is unlikely to lead to any improvement.

## If I reset the data mart, will I lose reports that I've already designed?

No. Your reports are stored in SQL tables that aren't affected by a data mart reset. If you're concerned about losing reports that you've designed, you can back up the designs that you don't want to lose. To back up designs, open Report Designer, and go to **Company \> Companies \> Building Blocks \> Export**.
 
## Do all users have to exit the system before I can reset the data mart?

No. Users can continue to work in the system during a data mart reset. However, until the reset is completed, users won't be able to access any reports that were created by using Financial Reporter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
