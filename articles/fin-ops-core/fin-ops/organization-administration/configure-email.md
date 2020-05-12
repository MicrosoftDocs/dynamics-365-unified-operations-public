---
# required metadata

title: Configure and send email
description: The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. 
author: ChrisGarty
manager: AnnBe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysEmailParameters
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 268274
ms.assetid: 194ca8fd-5e20-4464-9c85-08d2b5ff63ca
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Configure and send email

[!include [banner](../includes/banner.md)]

The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. This topic is divided into sections for administrators and users to make it easy to find relevant information.

Both administrators and users set the behavior of the email subsystem.

## Administrator: Email parameters page

On the **Email parameters** page, note the following settings on the **Configuration** tab.

| Field                 | Description |
|-----------------------|-------------|
| Batch email provider  | Specifies which email provider will be used to send emails that are sent by processes in a batch or non-interactive manner. The Exchange provider will use the account associated with the batch process. |
| Attachment size limit | Specifies the maximum size of a single email that can be sent via the email subsystem. |

In Platform update 32, an **Email history** page was added to allow administrators to review all sent emails, including any errors that might have prevented an email from being sent. By default, the last 30 days of email history is retained. This can be configured by changing the **Number of days to retain email history** to a non-zero amount. Zero provides the default amount and behavior.

On the **Email parameters** page, note the following settings on the **SMTP settings** tab.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Outgoing mail server</td>
<td>The host name of the desired SMTP server.
<ul>
<li>For <a href="https://support.office.com/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c">Microsoft 365 production</a> (including *.onmicrosoft.com accounts) use smtp.office365.com. (You can find this setting at outlook.office.com at <strong>Settings</strong> &gt; <strong>Mail</strong> &gt; <strong>POP and IMAP</strong>.)</li>
<li>For Outlook/Hotmail use smtp-mail.outlook.com.</li>
</ul>
</td>
</tr>
<tr>
<td>SMTP port number</td>
<td>Typically, the port number should be set to 587 for secure transport.</td>
</tr>
<tr>
<td><strong>User name</strong> and <strong>Password</strong></td>
<td>Specify, as needed, to send the email via the appropriate mail account. All users need to provide the SMTP account <strong>Send As</strong> and <strong>Send On Behalf Of</strong> permissions to enable the ability to send Simple Mail Transfer Protocol (SMTP) mail. You can configure Send As permissions in the Microsoft 365 admin center (portal.office.com/Admin), at <strong>Users</strong> &gt; <strong>Active users</strong> &gt; <strong>User</strong> &gt; <strong>Edit mailbox permissions</strong> &gt; <strong>Send email from this mailbox</strong>. For more information, see <a href="https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E">Enable sending email from another user's mailbox in Microsoft 365</a>.</td>
</tr>
<tr>
<td>Specify if SSL is required</td>
<td>Determines whether secure transport is used. Typically, this is <strong>Yes</strong>, except for internal or troubleshooting scenarios.</td>
</tr>
</tbody>
</table>

## Administrator: Email Distributor batch process

Email that is sent directly from the server, without user interaction, via SMTP is sent by the **Email distributor batch** process. That batch process must be started to process the email queue. To start the process, open the **Email distributor batch** pane (**System administration** &gt; **Periodic tasks** &gt; **Email processing** &gt; **Batch**) and turn on **Batch processing**.

If the Exchange provider is used, then the user account associated with the batch process (usually admin) will be sender.

## Administrator: User email

The default email address for each user is pulled from the **Email** field on the **Users** page (**System administration** &gt; **Users** &gt; **Users**). An email address should be specified for each user for sign in, so this field should be populated. Users can override this default if needed.

## User: Email provider selection section on the Options page

The **Options** page can be opened via **Settings &gt; User options**. The **Email provider selection** section is on the **Account** tab.

| Field             | Description |
|-------------------|-------------|
| Email provider ID | Allows the user to select the email provider that should be used when sending an email. Selecting an option here is the equivalent of selecting **Do not ask again** in the **How would you like to send email** dialog box. Selecting the blank option **Prompt for which email provider to use** will cause the **How would you like to send email** dialog box to display when an email is going to be sent. |
| Email             | Allows the user to provide an email address override for the **From** field of the email. By default, the email alias that associated with the user account is used as the **From** field in new emails, but this user option email address will override that. When sending email via SMTP the user needs to have appropriate **Send As** and **Send On Behalf Of** permissions configured in Exchange or on the SMTP server.<blockquote>[!NOTE] You can configure **Send As** and **Send On Behalf Of** permissions in the Microsoft 365 admin center (portal.office.com/Admin) at **Users** &gt; **Active users** &gt; **User** &gt; **Edit mailbox permissions** &gt; **Send email from this mailbox**. For more information, see [Enable sending email from another user's mailbox in Microsoft 365](https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E).</blockquote> |

## User (optional): How would you like to send email dialog box

When an email is going to be sent, the user will see the **How would you like to send email** dialog box that will list the available options for sending email.

| Field                                                                  | Description |
|------------------------------------------------------------------------|-------------|
| Use an email app, such as Outlook                                      | Provides the user with a generated email (.eml) file. |
| Use Exchange email server                                              | Uses the Exchange Online server associated with the tenant. The email will be sent using Exchange Web Services (EWS). On-premises Exchange servers are not supported at this time for the **Exchange** mail provider. |
| Use the system email client | Opens the **Send email** composition dialog box and then sends the resulting email via SMTP. |
| Do not ask again                                                       | If this field is not selected, the next time an email is sent the most recently selected option will be used and the dialog box will not open. |

## User (optional): Send email dialog box

The **Send email** dialog box is opened to allow the user to edit the contents of the email that will be sent. Some of the following fields will be pre-populated in this window.

| Field                                                     | Description |
|-----------------------------------------------------------|-------------|
| From                                                      | Populated from the **Email** field on the **Options** page. |
| **To**, **Cc**, **Bcc**, **Subject**, and **Body** | Populated with values specified by the process that initiated the sending of the email. These fields can be edited as needed by the user. |
| Attachments list                                          | May be populated with attachments specified by the process that initiated the sending of the email. This list can be edited as needed by the user. |

When the email is ready to be sent, the **Send** button will cause the email to be sent via SMTP.

## Usage scenarios to verify if email is configured correctly

### Send mail via a local mail client

Email workflows that are enabled via the SysEmail framework can generate email messages (.eml files) that contain attachments. You can then send these messages via Microsoft Outlook or another email client.

1. In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
2. Select **US-008 Sparrow Retail**.
3. Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
4. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
5. Click **OK** to accept the default values in the dialog box.
6. If you're prompted for the mail option to use, clear the **Do not ask again** check box (you can change this option from the **User options** page), select **Use an email app, such as Outlook**, and then click **OK**.
7. If you're using Internet Explorer on your computer, open the email (.eml) file that is generated. If you're using Internet Explorer on the VM, copy the file to your computer, and open it there.
8. Note the email address in the **To** field and the generated workbook attachment.

### Send mail via SMTP

Email workflows that are enabled via the SysEmail framework can also be created in a simple email dialog box and then sent via Simple Mail Transfer Protocol (SMTP).

1. Go to the **Email parameters** page.
2. Click **SMTP settings**.
3. Set the **Outgoing mail server** to the desired SMTP server:

    - For [Microsoft 365 production](https://support.office.com/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including \*.onmicrosoft.com accounts) use smtp.office365.com. (Find this setting via outlook.office.com, at **Settings** &gt; **Mail** &gt; **POP and IMAP**.)
    - For Outlook/Hotmail use smtp-mail.outlook.com.

4. Set the user name and password to an appropriate email account and password.
5. Leave **SSLRequired** turned on, and leave **SMTP port number** set to **587**.
6. Click **Save**.
7. In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
8. Select **US-008 Sparrow Retail**.
9. Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
10. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
11. Click **OK** to accept the default values in the dialog box.
12. If you're prompted for the mail option to use, select **Use the Microsoft Dynamics 365 for Finance and Operations email client**, and then click **OK**.
13. To receive the test message, change the **To address** to your email address.

    Ensure that the account specified in the SMTP settings is able to **Send As** and **Send On Behalf Of** your email account. The easiest way to ensure this to use your email account in the SMTP settings.

14. Enter a subject and body for the message.
15. Click **Send**. The message should be delivered in one to five minutes.

## Administrator: Workflow email notifications

Workflow email configuration is a collection of related settings that work in conjunction.

### Workflow email notification setup

1. Verify email settings:

    1. Go to **System administration** \> **Setup** \> **Email** \> **Email parameters**.
    2. Verify that SMTP is enabled.
    3. Set the SMTP mail server settings.

2. Verify that the email batch process is running:

    1. Go to **System administration** \> **Periodic tasks** \> **Email processing** \> **Email distributor batch**.
    2. Enable the **Batch processing** option.
    3. Optionally, adjust the recurrence of the email process:

        1. Select **No end date** to adjust all recurrences of the email batch process.
        2. Adjust the count.
        3. Adjust to run every minute if needed.

3. Verify workflow notification system email templates:

    1. Go to **System administration** \> **Setup** \> **Email** \> **System email templates** (for system-wide templates).
    2. Verify that the **Sender email** field is set and valid.

4. Verify workflow notification organization email templates:

    1. Go to **Organization administration** \> **Setup** \> **Organization email templates** (for organization-specific templates).
    2. Verify that the **Sender email** field is set and valid.

5. Verify that the user can receive email notifications:

    1. Go to **Settings** \> **User options**.
    2. Go to the **Account** tab.

       1. Set the email provider ID (for example, SMTP).
       2. Optionally, set the email address for the provider if it was not the default from the user setup.

    3. Navigate to the **Workflow** tab. Set the option to send notifications in email to **Yes**.

6. Verify that the workflow system will send email notifications:

    For each workflow that should have a notification, open the workflow properties in the workflow editor.

    1. Click **Basic settings**. Adjust the email template for the workflow notifications.
    2. Click **Notifications**.

        1. Enable the events for which a user should be notified.
        2. Set the recipient of the workflow notification for each event notification that is enabled.

    3. On a workflow approval element for which a user should be notified:

        1. Go to **Properties**.
        2. Enable the events for which a user should be notified.
        3. Set the recipient of the workflow notification for each event notification that is enabled.

### Workflow email notification testing

The testing for email notifications is to simply trigger the notification and then check for it.

1. Submit a workflow that has been set up for email notifications.
2. Check the workflow history to make sure that a workflow work item was assigned to the expected user.
3. Check the status of the pending email notification in **System administration** \> **Periodic tasks** \> **Email processing** \> **Batch email sending status**.

    If the email is fails to send, make sure that the SMTP mail account can be opened.

4. Check for the email notification in the appropriate inbox.

## Troubleshoot email

There are a few standard steps that can help you troubleshoot the configuration of email settings.

1. Verify email settings:

    1. Go to **System administration** \> **Setup** \> **Email** \> **Email parameters**.
    2. Verify that SMTP is enabled.
    3. Verify the settings of the SMTP mail server.
    4. Sign in to the SMTP account in a separate window to make sure that the account and password are correct.
    5. Send a test email using **System administration** \> **Setup** \> **Email** \> **Email parameters** \> **Test email**.

2. Verify that the email batch process is running:

    1. Go to **System administration** \> **Periodic tasks** \> **Email processing** \> **Batch**.
    2. Make sure that the **Batch processing** option is set to **Yes**.
    3. Review the recurrence of the email process:

        1. Select **No end date** to adjust all recurrences of the email batch process.
        2. Adjust the count as you require.

3. To review the contents and status of batch emails, go to **System administration** \> **Periodic tasks** \> **Email processing** \> **Batch email sending status**.

    1. If you're using a release that is earlier than Platform update 28, personalize the form to add the email sender for easy review. To do this, right-click the grid header, select **Add columns**, select **Email**, and then click **Insert**. If the **Email** field isn't added into the grid, you can view the sender by selecting **Show message**, and then selecting the **Email** field.
    2. Verify that emails are being sent from the correct account. If the account is incorrect, you need to adjust settings such as user options, system templates,  or organization templates, as needed.
    3. Verify that all email user accounts have been granted permission to **Send As** for the configured SMTP account (see step 4 for details).
    
4. In Platform update 32, an **Email history** page was added to allow administrators to review all sent emails, including any errors that might have prevented an email from being sent. The **Email history** page will show interactive as well as non-interactive/batch emails. For any emails that have an **Email status** of **Failed**, review the error message on the **Failure details** tab and determine if corrective actions should be taken.

5. In the Microsoft 365 admin center, verify that all user mail accounts that will be used to send emails have **Send As** and **Send On Behalf Of** permissions for the configured SMTP account. For more information, see [Enable sending email from another user's mailbox in Microsoft 365](https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E).
6. Sign in to all user mailboxes to verify that they are valid and can be accessed using sign in.
7. Send a test email using **System administration** \> **Setup** \> **Email** \> **Email parameters** \> **Test email**.
8. If the SMTP settings were migrated from another environment, clear the password field and re-enter the password to ensure that the field encryption hasn't negatively affected the stored value.
9. If you continue to experience issues when email is sent via SMTP, enter the SMTP account information in a tool such as [SMTPer.net](https://www.smtper.net/) to verify that the SMTP server and account are valid and working correctly.


## Troubleshoot the Exchange mail provider

The **Email parameters** page allows an administrator to select Exchange as an interactive email provider and as the Batch email provider. The Exchange mail provider will use the current user's Exchange Online account to send emails. When used as the Batch email provider, the batch account will be used. No additional configuration is needed. 
If troubleshooting is needed, ensure that the current user's account can be signed into and that emails can be sent from that account to the intended recipients.

### Exchange mail provider not supported for external users

Users that are external to the primary tenant will not have exchange accounts on that tenant, so the Exchange mail provider is not supported for external users.

## Other notes

The system communicates with Exchange or an SMTP server like a typical email client, so standard behavior and limits apply. For example, standard [Exchange Online receiving and sending limits](https://technet.microsoft.com/library/exchange-online-limits.aspx#RecipientLimits) apply.

## Additional resources

[Troubleshoot the Office integration](../../dev-itpro/office-integration/office-integration-troubleshooting.md)

[Office integration tutorial](../../dev-itpro/office-integration/office-integration-tutorial.md)

[Configure email functionality in Microsoft Dynamics AX [AX 2012]](https://technet.microsoft.com/library/aa834374.aspx)
