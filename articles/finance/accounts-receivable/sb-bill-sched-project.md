---
# required metadata

title: Billing schedules with projects
description: This article provides information about the Billing schedules with projects feature, which lets you set up a billing schedule that has a project ID and invoice it through a project invoice proposal.
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

# Billing schedules with projects

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Subscription billing enables organizations to manage recurring billing through billing schedules. Projects help you plan, create, manage, control, and complete customer-focused work for your organization. On some time-and-material projects, a customer might have to be billed on a recurring basis for all or part of the project.

For example, for one project that you have with a customer, the customer agrees to pay for a monthly subscription for a service, such as cloud storage or a support contract. A billing schedule can be used to set up the recurring charge, and the project invoice proposal can be used to do the billing. This approach helps streamline customer billing, because project transactions and recurring billing charges can be included in the project invoice proposal.

> [!NOTE]
> Billing schedules with projects are available only in Microsoft Dynamics 365 Project Operations – Stocked/Production-based deployments.

## Enable billing schedules with projects

In the **Feature management** workspace, you must enable the **Billing schedules with projects** feature in the **Subscription billing** module. After it's enabled, refresh the browser window. This integration works with the **Project management and accounting** module in Dynamics 365 Finance.

1. Go to **Project management and accounting \> Setup \> Project management and accounting parameters**.
2. On the **Project stage** tab, select a stage, and then select a value in the **Project stage rules** field. Project stage rules for creating a billing schedule on a time-and-material project are added.
3. You must set the **Create billing schedule** option to **Yes** to create a billing schedule that's linked to a project in the selected project stage.

## Create a billing schedule from a project

To create a billing schedule directly from a time-and-material project, follow these steps.

1. On the **All projects** page, select a project.
2. On the Action Pane, on the **Manage** tab, select **New**, and then select **Subscription billing \> Billing schedule**. The **Create billing schedule** page is opened and includes the standard options for creating a billing schedule.
3. Select the **Billing schedule** group. By default, the customer account, customer name, project, and funding source are entered from the project. If there's more than one funding source (customer or grant) on the project contract, select the funding source for the billing schedule. This funding source will be set as the invoice account.
4. Optional: Set the **End user account** and **End user name** fields.
5. Set the **Billing start date** and **Number of periods** fields. The **Billing end date** value is automatically calculated, but you can also enter a value.
6. Select **OK** to create the billing schedule.

The **All billing schedules** page shows the newly created billing schedule. By default, the **Project ID**, **Project name**, **Project contract ID**, and **Funding source** values on the billing schedule header are entered from the project. By default, the payment terms, payment schedule, and currency are entered from the funding source. The project fields can be changed until billing schedule lines are added. When a project is used on a billing schedule, the **Invoice transaction type** field is set to **Sales order** and can't be changed.

## Billing schedule lines

If a project is added to a billing schedule header, it will be entered by default on the billing schedule line on the **Project** tab. By default, the **Project ID**, **Category**, **Line property** and **Sales tax** values are entered from the project. When a billing schedule line has a project, only service items and non-stock items can be added to it. Billing schedule lines can be added without the project ID.

When a billing schedule line that has a project is invoiced by using the **Generate invoice** process, a sales order is created if the **Create sales order** option is selected. The sales order is invoiced through a project invoice proposal, not a standard sales invoice. If a packing slip is required, it must be posted before invoicing. If the **Show Posting invoice or Create invoice proposal page** option is selected, the invoice proposal is created and opened for review. If **Post invoice automatically** is selected in the **Posting option** field, the sales order is created, and the project invoice proposal that includes the sales order is created and automatically posted.

> [!NOTE]
> If the **Generate invoice** process doesn't show billing schedule lines, verify that the following requirements are met:
>
> - If unbilled revenue is marked for the billing schedule line, the **Create journal entry** process must be completed.
> - On the **Billing schedule** header, on the **Address** tab, a bill-to address must be defined for the customer.
> - The billing schedule or billing schedule line must not have an **On hold** status.
> - On the **Project management and accounting parameters** page, the project stage must be set to one that can be invoiced.

## Viewing a billing schedule from a project or a project contract

To view a billing schedule, follow these steps.

1. On the **All projects** page, select a project.
2. Select **Manage**, select **Related information**, and then select **Subscription billing \> Billing schedules**. The **All billing schedules** page shows billing schedules that have been created for the selected project.
3. On the **Project contracts** page, select **Maintain**, and then, under **Related information**, select **Subscription billing \> Billing schedules**. The **All billing schedules** page shows any billing schedules that have been created for the project contract.
