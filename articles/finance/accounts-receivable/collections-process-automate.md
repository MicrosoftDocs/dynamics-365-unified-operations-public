---
# required metadata

title: Collections process automation
description: This topic describes the process of setting up collections process strategies that automatically identify customer invoices that require an email reminder, collection activity (such as a phone call), or a collection letter to be sent to the customer. 
author: panolte
manager: AnnBe
ms.date: 08/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  CustomerCollectionManagerWorkspace
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
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

This topic describes the process of setting up collections process strategies that automatically identify customer invoices that require an email reminder, collection activity (such as a phone call), or a collection letter to be sent to the customer. 

Organizations spend a significant amount of time researching aged balance reports, customer accounts, and open invoices to determine which customers need to be contacted about an open invoice or account balance. This research takes times away from a collection agent’s time spent communicating with customers to collect past due balances or resolving invoice disputes. Collections process automation lets you set up a strategy-based approach to your collection process. This helps you apply collection activities consistently by providing customized email reminders, or programmed process for sending collection letters. 

## Collections process setup
You can use the **Collections process setup** page (**Credit and collections > Setup > Collections process setup**) to create an automated collections process that will schedule activities, send email messages, and create and post customer collection letters. The process steps are based on the leading or oldest open invoice. Each step uses this invoice to determine what communication or activity should take place with a specific customer.  

### Process hierarchy
Each customer pool can only be assigned to one process hierarchy. The hierarchy rank of this step identifies which process will take precedence if a customer is included in more than one pool that has a process hierarchy assigned. The pool ID determines which customers will be assigned to the process. 

The quiet days are used to ensure that a customer does not get contacted too frequently by the automated process.  For example, if the quiet days are set to two, a customer will not be contacted by the automated process for at least two days, even if the original leading invoice has been settled in full. 

To exclude customers from the process automation if the account balance or invoice balance is less than a defined value, set the **Exclude from process** field to **Yes** and enter the amount value.

## Process details
**Description** is used to identify the purpose or name of the step in the hierarchy.

**Action type** defines if the step will create an activity, send an email, or create a collection letter.

**Business document** defines the template used to create the action type.  This can be an activity template, an email template, or a collection letter per customer. 

The action types can be created on either before or after the invoice due date, based on the setting that's displayed in the **Days in relation to the invoice due date** column.

When you select an email action type, the recipient will be used to define if that is a customer, sales group, or collections agent contact. The value in the **Business purpose contact** field will then determine which contact from that customer's account will receive the communication.

## Business document details
The business document details will vary based on the action type that's selected in the process details.  When the action type is an activity, the activity template details will be shown.  These details include the activity template name, the type of activity that will be created, the purpose of the activity, the number of days scheduled to complete the activity, and the details of the activity.  This activity will then link to the leading invoice that tells the recipient of the action that’s needed to complete the activity.

If the action type is an email in the process details, this section will contain two FastTabs.  The first is used to define the template ID, email description, default language, the user name that will be assigned to email messages that are automatically sent, and the associated senders email address. The second will allow the body of the email to be created after the values in the **Language** and **Subject** fields are saved by selecting **Edit**.  This will open a window that allows HTML content to be uploaded. You can also type the message that’s created manually in the lower left box of the window.  

> [!Note]
> An Outlook email can be saved with the desired body of the communication in HTML format. This can then be uploaded to implement the template. <br> <br> If the action type of collection letter is selected there will not be a business document detail section on the setup form.


## FastTab reference
The following tables list the pages and fields that the specified FastTabs can be accessed from, along with a description of the information in that tab. 

### Process hierarchy

|     Page                                                	|     Field                     	|     Description                          	|
| --------------------------------------------------------	|-------------------------------	|---------------------------------------	|
|     Collections   process setup <br> Process automation    	|                               	|     Create and   manage collections processes based on customer pool assignments.                                                                                                                           	|
|     Collections   process setup <br> Process automation    	|     Hierarchy                 	|     Defines the   priority of process automation to assign a customer if they belong in multiple pools.                                                                                               	|
|     Collections   process setup <br> Process automation    	|     Pool ID                   	|     Queries that   define a group of customer records.                                                                                                                                                     	|
|     Collections   process setup <br> Process automation    	|     Quiet days                	|     Limit how frequently a process step can be completed. For example, if two quiet days are set the next process step will not   occur for at least two days if the leading invoice changes.    	|
|     Collections   process setup <br> Process automation    	|     Exclude from   Process    	|     Selecting either **Customer aging balance less than** or **Invoice amount less than** will exclude a customer from the process automation if the value criteria is not met.                               	|

### Process details
|     Page                                               	|     Field                                     	|      Description                	|
|--------------------------------------------------------	|-----------------------------------------------	|----------------------------	|
|     Collections   process setup <br> Process automation    	|                                               	|     Define the steps   taken based on the leading invoice.                                                                                               	|
|                                                        	|     Description                               	|     Free text   field used for providing a name and/or description of the step.                                                                          	|
|                                                        	|     Action type                               	|     Activity,   email, or collection letter that will be created by the process step.                                                                    	|
|                                                        	|     Business   document                       	|     Defines the   activity or email template that is used during the process step.                                                                      	|
|                                                        	|     When                                      	|     Defines if   the process step will occur before or after the leading invoice due date   along with the **Days in relation to invoice due date** field.    	|
|                                                        	|     Days in   relation to invoice due date    	|     Together   with the **When** field it identifies the timing of the process step.                                                                        	|
|                                                        	|     Recipient                                 	|     Identifies   if an email will be sent to a Customer, Sales group, or Collections Agent contact.                                                  	|
|                                                        	|     Business   purpose contact                	|     Determines   which recipient’s email address is used in email communications.                                                                             	|

### Business process activity template details 
|     Page                                               	|     Field                  	|      Description              	|
|--------------------------------------------------------	|----------------------------	|-------------------------	|
|     Collections   process setup <br> Process automation    	|                            	|     Section of   the setup process that identifies the details of the activity template.                                                                     	|
|     Collections   process setup <br> Process automation    	|     Activity   template    	|     Identifies   the type, purpose, number of days to complete, and provides details about the   activity that will be created during an activity process step.    	|

### Business document email template details 
|     Page                                               	|     Field    	|      Description                 	|
|--------------------------------------------------------	|--------------	|-----------------------------	|
|     Collections   process setup <br> Process automation    	|              	|     Identifies   the email description, default language, senders name, and email address that will be   created during an email process step.    	|


### Collections history 
|     Page                           	|     Field    	|      Description                                                         	|
|------------------------------------	|--------------	|---------------------------------------------------------------------	|
|     Collections   process setup    	|              	|     View the   recent history for the selected process hierarchy.    	|

### Collection process assignment
|     Page                           	|     Field    	|      Description                                                	|
|------------------------------------	|--------------	|-----------------------------------------------------------	|
|     Collections   process setup    	|              	|     View   customers assigned to a collections process.  
|     Manual assignment               |               |     View customers that have been manually assigned to a process or select customers to be assigned to a process. |
|     Preview process assignment      |               |     Preview the customers that will be assigned to a strategy when it is run.   |
|     Preview customer assignment     |               |     View the strategy that a specific customer is assigned.    |
 
### Parameters
|     Page                                                                 	|     Field                                            	|      Description                           	|
|--------------------------------------------------------------------------	|------------------------------------------------------	|-------------------------------------	|
|     Accounts   receivable parameters > Collections process automation    	|     Percentage   of customers per batch task         	|     Setting to   determine the number of batch tasks per automation process.                                         	|
|     Accounts   receivable parameters > Collections process automation    	|     Post   Collection letters automatically          	|     Collection   letter action types will post the letter during the automation.                                     	|
|     Accounts   receivable parameters > Collections process automation    	|     Create   activities for automation               	|     Create and   close activities for non-activity action types to view all automated steps   taken on an account.    	|
|     Accounts   receivable parameters > Collections process automation    	|     Days to keep   collections process automation    	|     Defines the   number of days collections history is stored.                                                      	|
