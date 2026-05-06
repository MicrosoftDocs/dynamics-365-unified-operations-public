---
title: Collections process automation
description: Learn about the process of setting up collections process strategies that automatically identify customer invoices that require email reminders.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/06/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-26 
ms.search.form:  CustomerCollectionManagerWorkspace
ms.dyn365.ops.version: 10.0.13 
---

# Collections process automation

[!include [banner](../includes/banner.md)]

This article describes how to set up collections process strategies that automatically identify customer invoices that require an email reminder, collection activity (such as a phone call), or a collection letter to send to the customer.

Organizations often spend significant time researching aged balance reports, customer accounts, and open invoices to learn which customers to contact about an open invoice or account balance. This research takes time away from a collection agent’s time spent communicating with customers to collect past due balances or resolving invoice disputes. Collections process automation lets you set up a strategy-based approach to your collection process. This approach helps you apply collection activities consistently by providing customized email reminders or programmed process for sending collection letters.

## Collections process setup

Use the **Collections process setup** page (**Credit and collections > Setup > Collections process setup**) to create an automated collections process that schedules activities, sends email messages, and creates and posts customer collection letters. The process steps are based on the leading or oldest open invoice. Each step uses this invoice to determine what communication or activity should take place with a specific customer.  

Collections teams typically send out an early notice related to each outstanding invoice so that a customer is notified when an invoice is about to become due. Set the **Pre-dunning** selection to allow one step in each process hierarchy to be acted on for every invoice as the invoice timing reaches that step.

### Process hierarchy

You can assign each customer pool to only one process hierarchy. The hierarchy rank of this step identifies which process takes precedence if a customer is included in more than one pool that has a process hierarchy assigned. The pool ID determines which customers are assigned to the process. You can assign each hierarchy to only one process automation.

Set the quiet days to ensure that a customer doesn't get contacted too frequently by the automated process. For example, if you set the quiet days to two, the automated process doesn't contact a customer for at least two days, even if the original leading invoice is settled in full.

To exclude customers from the process automation if the customer aging balance or invoice amount is less than a defined value, select **Customer aging balance less than** or **Invoice amount less than** in the **Exclude from process** field and enter the amount value.

Mark **Use prediction** to create collections activities using Customer payment predictions. The activities created will use the Activity template from **Payment predictions** on the **Accounts receivable parameters** page, **Collections process automation** tab.

Mark **Use track step** to ensure that invoices go through all steps of the automation. Set this to **Yes** if you want invoices to start at the first step in the process. For example, if the **Collections status** field was set to **Disputed**, but later set to **Resolved**, collections process automation starts at the first step on the **Process details** tab of the collections process setup. Select **No**, to start invoices with the activity that most closely matches the date. This checkbox is available when the **Collections process automation track step enhancement** feature is enabled in Dynamics 365 Finance release 10.0.43 and later.

This checkbox can't be disabled. After this feature is enabled, each open invoice is assigned the last step that was run according to the process automation history. If the process automation history has been removed, any open invoice starts with the first step in the process automation setup details.

### Process details

Select **New** to add a new process detail to the hierarchy. The **Description** is used to identify the purpose or name of the step in the hierarchy. Select the **Action type** to define the step that will create an activity, send an email, or create a collection letter.

- The **Business document** defines the template used to create the action type. This document can be an activity template, an email template, or a collection letter sent to each customer. Collections process automation only creates collection letters per customer, regardless of how other collections parameters are set.
- **When** defines the process step that will occur before or after the leading (oldest) invoice due date, and is used together with the number displayed in the **Days in relation to the invoice due date** column.
- Mark the **Pre-dunning** option to create an action for every invoice in one step in a process hierarchy. Predunning actions are typically an early notice related to outstanding invoices so a customer can be notified when an invoice is about to become due. Predunning can only be marked for one activity per hierarchy. Only one step in a hierarchy can be designated for predunning actions, and this step must be either an activity or an email. When you select an email action type, the recipient is used to define whether the email message is sent to a customer, sales group, or collections agent contact.
- The value in the **Business purpose contact** field determines which contact from that customer's account receives the communication.

### Business document details

The business document details vary based on the action type that you select in the process details. When the action type is an activity, the activity template details appear. These details include the activity template name, the type of activity that the process creates, the purpose of the activity, the number of days scheduled to complete the activity, and the details of the activity. This activity then links to the leading invoice that tells the recipient of the action that’s needed to complete the activity.

If the action type is an email in the process details, this section contains two FastTabs. Use the first FastTab to define the template ID, email description, default language, the user name that you assign to email messages that are automatically sent, and the associated sender's email address. The second FastTab allows you to create the body of the email after you save the values in the **Language** and **Subject** fields by selecting **Edit**. This action opens a window that allows HTML content to be uploaded.

> [!Note]
> You can save an Outlook email message that contains the body text of the communication in HTML format. You can then upload the message content to implement the template. <br> <br> If you select the action type of collection letter, the setup page doesn't include a business document detail section.

Use the **Collections process history** button to view the recent history for the selected process hierarchy.

Select the **Collections process assignment** action to view customers assigned to a collections process. Use **Preview customer assignment** to view the hierarchy that a specific customer is assigned. Use **Preview process assignment** to preview the customers that the process assigns to a hierarchy when it runs. Select **Manual assignment** to view customers that you manually assigned to a process or select customers to assign to a process.

Select the **Process simulation** action to preview the actions that the process creates if the selected process automation runs.

Beginning in Dynamics 365 Finance version 10.0.44, the **Include project and General journal invoices in Collections process automation** feature is introduced.  

When you enable this feature, you get access to new parameters in the strategy grid. Select the checkboxes based on the type of invoices you want to be part of the automation process.

A new **Voucher** column is introduced on the **Collections process history** page to enhance the tracking and management of financial transactions. This column allows users to view associated voucher details for each entry, providing greater transparency and ease of identification.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
