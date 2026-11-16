---
title: Follow up on purchase orders using the Procurement Agent (production-ready preview)
description: Learn how to use the Procurement Agent to identify unconfirmed or delayed purchase orders and automate follow-up emails tailored to your business needs.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: PurchCopilotFollowupTaskResults, PurchOrderProcessReceiptsWorkspace, AppCopilotAgentWorkspace, SysEmailParameters, VendTable, LogisticsLocationRole
ms.topic: how-to
ms.date: 11/16/2026
ms.update-cycle: 180-days
ms.collection:
  - bap-ai-copilot
ms.custom: 
  - bap-template
---

# Follow up on purchase orders by using the Procurement Agent (production-ready preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Procurement Agent helps you identify and follow up on purchase orders that vendors didn't yet confirm or that delivery is late for. For each order that it finds, the agent automatically generates a draft email that is addressed to the relevant vendor.

The Procurement Agent helps you perform the following actions:

- Create agent tasks to find purchase orders that require follow-up. Each user has unique tasks, so you can create and adjust them to meet your specific business needs.
- Configure how emails are generated for each task.
- Review the draft emails that the agent generates. After you review each message, you can modify it, and send it. To generate the emails, the agent uses data from the purchase order lines and related tables.

<a name="standard-scenarios"></a>

## Standard follow-up email scenarios

By default, the system provides two standard follow-up email scenarios that help you find purchase orders that require action:

- *Unconfirmed purchase orders* – This scenario finds purchase orders with a delivery date within the next 60 days that the vendor didn't yet confirm (that is, the confirmed delivery date is blank). The scenario uses the following criteria:
    - The **Deliver remainder (line)** field is set to a value other than *0* (zero).
    - The **Confirmed receipt date (line)** field is blank.
    - The **Requested receipt date (line)** field is set to a date that is before the current date.
    - The **Document status (header)** field isn't *None*.

- *Delayed purchase orders* – This scenario finds purchase orders that are delayed (that is, the confirmed delivery date is one or more days ago). The scenario uses the following criteria:
    - The **Deliver remainder (line)** field is set to a value other than *0* (zero).
    - The **Confirmed receipt date** field is set to a date that is before the current date.

- *Get tracking number* – This scenario finds confirmed purchase orders that have an upcoming delivery date but no shipment tracking number or carrier. The scenario uses the following criteria:
    - The **Deliver remainder (line)** field is set to a value other than *0* (zero).
    - The **createdDateTime (header)** field is set to a date that is before the current date.

<a name="custom-scenarios"></a>

## Configure custom follow-up email scenarios

In addition to the standard scenarios described in the previous section, you can create custom follow-up scenarios to address other business needs.

In addition to confirmations and delivery dates, procurement teams also contact vendors about certificates, compliance documents, quality issues, pricing acknowledgements, and other organization-specific requests. Custom scenarios let you define your own follow-up purposes in addition to the built-in ones, so the Procurement Agent can automate the vendor outreach that matters to your business without any code changes.

### Prerequisites

Custom scenarios are available starting in Supply Chain Management version 10.0.49, build 10.0.2790.83. They're turned on by default starting in version 10.0.50. If you're running an earlier version than 10.0.50, turn on the *Issue: 1175850* feature in the [Feature management](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) workspace.

### Who can create and use custom scenarios

Your security role determines whether you can create custom scenarios or use and adapt existing ones:

- **To create custom scenarios** – Only users with the *Purchasing manager* role can create custom scenarios and enter the agent **Instructions** for them.
- **To use and adapt custom scenarios** – Any user who has access to the agents page can select a custom scenario in the agent configuration and adjust its settings, such as the selection criteria and email style. These users can't edit the scenario's instructions.

### Create a custom follow-up scenario

Create a custom scenario to define how the agent follows up with vendors about a specific business need. In this procedure, you enter instructions and set default email options. After you save the scenario, users can select it in the agent configuration to generate follow-up emails for that purpose.

1. Go to **Procurement and sourcing** > **(Preview) Procurement Agent - Supplier communications** > **(Preview) Follow-up email scenarios**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Name** – Enter a name for the scenario.
    - **Description** – Enter a description of the scenario.
    - **Instructions** – Enter the instructions that the agent follows when it generates emails for this scenario.
1. On the Action Pane, select **Save**.
1. On the **Default values** FastTab, set up the logic and options for the scenario. These settings work just like the standard task configuration in the agent (except you can't change the scenario setting). They work as described in [Configure agent task criteria and email settings](#task-criteria).

    > [!IMPORTANT]
    > Always review and update the selection criteria before you activate a custom scenario. Because the system can't know the purpose of a custom scenario, its default criteria are very generic and can select many purchase orders that the scenario isn't intended for. As a result, the agent might generate and send follow-up emails to vendors about purchase orders that you didn't expect. A warning message reminds you to review the criteria. Don't ignore it.

1. On the Action Pane, select **Save**.

<a name="task-criteria"></a>

## Configure agent task criteria and email settings

The following procedure explains how to set up agent tasks to find purchase orders that require follow-up. It also explains how to configure the way that Copilot generates vendor email content for each task.

1. Open the **(Preview) Follow-up emails** page by following one of these steps:

    - Go to **Procurement and Sourcing** > **(Preview) Procurement Agent - Supplier communications** > **(Preview) Follow-up emails**.
    - Go to **Procurement and sourcing** > **Purchase order receipt and follow-up** to open the **Purchase order receipt and follow-up** workspace. A tile named **(Preview) Follow-up emails** indicates the number of emails that require review. Select the tile.

1. Follow one of these steps:

    - To create a new agent task, select **Configure agents**. Open the **Library** tab. Find the **Send follow-up emails to vendors with Supplier Communications Agent** tile and select its **Select** button.
    - To edit an existing agent task, select **Configure agents**. Then find the task you want to edit in the list, expand it, and select **Edit**.
    - To remove an existing agent task, select **Configure agents**. Then find the task you want to edit in the list, expand it, and select **Delete**.

1. Edit the **Title** of the task as required. Ensure that each agent task has a unique and descriptive title.
1. Use the various dropdown lists in the sentence at the top of the page to set the basic logic for the scenario. For example: *Draft an email from **this sender address** to **follow up on delayed orders** per **purchase order** when purchase orders meet **these criteria***.

    - The first drop-down list lets you choose the sender's email address. When you select it, a dialog opens that lets you choose the address.
    - The second drop-down list lets you choose the scenario, which might be one of the [standard scenarios](#standard-scenarios) or a [custom scenario](#custom-scenarios) that you created. When you select a scenario, many of the other settings on this page (including the other drop-down options and configurations in the opening sentence) update based on the scenario's configuration and instructions.
    - The third drop-down list lets you choose whether to send one message per purchase order or one per vendor.
    - The fourth drop-down list opens a dialog that lets you choose the criteria that determine when the email should be sent. For example, you might want the task to find: unconfirmed orders for the next two months, or orders created more than three days ago, or orders sent but not confirmed.

    > [!IMPORTANT]
    > Always review and update the selection criteria to make sure you only target the purchase orders that you intend to. A warning message reminds you to review the criteria. Don't ignore it.

1. Set the following options for the message. Select a checkbox to turn an option on, then use its **Edit** button to configure it.
    - **Include purchase order details** – Select the purchase order details to include in the email. You can use these details as placeholders in the email sample (see the next setting).
    - **Customize email style with a sample** – Enter a sample subject and body that the agent uses as a model when it generates emails. To insert purchase order details, put the field name in square brackets, such as *[PO number]* or *[Confirmed receipt date]*. The agent replaces each placeholder with the actual value.
    - **Include signature** – Choose whether to add an AI-generated signature or your own signature to the end of every email.
    - **Include AI disclaimer** – Choose whether to add an AI disclaimer to every email.
    - **Generate new emails and delete old ones every time the agent runs** – Select this checkbox to delete unsent emails and generate new ones each time the agent runs, so that drafts always reflect the latest purchase order status. Clear this checkbox to delete and regenerates emails only when the configuration changes.

    > [!NOTE]
    > Copilot credits are consumed every time new emails are generated. If you turn on **Generate new emails and delete old ones every time the agent runs**, credit consumption increases.

1. Select **Save**.

> [!TIP]
> Before you turn on automatic sending, preview the purchase orders that match your criteria and review the generated emails to confirm that the scenario targets the right purchase orders.

### Examples

Here are some examples of other tasks that you might set up:

- To generate emails for orders that you created less than three days ago, and that the vendor didn't yet confirm, specify the following criteria:

    - The **Deliver remainder (line)** field on the line is set to a value other than *0* (zero).
    - The **Confirmed receipt date (line)** field on the line is blank.
    - The **Created date** field is set to a date that's between three days before the current date and current date.
    - The **Orderer (header)** field on the header is set to your user account (the current user).

- To generate emails for orders that you created for vendor group A less than three days ago, and that the vendor didn't yet confirm, specify the following criteria:

    - The **Deliver remainder (line)** field on the line is set to a value other than *0* (zero).
    - The **Confirmed receipt date (line)** field on the line is blank.
    - The **Created date** field is set to a date that's between three days before the current date and current date.
    - The **Orderer (header)** field on the header is set to your user account (the current user).
    - The **Vendor (group)** field is set to *A*.

- You might want to send a second follow-up email if a vendor doesn't reply to the first one you sent. However, agent tasks are designed to generate just one email per purchase order unless the purchase order changes. Therefore, to continue following up when no vendor reply is received, create two agent tasks that use the same core criteria but different date ranges that don't overlap. You can use any suitable date field to define the ranges. For example, you can use the delivery date, as illustrated in the following table:

    | Agent task | Example criteria |
    |---|---|
    | *Recent overdue purchase orders* | The delivery date is between seven days ago and the current date. |
    | *Extended overdue purchase orders* | The delivery date is earlier than eight days ago. |

    This setup lets the first task generate draft emails for recently overdue purchase orders while a second task generate draft emails for purchase orders that are still overdue after that. Even though no purchase order changes are made, a second draft email is generated when the order moves into the second date range.

    > [!IMPORTANT]
    > Make sure that the date ranges don't overlap. Otherwise, the same purchase order might get evaluated by multiple tasks at the same time.

## Configure automatic sending of follow-up emails

To configure automatic sending of follow-up emails without requiring user review, follow these steps:

1. Sign in to Supply Chain Management as an administrator.
1. Go to **System administration** > **Workspaces** > **Feature management**.
1. Make sure the *(Production ready preview) Procurement Agent – Supplier communications - automatically sending follow-up emails* feature is turned on. This feature is optional and is turned off by default. Learn more in [Set up and configure supplier communications features of the Procurement Agent](procurement-agent-supplier-com-setup-wizard.md).
1. Go to **System administration** > **Setup** > **Email** > **Email parameters**.
1. Open the **Configuration** tab.
1. On the **General** FastTab, set **Batch email provider** to *Graph*. This setting turns on the batch email provider.
1. On the **Enabled interactive email providers** FastTab, make sure that *Graph* is listed in the **Enabled** column.
1. On the **Microsoft Graph settings** tab, make sure that the **Application ID** and **Application secret** fields are filled in. If they aren't, you might need to contact your organization's Azure tenant admin for help. Learn more in [Configure Microsoft Graph in Dynamics 365 finance and operations apps](../../fin-ops-core/dev-itpro/organization-administration/configure-email.md#configure-microsoft-graph-in-dynamics-365-finance-and-operations-apps).
1. To test whether the email is working, open the **Test email** tab. Set **Email provider** to *Graph* and enter the email address for an account that you can read in the **Send to** field. Then select **Send test email** and check your inbox for the test email.

## Configure the email sender

When a user reviews and sends an email that the agent drafts, the email comes from that user's email address.

When the system automatically sends an email without user review, the email comes from the [agent identity user](procurement-agent-supplier-com-setup-wizard.md) email address.

To configure the email address of any user (including the agent identity user):

1. Sign in to Supply Chain Management as an administrator.
1. Go to **System administration** > **Users**.
1. Select the user you want to configure (for example, the [agent identity user](procurement-agent-supplier-com-setup-wizard.md)).
1. On the Action Pane, select **User options**.
1. Open the **Account** tab.
1. On the **Email provider selection** FastTab, make the following settings:
    - **Email provider ID** – Set to *Graph*.
    - **Sender email** – Enter the email address that should appear in the **From** field of the follow-up emails sent by the selected user.

1. On the **Account** FastTab, enter the **Name** that you want to show in the signature of the email body. The emails conclude with a "Best regards" signature that includes the name configured in this field.

> [!TIP]
> If you're a user without administrator rights in Supply Chain Management, you can configure your own email parameters, but not other users'. To configure your own email parameters, select the settings gear icon at the upper right side of the screen, and choose **User Options** from the menu. Then continue from step 5 in the previous procedure.

## Configure the email receiver for each vendor

To choose the recipient of the follow-up emails for a vendor, follow these steps:

1. Go to **Procurement and sourcing** > **Vendors** > **All vendors**.
1. Find and open the vendor you want from the list.
1. The **Contact information** FastTab lists various ways that you can contact the selected vendor and lets you edit the list. Use the settings here to configure the email address the agent should use when sending follow-up emails to this vendor. The agent chooses which contact line to use as follows:
    - If you set up a contact line as the priority email address for purchase order communications, the agent always uses that email address for this vendor, regardless of whether the agent task is set up to send emails per purchase order or grouped per vendor. For details about how to set up this address, see [Set up the priority purchase order communications email address for a vendor](#priority-email).
    - If you don't set up a contact line as the priority email address for purchase order communications, the agent applies the following logic to find the email address to use:
        - If the agent task is configured to send emails grouped per vendor, the agent uses the contact line of **Type** *Email address* that has the **Primary** checkbox selected. If no email address is set as **Primary**, then the agent arbitrarily chooses one of the lines of **Type** *Email address*.
        - If the agent task is configured to send emails per purchase order, the agent prioritizes the **Email** field of the purchase order if there is one. If the purchase order doesn't have an email address, the agent uses the vendor's contact information as described in the previous bullet point.

> [!TIP]
> To see whether an email address listed on the **Contact information** FastTab is set up as the priority email address for purchase order communications, select the row and then select **Edit contact information** from the FastTab toolbar. In the **Edit contact information** dialog, check the value of the **Purpose** field. If it's set to *Purchase Order Communications* (or to another name that you created for this purpose), the email address is set up as the priority email address for purchase order communications. Learn more in [Set up the priority purchase order communications email address for a vendor](#priority-email).

## <a name="priority-email"></a>Set up the priority purchase order communications email address for a vendor

As described in the previous section, the agent always uses the contact line that is set up as the priority email address for purchase order communications if such a line exists for the vendor, regardless of whether the agent task is set up to group emails per vendor or per purchase order. To set up this priority address, follow these steps:

1. Go to **Organization administration** > **Global address book** > **Address and contact information purpose**.
1. At the top-right corner of the grid, open the **Grid options** menu (ellipsis button) and select **Insert columns**.
1. In the **Insert columns** dialog, select the check box for the row with a **Field value** of *Type*. Then select **Update**. The grid now shows a **Type** column.
1. If a row already exists with a **Type** of *Purchase Order Communications*, note its **Purpose** name and skip this step. Otherwise, add it by selecting  **New** on the Action Pane and make the following settings for the new row:
    - **Purpose** – Enter a short name, such as *My Purchase Order Agent Communications*.
    - **Description** – Enter a short description, such as *Priority purchase order communications email address for a vendor*.
    - **Postal address** – Don't select this check box because this purpose is for email addresses, not postal addresses.
    - **Contact information** – Select this check box. This option makes the row available for use with contact information lines, including email addresses.
    - **Type** – Select *Purchase Order Communications*.

1. On the Action Pane, select **Save**.
1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. Find and open the vendor you want to set up from the list.
1. On the **Contact information** FastTab, select the row with the email address you want to send follow-up messages to. Then select **Edit contact information** from the FastTab toolbar.
1. In the **Edit contact information** dialog, set **Purpose** to the purpose name you found or created earlier in this procedure.
1. Select **OK**.

## Review and send drafted emails

To review the emails that were previously created for the various configurations, go to **Procurement and Sourcing** > **(Preview) Procurement Agent - Supplier communications** > **(Preview) Follow-up emails**. The configurations appear on the left, and the emails for each configuration appear on the right.

To refresh the message list, select an agent task and then select **Run** from the Action Pane to run that task immediately and generate the latest follow-up emails.

Edit each message as required, and then select **Send** to send it to the vendor.

## Review sent emails

To view and follow up on emails that the agent already sent to suppliers, select **Reviewed emails** from the Action Pane.

## Set up the periodic agent run schedule and batch job options

The Procurement Agent includes a batch job that runs the agent automatically. To change the default configuration of the job, follow these steps:

1. Go to **System Administration** > **Inquiries** > **Batch jobs**.
1. Find and select the job that has a **Job description** that matches the name of the agent configuration, which is described in [Configure agent task criteria and email settings](#task-criteria). For example, if the agent name is *Send follow-up emails to vendors with Supplier Communications Agent*, you can locate its batch job quickly by using this text in the **Job description** column header filter. The agent name might be different on your system, so check the name before proceeding.

    :::image type="content" source="media/supplier-agent-batch-job.png" alt-text="Screenshot showing the column filter for finding a batch job by its description." lightbox="media/supplier-agent-batch-job.png":::

1. Select the job, and then select **Recurrence** from the Action Pane.
1. In the **Define recurrence** dialog, set up the run schedule as desired, and then select **OK**.

    :::image type="content" source="media/supplier-agent-batch-job-schedule.png" alt-text="Screenshot showing the settings provided for scheduling a batch job." lightbox="media/supplier-agent-batch-job-schedule.png":::

1. To get more information about the batch job and adjust other settings, return to the **Batch jobs** page and select the link in the **Job ID** column.
