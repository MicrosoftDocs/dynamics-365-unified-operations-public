---
title: Data mart resets FAQ
description: Access answers to some frequently asked questions about data mart resets, including questions about when and when not to perform a data mart reset.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom: 
  - bap-template
ms.date: 03/12/2026
ms.reviewer: johnmichalak

---

# Data mart resets FAQ

This article provides answers to some frequently asked questions about data mart resets. Resetting the data mart can be a time-consuming process. Depending on your circumstances, it might not be the solution you need. Therefore, this article includes information about circumstances where resetting the data mart might help and also circumstances where it's unlikely to help.

## What is a data mart reset?

When you reset the data mart, you disable the integration tasks, delete all the data mart data, and then re-enable the integration.

To ensure that old data isn't inserted, you can start a data mart reset only after existing tasks are completed. If you try to reset the data mart before all tasks are completed, you might receive a message such as, "The data mart reset was unable to be processed because of an active task. Try again later."

> [!IMPORTANT]
> Executing a data mart reset is a significant action and you should almost never do it. There are a few special cases where it might be required. If you encounter a situation where a reset seems necessary, contact support first to investigate any underlying product issues and address the root cause.

## When do I have to do a data mart reset?

If one or more of the following statements apply to your situation, your organization can benefit from a data mart reset:

- **You opened a support ticket** - A support engineer instructed you to reset the data mart as part of a troubleshooting step.
- **You restored your operations database without restoring your financial reporting database**

> [!NOTE]
> The process of resetting a data mart is affected by the number of general ledger and budget transactions in your database. Depending on the number of transactions in your system, you can complete a data mart reset in as little as 15 minutes, or it can take up to four hours. The reset dialog provides a rough estimate. If the reset takes longer than the estimated time given in the reset dialog, contact support.

## When is a data mart reset inappropriate?

Don't reset the data mart in the following circumstances:

- You're experiencing data integration performance problems.
- You have a recurring reset pattern for any of the following reasons:

  - **Missing or unexpected data in the report** – If you notice that data is missing, open a support ticket with Microsoft to review your report format and possible data synchronization problems.
  - **Stuck integration state** - If you notice the integration status is stuck in running, this condition might be due to a large volume of transactions. This state resolves itself. However, if you notice the integration status is stuck for more than four hours, open a support ticket with Microsoft.

## If I reset the data mart, do I lose reports that I already designed?

No. Your reports are stored in SQL tables that aren't affected by a data mart reset. If you're concerned about losing reports that you designed, you can back up the designs that you don't want to lose. To back up designs, open Report Designer, and go to **Company \> Companies \> Building Blocks \> Export**.

## Do all users have to exit the system before I can reset the data mart?

No. Users can continue to work in the system during a data mart reset. However, until the reset is completed, users can't access any reports that you created by using Financial Reporter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
