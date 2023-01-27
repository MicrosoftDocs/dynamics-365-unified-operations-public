---
# required metadata

title: Billing schedules with projects
description: Billing schedules with projects enables setting up a billing schedule with a project ID and invoicing it through a project invoice proposal. 
author: JodiChristiansen
ms.date: 01/27/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Billing schedules (Subscription billing) and projects
Subscription billing enables organizations to manage recurring billing through billing schedules. Projects help you to plan, create, manage, control and complete
customer-focused work for your organization. On some Time and material projects there may be times when a customer needs to be billed on a recurring basis for all or
part of the project. For example, you may have a project with a customer where they agree to pay for a monthly subscription for a service, such as cloud storage or a
support contract. A billing schedule can be used to set up the recurring charge and billed using the project invoice proposal. This helps streamline billing to the
customers as project transactions and recurring billing charges can be included on the project invoice proposal.

Note: Billing schedules with projects are only available with Project Operations – Stocked/Production based deployments. 

## Enable Billing schedules with projects
In Feature management the **Billing schedules with projects** feature needs to be enabled. It is in the Subscription billing module. Once enabled refresh the browser.
This integration works with the Project management and accounting module in Dynamics 365. Select Project management and accounting > Setup > Project management and
accounting parameters. Select the Project stage tab, select a stage and then **Project stage rules** drop-down menu. Project stage rules for creating a billing
schedule on a Time and material project have been added. The Create billing schedule must be set to Yes to create a billing schedule linked to a project in that
project stage. 

## Create a billing schedule from a project
A billing schedule can be created directly from a Time and material project. With the project selected, select the Manage tab in the action pane, under New select
**Subscription billing > Billing schedule**. This opens the **Create billing schedule** page with the standard options to create the billing schedule. Select the
Billing schedule group. The customer account, customer name, Project and Funding source default in from the project. If there is more than one funding source (customer
or grant) on the project contract, select the funding source for the billing schedule. This will be the funding source on the billing schedule and will be set as the
invoice account. The End user account and End user name are optional. Select the billing start date and number of periods and the Billing end date will calculate
automatically. Alternatively, the billing end date can be entered. Select OK to create the billing schedule. 
The **All billing schedules** page opens with the newly created billing schedule. In the Billing schedule header, the Project ID, Project name, Project contract ID and
Funding source default in from the project. The payment terms, payment schedule and currency also default from the funding source. The project fields may be changed
until billing schedule lines are added. When using a project on a billing schedule the Invoice transaction type is set to Sales order and cannot be changed. 

## Billing schedule lines
If a project is added to a billing schedule header, the project will default to the billing schedule line found under Line details, Project tab. The Project ID,
category, line property and Sales tax fields default from the project. When a billing schedule line has a project, only service items and non-stock items can be added
to the line. Billing schedule lines can be added without the project ID. 

When a billing schedule line with a project is invoiced using the Generate invoice process, a sales order is created when using the **Create sales order** option. The
sales order is invoiced through a project invoice proposal, not a standard sales invoice. The packing slip must be posted before invoicing if required. If the **Show
Posting invoice or Create invoice proposal** option is selected, then the invoice proposal is created and will be opened for review. If **Post invoice automatically**
is used the sales order is created, the project invoice proposal is created including the sales order, then posted automatically.

Note: If generate invoice doesn’t show any billing schedule lines check the following:
1.	If unbilled revenue is marked for the billing schedule line the Create journal entry process needs to be completed
2.	On the billing schedule header, select the Address tab, customer needs a Bill-to address
3.	The billing schedule or billing schedule line cannot have the On hold status
4.	The project stage must be set to one that can be invoiced

## Viewing a billing schedule from a project or project contract
From the **All projects** page, select a project. Select Manage from the action pane, then under Related information choose Subscription billing > Billing schedules. This opens the **All billing schedules** page to any billing schedules created for that project. From the **Project contracts** page, select Maintain from the action pane, then under Related information choose Subscription billing > Billing schedules. This opens the **All billing schedules** page for any billing schedules created for the project contract. 



