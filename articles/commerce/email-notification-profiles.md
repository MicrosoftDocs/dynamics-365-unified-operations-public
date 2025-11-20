---
title: Set up an email notification profile
description: This article describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 11/20/2025
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---

# Set up an email notification profile

[!include [banner](includes/banner.md)]

This article describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.

When you create channels, you can set up an email notification profile. The email notification profile defines the events of a sales transaction (such as order created, order packed, and order invoiced events) for which you'll send notifications to your customers. 

For additional email configuration information, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json).

## Create an email template

Before an email notification type can be enabled, you must create an organization email template in Commerce headquarters for each notification type you want to support. This template defines the email subject, sender, default language, and email body for each supported language.

To create an email template, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Parameters \> Organization email templates**.
2. On the action pane, select **New**.
3. In the **Email ID** field, enter an ID to help identify this template.
4. In the **Sends name** field, enter the senders name.
5. In the **Email Description**, enter a meaningful description.
6. In the **Sender email**, enter the senders email address.
7. In the **General** section, select a default language for the email template. The default language will be used when no localized template exists for the specified language.
8. Expand the **Email message content** section and select **New** to create the template content. For each content item, select the language and provide the email subject line. If the email will have a body, ensure that the **Has body** box is checked.
9. On the action pane, select **Email message** to provide an email body template.

The following image shows some example email template settings.

:::image type="content" source="media/email-template.png" alt-text="Screenshot of email template settings.":::

For more information about creating email templates, see [Create email templates for transactional events](email-templates-transactions.md). 

## Create an email notification profile

To create an email notification profile in headquarters, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
2. On the action pane, select **New**.
3. In the **Email notification profile** field, enter a name to identify the profile.
4. In the **Description** field, enter a relevant description.
5. Set the **Active** switch to **Yes**.

## Add a notification type

To create an email event, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
2. Under **Retail email notification settings**, select **New**.
3. Select the appropriate **Email notification type** from the drop-down list. The options in the drop-down list are defined by the `RetailEventNotificationType` enum. If you want to add an option to the drop-down list, you must [extend the enum](../fin-ops-core/dev-itpro/extensibility/add-enum-value.md).
4. Select the email template you created above from the **Email ID** drop-down list.
5. Select the **Active** checkbox.
6. On the action pane, select **Save**.

The following image shows some example event notification settings.

:::image type="content" source="media/email-notification-profile.png" alt-text="Screenshot of event notification settings.":::

##  Associate the email notification profile to channel

The email notification profile created above can activated by associating it with the channel e.g., brick and mortal store, Online channel or call center channel. To do so, navigate to the channel form and select the desired email notification profile. 

> [!NOTE]
> The email notification profile can also be defaulted at the **Commerce parameters -> General** section, but it is recommended to define these at the individual channel level.

## Enable the optimized order notifications processing feature

When the **Optimized order notifications processing** feature is enabled, the email notification process job is executed in parallel and more emails can be processed at a time.

To enable the optimized order notifications processing feature in headquarters, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
2. On the **Not enabled** tab, in the **Feature name** list, find and select the **Optimized order notifications processing** feature.
3. In the lower-right corner, select **Enable now**. After the feature has been turned on, it will appear in the list on the **All** tab with a status of **Enabled**.

## Schedule a recurring email notification process job

To send out email notifications, you must have the **Process retail order email notification** job running.

To set up a batch job in headquarters for sending transactional emails, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Email and notifications \> Send email notification**.
2. In the **Process retail order email notification** dialog box, select **Recurrence**.
3. In the **Define recurrence** dialog box, select **No end date**.
4. Under **Recurrence pattern**, select **Minutes**, and then set the **Count** field to **1**. These settings will ensure that email notifications are processed as quickly as possible.
5. Select **OK** to return to the **Process retail order email notification** dialog box.
6. Select **OK** to complete the job setup.

### Enable optimized email notification processing

The **Optimized order notifications processing** feature enables optimized processing of email order notifications. When this feature is enabled, order notification emails are sent by several tasks running in parallel, resulting in higher job throughput. 

To enable optimized email notification processing, go to **Workspaces \> Feature Management** and enable the **Optimized order notifications processing** feature. 

> [!NOTE]
> If your Commerce headquarters version is older than 10.0.31, you must cancel the currently running **Process retail email order notification** batch job by going to **System Administration \> Inquiries \> Batch jobs** and deleting it. Then follow the instructions in [Schedule a recurring email notification process job](#schedule-a-recurring-email-notification-process-job) to recreate the batch job. 

## Schedule a clean-up batch job for email notification logs

To set up a clean-up batch job in headquarters for cleaning up email notification logs, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Email and notifications \> Clean up email notification logs**.
2. In the **Clean up email notification logs** dialog box, configure the following parameters:
    1. **Also delete unsent emails** - When this parameter is set to **Yes**, emails that weren't successfully sent will be deleted by the clean-up batch job.
    2. **Retention days** - This parameter specifies the number of days that emails should be kept. Only emails that are older than the number of days specified can be deleted by the clean-up batch job.
3. To set up a recurring job that checks and cleans up the email notification logs older than the specified number of retention days, select **Recurrence**.
4. In the **Define recurrence** dialog box, configure the recurrence pattern.
    - For example, to define a recurrence frequency of 3 months, under **Recurrence pattern**, select **Months**, and then for **Count** enter the number "3". This configuration has the batch job check and clean up logs every 3 months.
    - To keep the clean-up batch job running indefinitely, select **No end date**.
5. Select **OK** to return to the **Clean up email notification logs** dialog box.
6. Select **OK** to complete the job setup.

Once the batch job starts, it will continue to create subtasks to delete email notification logs based on the parameters until no logs are left to delete. The maximum number of logs that can be deleted by each subtask is 2000. To change the maximum number of logs that can be deleted, in headquarters go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Configuration parameters**, and then for the **NotificationLog_NumOfRowsToBeCleaned** parameter, enter a new maximum number. 

## Next steps

Before emails can be sent, you must configure your outgoing mail service. For more information, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json).

## Troubleshooting

### Check the email notification log

To check the email notification log, follow these steps.

1. Go to `https://<environment-URL>/?mi=RetailEventNotificationLog`.
2. If email is not found in the log, then the email notification is not processed. Verify that the **Email notification profile** is created correctly. 
    1. Go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
    2. In the **Retail event notification settings** section, verify the email notification type is active.
    3. Click **Email ID**, in the email template, verify that sender email, default language code and email message content are configured correctly. 
3. Verify that the **Process retail order email notification** job is scheduled.
    1. Go to **Retail and commerce \> Inquiries and reports \> Batch jobs**.
    2. Find the **Process retail order email notification** batch job.
    3. Verify that the batch job is executing.

### Check email sending failures

To check email sending failures, follow these steps.

1. Go to **System administration \> Setup \> Email \> Email history**.
2. For any emails where the email status value is **Failed**, review the error message on the **Failure details** tab and determine whether corrective actions should be taken. For more information, see [Common issues with sending email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json#common-issues-with-sending-email).

## Additional resources

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json)

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
