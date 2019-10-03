---
# required metadata

title: Expense reports reimagined
description: This topic provides information about the redesigned and reimagined experience for expense report entry in Microsoft Dynamics 365 Finance. The new experience simplifies the process of completing expense reports and decreases the time that is required.
author: ryansandness
manager: AnnBe
ms.date: 06/14/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: ryansand
ms.search.validFrom: 2019-6-30 
ms.dyn365.ops.version: 10.0.3 
---

# Expense reports reimagined

[!include[banner](../includes/banner.md)]

Expense report entry has been redesigned to simplify the process of completing expense reports and decrease the time that is required. Here are the major components of the new expense experience:

- A new expense management workspace that lets you access your delegate's expenses.
- A new receipt matching experience to better show header-level receipts and simplify the process of attaching receipts to expense lines.
- A new read-only grid that lets you view many more expense lines and additional columns of data. You can now see all itemized and split lines, together with their parent expenses.
- A simplified pane for editing expenses.
- Redesigned error, warning, and policy messages to help guarantee that you have the correct context to understand what the issue is and how to resolve it. Microsoft has removed many messages that appeared before users had an opportunity to complete their tasks and address the issues, such as the incomplete itemization message.
- A new page for specifying which fields are required by your organization, which fields are optional, and which fields should not be captured. This page will help reduce the number of fields that users must to set.
- A new look and feel for expense reports, so that the reports no longer seem as though they were designed for accounting personas.

To turn on the new experience, use the **Feature management** workspace to turn on the **Expense reports re-imagined** feature. When you turn on this feature, the following actions occur:

- The existing expense workspace is replaced with the new workspace.
- A new menu item for expense field visibility is added.
- No existing menu items for expense reports (the existing page) or expense report fields are removed.
- Workflows and any approvals still take you to the existing expense reports page.

## Getting started video for new users

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Y7gO]

The [Expense experience in Dynamics 365 for Finance and Operations](https://youtu.be/Ocy-MsTvEE0) video (shown above) is included in the [Finance and Operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## New features

| New feature | Description |
|---|----|
| Expense field visibility | A new setup page lets you specify which fields should be disabled for an organization, which fields should be required, and which fields are recommended. |
| Required fields | New simple configuration lets you make some fields required without having to use the policy framework. |
| Optional fields | A second page for optional fields is added. In this way, employees won't feel as if they must set the fields, but the fields are still easily accessible. |
| Add unattached receipts | The ability to add unattached receipts to expense report is more visible from the workspace and on the expense report. |
| Improved messaging | There is better visibility into expense lines that have warnings or errors. |
| Reduction in messages in the message bar| The number of Infolog messages was decreased, and an effort was made to prevent duplicate messages from appearing in many cases. |
| Grouped together common actions | The interface was cleaned up with the addition of a new actions button for most of the common line-level actions and the addition of an ellipsis button (...) for header and other less frequent actions. |
| New workspace to increase visibility | A new workspace unifies features and links that let users move to different areas. |
| Add existing expenses and receipts during expense creation | When you create expense reports, you can add all or selected expenses and receipts. |
| Exchange rate calculator | An exchange rate calculator is added that lets you calculate the exchange rate for out-of-pocket multicurrency transactions. |
| Save and add new expense lines | **Save** and **New** buttons are available when new expenses are entered, to help you quickly enter expense lines. |
| Better visibility into split and itemized lines | Itemized and split lines are added directly to the list of expenses, to increase visibility and help you easily determine whether there are policy errors or other errors. |
| Show receipts during itemization | Receipts can be shown during itemization. |

The initial release is focused on expense entry scenarios. Any expense report review or approval scenario will continue to use the existing expense entry page.

The following features are present on the existing page but aren't yet present on the new page. These features will be reintroduced over the next several releases:

- Approvals
- Accounts payable approvals and the ability to edit the accounting
- Multiple entry points
- Travel requisition integration
- Data entity for expense field visibility
- Entry for per-diem expenses
- Line-level workflow
- Interim approver support
- Advanced itemization
