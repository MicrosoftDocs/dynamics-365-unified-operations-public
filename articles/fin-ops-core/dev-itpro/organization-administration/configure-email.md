---
title: Configure and send email
description: The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. 
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: SysEmailParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 194ca8fd-5e20-4464-9c85-08d2b5ff63ca
---

# Configure and send email

[!include [banner](../../../finance/includes/banner.md)]

The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. This article is divided into sections for administrators and users to make it easy to find relevant information.

Both administrators and users set the behavior of the email subsystem.

## [Administrator] Email parameters page

### Email configuration for the environment

On the **Email parameters** page, administrators can configure the high-level email behavior for the environment from the **Configuration** tab.

| Field                 | Description |
|-----------------------|-------------|
| Batch email provider  | Specifies which email provider will be used to send emails that are sent by processes in a batch or non-interactive manner. The Microsoft Graph and Exchange providers will use the account that's associated with the batch process. Note: Microsoft Graph is available in Dynamics 365 Finance version 10.0.38 and later. |
| Attachment size limit | Specifies the maximum size of a single email that can be sent via the email subsystem. |
| Email expiration in days | Specifies the number of days before the status of an unsent message is set to **Expired**. A value of **0** means that the default period of 30 days is in effect. |

The **Email history** section serves two purposes. First, it provides an entry point to the **Email history** page, where administrators can review all sent emails and also any errors that prevented an email from being sent. Second, it lets you configure how long email history is maintained. By default, the last 30 days of email history are retained. You can adjust this period by changing the value of the **Number of days to retain email history** field to a non-zero number. If you set the value to **0** (zero), the default number and behavior are used.

The **Email throttling** section enables non-interactive email providers (such as the batch email provider) to adhere to a per-minute sending limit. This feature can help prevent some errors if the system tries to send more emails than the provider allows. Specifically, if an email can't originally be sent because the per-minute sending limit has been reached, the send attempt for the email will be deferred for up to one minute. After ten deferrals, the system will try to send the email regardless. You can remove the per-minute sending limit from a provider by resetting the **per-minute email sending limit** field to **0**. The sending limits for the Office 365 SMTP email provider is automatically set according to the [Exchange Online sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits). Manual configuration is required for all other email providers.

> [!NOTE]
> Use of the **Email throttling** feature isn't recommended for the Microsoft Graph and Exchange email providers, because they have their own throttling mechanisms. Therefore, you should ensure that the **per-minute email sending limit** field is set to **0** for both those providers.

### Send email with Microsoft Graph

For customers who use Office 365, Microsoft Graph is the recommended email provider for Dynamics 365 finance and operations apps. This email provider replaces the deprecated Exchange email provider.

You must have the following permissions to set up the Microsoft Graph integration:

- You must be a system administrator in the application to link the Dynamics 365 finance and operations environment to Microsoft Graph.
- You must be an administrator for your Microsoft Entra ID account. If you aren't the administrator, an administrative user must perform the first part of the configuration for you.

#### One-time registration process

To create an app, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/) by using an Azure tenant admin account.

    > [!NOTE]
    > The user who completes this procedure must have Admin rights for the tenant to register applications.

2. Go to **Microsoft Entra ID** \> **App registrations** \> **New application**.
3. Enter the following values:

    - **Name** – Enter the name of your app.
    - **Supported account types** – Enter only accounts that are directly in this organization (single tenant).

4. Select **Register**.
1. Make a note of the **Application (client) ID** value. You will use this value to connect to the Microsoft Graph service from your finance and operations environment.

    > [!IMPORTANT]
    > Be sure to capture the **Application (client) ID** value before you continue.

1. To add permissions, follow these steps:

    1. Select **Manage** \> **API permissions** \> **Add a permission** \> **Microsoft APIs** \> **Microsoft Graph**.
    1. Select **Application permissions**, and enable **Mail.Send**.

        > [!NOTE]
        > By default, the app should include the **User.Read** delegated permission for Microsoft Graph. If that permission is missing, you must add it from the delegated permissions.

    1. Select **Add permissions**.
    1. Select **Grant admin consent for** to allow emails to be sent.

1. To create a client secret, follow these steps:

    1. Select **Manage** \> **Certificates and secrets**.
    1. On the **Client secrets** tab, select **New client secret**.
    1. Enter a value in the **Description** and **Expires** fields, and then select **Add**.
    1. Make a note of the **Secret value** value. You will use this value to connect to the Microsoft Graph service from your Dynamics 365 finance and operations environments.

    > [!IMPORTANT]
    > Be sure to capture the **Secret value** value before you continue.

#### Restrict mailboxes

Administrators can modify mailbox access. For more information, see [Limiting application permissions to mailboxes](/graph/auth-limit-mailbox-access).

#### Configure Microsoft Graph in Dynamics 365 finance and operations apps

1. In Dynamics 365 finance and operations apps, open the **Email parameters** page.
1. On the **Microsoft Graph settings** tab, in the **Application ID** field, enter the **Application ID** value that you captured when you created the new app in the previous procedure.
1. In the **Application secret** field, enter the **Secret value** value that you captured when you created a client secret in the previous procedure.
1. Select **Save**.

#### Exchange email provider (Deprecated)

On the **Email parameters** page, an administrator can select **Exchange** as an interactive email provider and as the Batch email provider. This mail provider will use the current user's Exchange Online account to send emails. When it's used as the Batch email provider, the batch account will be used. No additional configuration is required.

If troubleshooting is required, ensure that it's possible to sign in to the current user's account, and that emails can be sent from that account to the intended recipients.

Note that the Exchange mail provider has the following limitations:

- It isn't supported for external users, because those users won't have Exchange accounts on the system tenant.
- It's available only in Microsoft-managed environments.

### Send email by using SMTP

On the **Email parameters** page, note the following settings on the **SMTP settings** tab.

#### Server information

| Field | Description |
|---|---|
| Outgoing mail server | The host name of the desired Simple Mail Transfer Protocol (SMTP) server. For [Microsoft 365 production](https://support.office.com/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including *.onmicrosoft.com accounts), use smtp.office365.com. (You can find this setting at outlook.office.com at **Settings** > **Mail** > **POP and IMAP**.) For Outlook/Hotmail, use smtp-mail.outlook.com. |
| SMTP port number | Typically, the port number should be set to 587 for secure transport. |
| SSL required | Determines whether secure transport is used. Typically, this is **Yes**, except for internal or troubleshooting scenarios. |  

> [!NOTE]
> If you are running into issues from too many emails being sent in a short period of time, it is recommended to utilize the **Email throttling** feature mentioned in the **Configuration tab** section above. If that doesn't resolve the issue, you may consider adding the appropriate IP addresses from the outbound IP safe list to your DNS SPF record authorizing Dynamics 365 finance and operations to send emails from your domain. For more information, see [Outbound IP safe list](../deployment/deploymentFAQ.md).

#### Authentication

| Field | Description |
|---|---|
| Authentication required | Determines whether a user name and password are needed to send emails. |
| **User name** and **Password** | If authentication is required, specify the appropriate mail account to send email from. All users need to provide the SMTP account **Send As** and **Send On Behalf Of** permissions to enable the ability to send SMTP mail. You can configure Send As permissions in the Microsoft 365 admin center (portal.office.com/Admin) at **Users** > **Active users** > **User** > **Edit mailbox permissions** > **Send email from this mailbox**. For more information, see [Enable sending email from another user's mailbox in Microsoft 365](https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E). |

> [!NOTE]
> Finance and operations apps don't support multifactor authentication or Modern auth (OAuth 2.0) for SMTP. The Microsoft Graph email provider can be used if a more modern integration is desired. Administrators might have to re-enable Basic authentication to allow for SMTP AUTH. For more information, see [Enable or disable SMTP AUTH](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission). Note that the [deprecation of Basic authentication for Exchange online](/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online#pop-imap-and-smtp-auth) only impacts the use of Office 365 SMTP servers. Other SMTP servers that still support basic authentication won't be impacted by this Office 365 deprecation.

## [Administrator] Email distributor batch process

Email that is sent directly from the server, without user interaction, via SMTP is sent by the **Email distributor batch** process. That batch process must be started to process the email queue. To start the process, open the **Email distributor batch** pane (**System administration** &gt; **Periodic tasks** &gt; **Email processing** &gt; **Batch**) and turn on **Batch processing**.

If the Microsoft Graph or Exchange provider is used, then the user account associated with the batch process (usually admin) will be the sender.

## [Administrator] User email

The default **send from** address for each user is pulled from the **Email** field on the **Users** page (**System administration** &gt; **Users** &gt; **Users**). Administrators can override this **send from** default if needed using the **Sender email** field on the **Options** page.

## [User] Email provider selection section on the Options page

The **Options** page can be opened via **Settings &gt; User options**. The **Email provider selection** section is on the **Account** tab.

| Field             | Description |
|-------------------|-------------|
| Email provider ID | Allows the user to select the email provider that should be used when sending an email. Selecting an option here is the equivalent of selecting **Do not ask again** in the **How would you like to send email** dialog box. Selecting the blank option **Prompt for which email provider to use** will cause the **How would you like to send email** dialog box to display when an email is going to be sent. |
| Sender email    | Allows the administrator to provide an email address override for the user in the **From** field of the email. By default, the email alias that is associated with the user account is used as the **From** field in new emails, but this user option email address will override that. When sending email via SMTP, the user needs to have appropriate **Send As** and **Send On Behalf Of** permissions configured in Exchange or on the SMTP server. **NOTE:**  You can configure **Send As** and **Send On Behalf Of** permissions in the Microsoft 365 admin center (portal.office.com/Admin) at **Users** &gt; **Active users** &gt; **User** &gt; **Edit mailbox permissions** &gt; **Send email from this mailbox**. For more information, see [Enable sending email from another user's mailbox in Microsoft 365](https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E). |

## [User] How would you like to send email dialog box (optional)

When an email is going to be sent, the user will see the **How would you like to send email** dialog box that will list the available options for sending email.

| Field                                                                  | Description |
|------------------------------------------------------------------------|-------------|
| Use an email app, such as Outlook                                      | Provides the user with a generated email (.eml) file. |
| Use Exchange email server                                              | Uses the Exchange Online server associated with the tenant. The **Exchange** mail provider is currently not supported outside the public cloud, including on-premises environments. |
| Use the system email client | Opens the **Send email** composition dialog box and then sends the resulting email via SMTP. |
| Do not ask again                                                       | If this field is not selected, the next time an email is sent the most recently selected option will be used and the dialog box will not open. |

## [User] Send email dialog box (optional)

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

1. In Microsoft Edge, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
1. Select **US-008 Sparrow Retail**.
1. Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
1. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
1. Click **OK** to accept the default values in the dialog box.
1. If you're prompted for the mail option to use, clear the **Do not ask again** check box (you can change this option from the **User options** page), select **Use an email app, such as Outlook**, and then click **OK**.
1. If you're using Microsoft Edge on your computer, open the email (.eml) file that is generated. If you're using Microsoft Edge on the VM, copy the file to your computer, and open it there.
1. Note the email address in the **To** field and the generated workbook attachment.

### Send mail via SMTP

Email workflows that are enabled via the SysEmail framework can also be created in a simple email dialog box and then sent via Simple Mail Transfer Protocol (SMTP).

1. Go to the **Email parameters** page.
1. Click **SMTP settings**.
1. Set the **Outgoing mail server** to the desired SMTP server:

    - For [Microsoft 365 production](https://support.office.com/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including \*.onmicrosoft.com accounts) use smtp.office365.com. (Find this setting via outlook.office.com, at **Settings** &gt; **Mail** &gt; **POP and IMAP**.)
    - For Outlook/Hotmail use smtp-mail.outlook.com.

1. Set the user name and password to an appropriate email account and password.
1. Leave **SSLRequired** turned on, and leave **SMTP port number** set to **587**.
1. Click **Save**.
1. In Microsoft Edge, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
1. Select **US-008 Sparrow Retail**.
1. Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
1. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
1. Click **OK** to accept the default values in the dialog box.
1. If you're prompted for the mail option to use, select **Use the Microsoft Dynamics 365 Finance email client**, and then click **OK**.
1. To receive the test message, change the **To address** to your email address.

    Ensure that the account specified in the SMTP settings is able to **Send As** and **Send On Behalf Of** your email account. The easiest way to ensure this is to use your email account in the SMTP settings.

1. Enter a subject and body for the message.
1. Click **Send**. The message should be delivered in one to five minutes.

## [Administrator] Workflow email notifications

Workflow email configuration is a collection of related settings that work in conjunction.

### Workflow email notification setup

1. Verify email settings:

    1. Go to **System administration** \> **Setup** \> **Email** \> **Email parameters**.
    1. Verify that SMTP is enabled.
    1. Set the SMTP mail server settings.

1. Verify that the email batch process is running:

    1. Go to **System administration** \> **Periodic tasks** \> **Email processing** \> **Email distributor batch**.
    1. Enable the **Batch processing** option.
    1. Optionally, adjust the recurrence of the email process:

        1. Select **No end date** to adjust all recurrences of the email batch process.
        1. Adjust the count.
        1. Adjust to run every minute if needed.

1. Verify workflow notification system email templates:

    1. Go to **System administration** \> **Setup** \> **Email** \> **System email templates** (for system-wide templates).
    1. Verify that the **Sender email** field is set and valid.

1. Verify workflow notification organization email templates:

    1. Go to **Organization administration** \> **Setup** \> **Organization email templates** (for organization-specific templates).
    1. Verify that the **Sender email** field is set and valid.

1. Verify that the user can receive email notifications:

    1. Go to **Settings** \> **User options**.
    1. Go to the **Account** tab.

       1. Set the **Email provider ID** (for example, SMTP).
       1. Optionally, set a **Sender email** override if the default **send from** address should not be used for the current user.

    1. Navigate to the **Workflow** tab. Set the option to send notifications in email to **Yes**.

1. Verify that the workflow system will send email notifications:

    For each workflow that should have a notification, open the workflow properties in the workflow editor.

    1. Click **Basic settings**. Adjust the email template for the workflow notifications.
    1. Click **Notifications**.

        1. Enable the events for which a user should be notified.
        1. Set the recipient of the workflow notification for each event notification that is enabled.

    1. On a workflow approval element for which a user should be notified:

        1. Go to **Properties**.
        1. Enable the events for which a user should be notified.
        1. Set the recipient of the workflow notification for each event notification that is enabled.

### Workflow email notification testing

The testing for email notifications is to simply trigger the notification and then check for it.

1. Submit a workflow that has been set up for email notifications.
1. Check the workflow history to make sure that a workflow work item was assigned to the expected user.
1. Check the status of the pending email notification in **System administration** \> **Periodic tasks** \> **Email processing** \> **Batch email sending status**.

    If the email fails to be sent, make sure that the SMTP mail account can be opened.

1. Check for the email notification in the appropriate inbox.

## Troubleshooting

### Common issues with sending email

There are some standard processes that can help you troubleshoot the configuration of email settings.

| &nbsp; | &nbsp; |
|---|---|
| <span id="verify-email-settings">**Verify email settings, and send a test email.**</span> | 1. Go to **System administration > Setup > Email > Email parameters**. 1. Verify that SMTP is enabled. 1. Verify the settings of the SMTP mail server. 1. Sign in to the SMTP account in a separate window to make sure that the account and password are correct. 1. Send a test email by going to **System administration > Setup > Email > Email parameters > Test email**. |
| <span id="verify-email-batch-process">**Verify that the email batch process is running.**</span> | 1. Go to **System administration > Periodic tasks > Email processing > Batch**. 1. Make sure that the **Batch processing** option is set to **Yes**. 1. Review the recurrence of the email process: 1. Select **No end date** to adjust all recurrences of the email batch process. 1. Adjust the count as needed. |
| <span id="review-status">**Review the status of batch emails.**</span> | 1. Go to **System administration > Periodic tasks > Email processing > Batch email sending status**. 1. Verify that emails are being sent from the correct account. If the account is incorrect, you must adjust settings such as user options, system templates, or organization templates, as needed. 1. Verify that all email user accounts have been granted **Send As** permission for the configured SMTP account (see [Verify that all email accounts have appropriate Send As permissions](#sendas_permissions) later in this table). |
| <span id="review-errors">**Review any errors on the Email history page.**</span> | 1. Go to **System administration > Setup > Email > Email history**. The **Email history** page lets administrators review all sent emails and also any errors that prevented an email from being sent. It shows both interactive and non-interactive/batch emails. 1. For any emails where the **Email status** value is **Failed**, review the error message on the **Failure details** tab, and determine whether corrective actions should be taken. Some of these errors are covered later in this article. |
| <span id="sendas_permissions">**Verify that all email accounts have appropriate Send as permissions.**</span> | In the Microsoft 365 admin center, verify that all user mail accounts that will be used to send emails have **Send As** and **Send On Behalf Of** permissions for the configured SMTP account. For more information, see [Give mailbox permissions to another user in Microsoft 365](/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user). |
| <span id="verify-user-mailboxes">**Verify user mailboxes.**</span> | Consider signing in to the affected (or all) user mailboxes to verify that they are valid and can be accessed by using sign-in. |

### Specific Microsoft Graph/Exchange email issues

- **<span id="unauthorized-forbidden-error">"(401) Unauthorized" or "(403) Forbidden" error when email is sent via Exchange</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | This issue might indicate an invalid or incorrectly set up mailbox in Office 365. |
    | **Fix** | To fix this issue, make sure that the specified user exists in Office 365 and has appropriate permissions. To find the affected users, follow these steps: 1. Open the **Email history** page. 1. Add a filter for **Failed** emails to the **Email status** field. 1. Make a note of the value in the **Email sender** field. This field shows the user that Exchange is indicating isn't a valid or correctly permissioned user in Office 365. |

- **<span id="404-not-found">"(404) Not found" error when email is sent via Exchange</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | This issue indicates that no mailbox exists for the user account in Exchange. |
    | **Fix** | To fix this issue, make sure that the specified user exists in Office 365 and has appropriate permissions, or use alternate user accounts that have valid Exchange mailboxes. To find the affected users, follow these steps: 1. Open the **Email history** page. 1. Add a filter for **Failed** emails to the **Email status** field. 1. Make a note of the value in the **Email sender** field. This field shows the user that doesn't have a mailbox in Exchange. |

### Specific SMTP email issues

If you continue to experience issues when email is sent via SMTP, you may be running into one of the specific errors below. If not, consider entering the SMTP account information in a tool such as [SMTPer.net](https://www.smtper.net/) to verify that the SMTP server and account are valid and working correctly.

- **<span id="single-label-domain-not-accepted-error">SMTP emails fail to be sent with "Recipient addresses in single label domains not accepted"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | An email failed to be sent because a recipient is using a single-label domain, but Office 365 doesn't support single-label domains. Single-label domains are Domain Name System (DNS) names that don't contain a suffix such as .com, .corp, .net, or .org. For example, contoso is a single-label domain. However, contoso.com, contoso.net, and contoso.local aren't single-label domains. |
    | **Fix** | Specify alternate addresses for email recipients that aren't single-label domains. |

- **<span id="mailbox-full-error">SMTP emails fail to be sent with "Mailbox full"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | An email failed to be sent because at least one recipient's mailbox is full. For more information, see [Error (554 5.2.2 mailbox full) when sending email to mail-enabled public folders in Office 365](/exchange/troubleshoot/email-delivery/cannot-send-mail-mepf). |
    | **Fix** | Use an alternate address for the recipient, or contact the recipient by using alternate means before you try again. |

- **<span id="authentication-unsuccessful-error">SMTP emails fail to be sent with "Authentication unsuccessful, the request did not meet the criteria to be authenticated successfully"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | An email failed to be sent because additional criteria are required to successfully authenticate the SMTP user account. These additional criteria might be required because multifactor authentication (MFA) is configured. However, finance and operations apps don't currently support MFA. |
    | **Fix** | Adjust the user account configuration as appropriate in Office 365 before you try again. For more information, see [Fix issues with printers, scanners, and LOB applications that send email using Microsoft 365 or Office 365](/exchange/mail-flow-best-practices/fix-issues-with-printers-scanners-and-lob-applications-that-send-email-using-off#error-authentication-unsuccessful). |

- **<span id="smtpclientauthentication-disabled-error">SMTP emails fail to be sent with "Authentication unsuccessful, SmtpClientAuthentication is disabled for the Mailbox"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | An email failed to be sent because SMTP client authentication is disabled for the SMTP user account. |
    | **Fix** | Enable SMTP client authentication for the user account in Office 365 before you try again. For more information, see [Enable or disable authenticated client SMTP submission](https://aka.ms/smtp_auth_disabled). |

- **<span id="smtp-emails-fail-to-send-with-if-your-smtp-server-doesnt-support-authentication-please-clear-the-smtp-user-name-and-password">SMTP emails fail to be sent with "If your SMTP server doesn't support authentication, please clear the SMTP user name and password"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | This issue is related to migration from the .NET SMTP mail client (which is now obsolete) to MailKit per Microsoft recommendations. This migration causes a change in the way that SMTP user names and passwords are handled in situations where the mail server didn't support authentication. Previously, if an SMTP user name was provided, but the server didn't support authentication, the .NET SMTP mail client ignored the provided user name and password, and continued without authentication. This behavior led some customers to incorrectly believe that they were using an authenticated mail server. In MailKit, authentication is required if a user name is provided. This requirement will trigger an error for mail servers that don't support authentication, and emails will fail to be sent. |
    | **Fix** | The user must go to the **Email parameters** page (**System administration > Setup > Email**) and clear the **User name** and **Password** fields on the **SMTP settings** tab. |

- **<span id="smtp-emails-fail-to-send-with-5757-smtp-error-or-an-indication-that-youre-not-authenticated-or-authentication-is-required">SMTP emails fail to be sent with an "5.7.57 SMTP" error, or an indication that either you aren't authenticated or authentication is required</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | The mail server is indicating that the SMTP user credentials aren't valid. |
    | **Fix** | Verify that the SMTP user credentials are correct. |

- **<span id="smtp-emails-fail-to-send-with-microsoftdynamicsaxxppsecuritycryptoencryptionexception-encryption-error-occurred-with-exception">SMTP emails fail to be sent with "Microsoft.Dynamics.Ax.Xpp.Security.CryptoEncryptionException: Encryption error occurred with exception"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | The SMTP password is encrypted by using a key that is specific to a single environment. This error typically occurs when the password can no longer be decrypted after database migration between environments. |
    | **Fix** | Clear and reenter the SMTP password on the **SMTP settings** tab of the **Email parameters** page. |

- **<span id="smtp-emails-fail-to-send-with-client-does-not-have-permissions-to-send-as-this-sender">SMTP emails fail to be sent with "Client does not have permissions to send as this sender"</span>**

    | &nbsp; | &nbsp; |
    |---|---|
    | **Explanation** | This issue is usually caused by incorrect setup of the **Send As** permissions for the email account. |
    | **Fix** | Ensure that the email account has appropriate **Send As** permissions. For more information, see [Verify that all email accounts have appropriate Send As permissions](#sendas_permissions) earlier in this article. |

## Frequently asked questions

### Where do workflow email templates come from?

The email templates will be sourced from either system email templates or organization email templates depending on whether the workflow is a system-level (not company specific) or organization-level (company specific) workflow.

### What email limits apply when using Microsoft Graph, Exchange, or SMTP?  

The system communicates with Microsoft Graph, Exchange, or an SMTP server like a typical email client, so standard behavior and limits apply. For example, standard [Exchange Online receiving and sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) apply.

## Additional resources

[Troubleshoot the Office integration](../office-integration/office-integration-troubleshooting.md)

[Office integration tutorial](../office-integration/office-integration-tutorial.md)

[Configure email functionality in Microsoft Dynamics AX [AX 2012]](/dynamicsax-2012/appuser-itpro/configure-email-functionality-in-microsoft-dynamics-ax)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
