---
title: Billing schedules with projects
description: Learn about the Billing schedules with projects feature, which lets you set up a billing schedule that has a project ID and invoice it through a project invoice proposal.
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.24
---

# Billing schedules with projects

[!INCLUDE [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Subscription billing enables organizations to manage recurring billing through billing schedules. Projects help you plan, create, manage, control, and complete customer-focused work for your organization. On some time-and-material projects, a customer might have to be billed on a recurring basis for all or part of the project.

For example, for one project that you have with a customer, the customer agrees to pay for a monthly subscription for a service, such as cloud storage or a support contract. Use a billing schedule to set up the recurring charge, and use the project invoice proposal to do the billing. This approach helps streamline customer billing, because project transactions and recurring billing charges can be included in the project invoice proposal.

> [!NOTE]
> Billing schedules with projects are available only in Microsoft Dynamics 365 Project Operations – Stocked/Production-based deployments.

## Enable billing schedules with projects

In the **Feature management** workspace, enable the **Billing schedules with projects** feature in the **Subscription billing** module. After you enable it, refresh the browser window. This integration works with the **Project management and accounting** module in Dynamics 365 Finance.

1. Go to **Project management and accounting \> Setup \> Project management and accounting parameters**.
1. On the **Project stage** tab, select a stage, and then select a value in the **Project stage rules** field. The system adds project stage rules for creating a billing schedule on a time-and-material project.
3. You must set the **Create billing schedule** option to **Yes** to create a billing schedule that's linked to a project in the selected project stage.

## Create a billing schedule from a project

To create a billing schedule directly from a time-and-material project, follow these steps:

1. On **All projects**, select a project.
1. On the Action Pane, on the **Manage** tab, select **New**, and then select **Subscription billing > Billing schedule**. The **Create billing schedule** page opens and includes the standard options for creating a billing schedule.
1. Select the **Billing schedule** group. By default, the customer account, customer name, project, and funding source come from the project. If the project contract has more than one funding source (customer or grant), select the funding source for the billing schedule. This funding source is the invoice account.
1. (Optional) Set the **End user account** and **End user name** fields.
1. Set the **Billing start date** and **Number of periods** fields. The system automatically calculates the **Billing end date** value, but you can also enter a value.
1. Select **OK** to create the billing schedule.

The **All billing schedules** page shows the newly created billing schedule. By default, the **Project ID**, **Project name**, **Project contract ID**, and **Funding source** values on the billing schedule header come from the project. By default, the payment terms, payment schedule, and currency come from the funding source. You can change the project fields until you add billing schedule lines. When you use a project on a billing schedule, the **Invoice transaction type** field is set to **Sales order** and can't be changed.

## Billing schedule lines

If you add a project to a billing schedule header, the project appears by default on the billing schedule line on the **Project** tab. By default, the **Project ID**, **Category**, **Line property**, and **Sales tax** values come from the project. When a billing schedule line has a project, you can only add service items and non-stock items to it. You can add billing schedule lines without the project ID.

When you invoice a billing schedule line that has a project by using the **Generate invoice** process, a sales order is created if you select the **Create sales order** option. The sales order is invoiced through a project invoice proposal, not a standard sales invoice. If a packing slip is required, you must post it before invoicing. If you select the **Show Posting invoice or Create invoice proposal page** option, the invoice proposal is created and opened for review. If you select **Post invoice automatically** in the **Posting option** field, the sales order is created, and the project invoice proposal that includes the sales order is created and automatically posted.

> [!NOTE]
> If the **Generate invoice** process doesn't show billing schedule lines, verify that the following requirements are met:
>
> - If you mark unbilled revenue for the billing schedule line, you must complete the **Create journal entry** process.
> - On the **Billing schedule** header, on the **Address** tab, you must define a bill-to address for the customer.
> - The billing schedule or billing schedule line must not have an **On hold** status.
> - On the **Project management and accounting parameters** page, the project stage must be set to one that can be invoiced.

## View a billing schedule from a project or a project contract

To view a billing schedule, follow these steps:

1. On **All projects**, select a project.
1. Select **Manage**, select **Related information**, and then select **Subscription billing > Billing schedules**. The **All billing schedules** page shows billing schedules that you created for the selected project.
1. On **Project contracts**, select **Maintain**. Under **Related information**, select **Subscription billing > Billing schedules**. The **All billing schedules** page shows any billing schedules that you created for the project contract.
