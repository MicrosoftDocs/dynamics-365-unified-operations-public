---
# required metadata

title: Collections process automation
description: This article describes the process of setting up collections process strategies that automatically identify customer invoices that require an email reminder, collection activity, or a collection letter to be sent to the customer. 
author: JodiChristiansen
ms.date: 03/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  CustomerCollectionManagerWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-26 
ms.dyn365.ops.version: 10.0.13 
---

# Collections process automation

[!include [banner](../includes/banner.md)]

This article describes the process of setting up collections process strategies that automatically identify customer invoices that require an email reminder, collection activity (such as a phone call), or a collection letter to be sent to the customer. 

Organizations often spend significant time researching aged balance reports, customer accounts, and open invoices to learn which customers should be contacted about an open invoice or account balance. This research takes times away from a collection agent’s time spent communicating with customers to collect past due balances or resolving invoice disputes. Collections process automation lets you set up a strategy-based approach to your collection process. This helps you apply collection activities consistently by providing customized email reminders, or programmed process for sending collection letters. 

## Collections process setup
You can use the **Collections process setup** page (**Credit and collections > Setup > Collections process setup**) to create an automated collections process that will schedule activities, send email messages, and create and post customer collection letters. The process steps are based on the leading or oldest open invoice. Each step uses this invoice to determine what communication or activity should take place with a specific customer.  

Collections teams typically send out an early notice related to each outstanding invoice so that a customer is notified when invoice is about to become due. The **Pre-dunning** selection can be set to allow one step in each process hierarchy to be acted on for every invoice as the invoice timing reaches that step.

### Process hierarchy
Each customer pool can only be assigned to one process hierarchy. The hierarchy rank of this step identifies which process will take precedence if a customer is included in more than one pool that has a process hierarchy assigned. The pool ID determines which customers will be assigned to the process. Each hierarchy that is setup can only be assigned to one process automation.

The quiet days are used to ensure that a customer doesn't get contacted too frequently by the automated process. For example, if the quiet days are set to two, a customer will not be contacted by the automated process for at least two days, even if the original leading invoice has been settled in full. 

To exclude customers from the process automation if the customer aging balance or invoice amount is less than a defined value, select **Customer aging balance less than** or **Invoice amount less than** in the **Exclude from process** field and enter the amount value.

Mark **Use prediction** to create collections activities using Customer payment predictions. The activities created will use the Activity template from **Payment predictions** on the **Accounts receivable parameters** page, **Collections process automation** tab. 

### Process details
Click **New** to add a new process detail to the hierarchy. The **Description** is used to identify the purpose or name of the step in the hierarchy. Select the **Action type** to define the step that will create an activity, send an email, or create a collection letter. 

- The **Business document** defines the template used to create the action type. This document can be an activity template, an email template, or a collection letter sent to each customer. Collections process automation only creates collection letters per customer, regardless of how other collections parameters are set.
- **When** defines the process step that will occur before or after the leading (oldest) invoice due date, and is used together with the number displayed in the **Days in relation to the invoice due date** column. 
- Mark the **Pre-dunning** option to create an action for every invoice in one step in a process hierarchy. Pre-dunning actions are typically an early notice related to outstanding invoices so a customer can be notified when an invoice is about to become due. Pre-dunning can only be marked for one activity per hierarchy. When you select an email action type, the recipient will be used to define whether the email message is sent to a customer, sales group, or collections agent contact. 
- The value in the **Business purpose contact** field will then determine which contact from that customer's account will receive the communication.

### Business document details
The business document details will vary based on the action type that's selected in the process details. When the action type is an activity, the activity template details will be shown. These details include the activity template name, the type of activity that will be created, the purpose of the activity, the number of days scheduled to complete the activity, and the details of the activity. This activity will then link to the leading invoice that tells the recipient of the action that’s needed to complete the activity.

If the action type is an email in the process details, this section will contain two FastTabs. The first is used to define the template ID, email description, default language, the user name that will be assigned to email messages that are automatically sent, and the associated senders email address. The second will allow the body of the email to be created after the values in the **Language** and **Subject** fields are saved by selecting **Edit**. This will open a window that allows HTML content to be uploaded. 

> [!Note]
> You can save an Outlook email message that contains the body text of the communication in HTML format. You can then be upload the message content to implement the template. <br> <br> If the action type of collection letter is selected there will not be a business document detail section on the setup page.

Use the **Collections process history** button to view the recent history for the selected process hierarchy. 

Click the **Collections process assignment** action to view customers assigned to a collections process. Use **Preview customer assignment** to view the hierarchy that a specific customer is assigned. Use **Preview process assignment** to preview the customers that will be assigned to a hierarchy when it is run. Click **Manual assignment** to view customers that have been manually assigned to a process or select customers to be assigned a process.

Click the **Process simulation** action to preview the actions that will be created if the selected process automation is run at this time. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
