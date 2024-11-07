---
title: Data mart resets FAQ
description: Access answers to some frequently asked questions about data mart resets, including questions about when and when not to perform a data mart reset.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom: 
  - bap-template
ms.date: 08/04/2024
ms.reviewer: johnmichalak

---

# Data mart resets FAQ

This article provides answers to some frequently asked questions about data mart resets. A reset of the data mart can be a time-consuming process and, depending on the circumstances, might not be the solution that is required. Therefore, this article includes information about circumstances where a data mart reset might help and also circumstances where it's unlikely to help.

## What is a data mart reset?

A data mart reset disables the integration tasks, delete all the data mart data, and then re-enables the integration.

To ensure that old data isn't inserted, a data mart reset can be started only after existing tasks are completed. If you try to reset the data mart before all tasks are completed, you might receive a message such as, "The data mart reset was unable to be processed because of an active task. Try again later."

Executing a data mart reset is a significant action and should almost never be done. There are, however, a few special cases where it may be required. If you encounter a situation where a reset seems necessary, it is highly recommended to contact support first. This allows us to properly investigate any underlying product issues that might be prompting the need for a reset. By doing so, we can ensure that we are addressing the root cause rather than applying a temporary fix.

## When do I have to do a data mart reset?

If one or more of the following statements apply to your situation, your organization can benefit from a data mart reset:

- **You opened a support ticket** - A support engineer instructed you to reset the data mart as part of a troubleshooting step.
- **•	Your operations database was restored without your financial reporting database**
   
> [!NOTE]
> The process of resetting a data mart is affected by the number of general ledger and budget transactions in your database. Depending on the number of transactions in your system, a data mart reset can be completed in as little as 15 minutes, or it can take up to four hours. The reset dialog will give you a rough estimate. However, If your reset takes longer than the estimated time given in the reset dialog, we recommend that you contact Support.
 
## When is a data mart reset inappropriate?

Here are some of the circumstances where we don't recommend that you reset the data mart:

- You're experiencing data integration performance issues.
- You have a recurring reset pattern for any of the following reasons:

    - **Missing or unexpected data in the report** – If you notice that data is missing, open a support ticket with Microsoft to review your report format and possible data synchronization issues.
    - **Stuck integration state** - If you notice the integration status is stuck in running, this may be due to a large volume of transactions. This state resolves itself. However, if you notice the integration status is stuck for more than four hours, open a support ticket with Microsoft. 
   
## If I reset the data mart, do I lose reports that I've already designed?

No. Your reports are stored in SQL tables that aren't affected by a data mart reset. If you're concerned about losing reports that you've designed, you can back up the designs that you don't want to lose. To back up designs, open Report Designer, and go to **Company \> Companies \> Building Blocks \> Export**.
 
## Do all users have to exit the system before I can reset the data mart?

No. Users can continue to work in the system during a data mart reset. However, until the reset is completed, users won't be able to access any reports that were created by using Financial Reporter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
