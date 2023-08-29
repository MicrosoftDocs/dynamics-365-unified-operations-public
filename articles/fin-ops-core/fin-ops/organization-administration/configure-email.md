---
# required metadata

title: Configure and send email
description: The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. 
author: jasongre
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysEmailParameters
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 268274
ms.assetid: 194ca8fd-5e20-4464-9c85-08d2b5ff63ca
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Configure and send email

[!include [banner](../includes/banner.md)]

The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. This article is divided into sections for administrators and users to make it easy to find relevant information.

Both administrators and users set the behavior of the email subsystem.

## [Administrator] Email parameters page 

### Configuration tab
On the **Email parameters** page, note the following settings on the **Configuration** tab.

| Field                 | Description |
|-----------------------|-------------|
| Batch email provider  | Specifies which email provider will be used to send emails that are sent by processes in a batch or non-interactive manner. The Exchange provider will use the account associated with the batch process. |
| Attachment size limit | Specifies the maximum size of a single email that can be sent via the email subsystem. |

The **Email history** section serves two purposes. First, it provides an entry point to the **Email history** page, where administrators can review all sent emails and also any errors that prevented an email from being sent. Second, it lets you configure how long email history is maintained. By default, the last 30 days of email history are retained. You can adjust this period by changing the value of the **Number of days to retain email history** field to a non-zero number. If you set the value to **0** (zero), the default number and behavior are used.

The **Email throttling** section enables non-interactive email providers (such as the batch email provider) to adhere to a per-minute sending limit. This feature can help prevent some errors if the system tries to send more emails than the provider allows. Specifically, if an email can't originally be sent because the per-minute sending limit has been reached, the send attempt for the email will be deferred for up to one minute. After ten deferrals, the system will try to send the email regardless. You can remove the per-minute sending limit from a provider by resetting the **per-minute email sending limit** field to **0**. The sending limits for the Office 365 SMTP email provider is automatically set according to the [Exchange Online sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits). Manual configuration is required for all other email providers. 

> [!NOTE]
> Use of the **Email throttling** feature isn't recommended for the Exchange email provider, because it has its own throttling mechanism. Therefore, if you're using Exchange, you should ensure that the **per-minute email sending limit** field for it is set to **0**.

### SMTP settings tab
On the **Email parameters** page, note the following settings on the **SMTP settings** tab.

#### Server information
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
    <td>The host name of the desired Simple Mail Transfer Protocol (SMTP) server.
      <ul>
        <li>For <a href="https://support.office.com/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c">Microsoft 365 production</a> (including *.onmicrosoft.com accounts), use smtp.office365.com. (You can find this setting at outlook.office.com at <strong>Settings</strong> &gt; <strong>Mail</strong> &gt; <strong>POP and IMAP</strong>.)</li>
        <li>For Outlook/Hotmail, use smtp-mail.outlook.com.</li>
      </ul>
    </td>
  </tr>
    
  <tr>
    <td>SMTP port number</td>
    <td>Typically, the port number should be set to 587 for secure transport.</td>
  </tr>

  <tr>
    <td>SSL required</td>
    <td>Determines whether secure transport is used. Typically, this is <strong>Yes</strong>, except for internal or troubleshooting scenarios.</td>
  </tr>
</tbody>
</table>  
  

#### Authentication

<table>
<thead>  
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
  <tr>
    <td>Authentication required</td>
    <td>Determines whether a user name and password are needed to send emails. </td>
  </tr>

  <tr>
    <td><strong>User name</strong> and <strong>Password</strong></td>
    <td>If authentication is required, specify the appropriate mail account to send email from. All users need to provide the SMTP account <strong>Send As</strong> and <strong>Send On Behalf Of</strong> permissions to enable the ability to send SMTP mail. You can configure Send As permissions in the Microsoft 365 admin center (portal.office.com/Admin) at <strong>Users</strong> &gt; <strong>Active users</strong> &gt; <strong>User</strong> &gt; <strong>Edit mailbox permissions</strong> &gt; <strong>Send email from this mailbox</strong>. For more information, see <a href="https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E">Enable sending email from another user's mailbox in Microsoft 365</a>.
    </td>
  </tr>
      
</tbody>

</table>

> [!NOTE]
> Finance and operations apps don't support multifactor authentication or Modern auth (OAuth 2.0) for SMTP. Administrators might have to re-enable Basic authentication to allow for SMTP AUTH. For more information, see [Enable or disable SMTP AUTH](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission). The Exchange mail provider can be used if a more modern integration is desired. Note that the [deprecation of Basic authentication for Exchange online](/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online#pop-imap-and-smtp-auth) doesn't affect the use of SMTP in finance and operations apps, because "SMTP AUTH will still be available when Basic authentication is permanently disabled."

## [Administrator] Email distributor batch process

Email that is sent directly from the server, without user interaction, via SMTP is sent by the **Email distributor batch** process. That batch process must be started to process the email queue. To start the process, open the **Email distributor batch** pane (**System administration** &gt; **Periodic tasks** &gt; **Email processing** &gt; **Batch**) and turn on **Batch processing**.

If the Exchange provider is used, then the user account associated with the batch process (usually admin) will be the sender.

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
12. If you're prompted for the mail option to use, select **Use the Microsoft Dynamics 365 Finance email client**, and then click **OK**.
13. To receive the test message, change the **To address** to your email address.

    Ensure that the account specified in the SMTP settings is able to **Send As** and **Send On Behalf Of** your email account. The easiest way to ensure this is to use your email account in the SMTP settings.

14. Enter a subject and body for the message.
15. Click **Send**. The message should be delivered in one to five minutes.

## [Administrator] Workflow email notifications

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

       1. Set the **Email provider ID** (for example, SMTP).
       2. Optionally, set a **Sender email** override if the default **send from** address should not be used for the current user.

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

    If the email fails to be sent, make sure that the SMTP mail account can be opened.

4. Check for the email notification in the appropriate inbox.

## Exchange mail provider

The **Email parameters** page allows an administrator to select **Exchange** as an interactive email provider and as the Batch email provider. The **Exchange** mail provider will use the current user's Exchange Online account to send emails. When used as the Batch email provider, the batch account will be used. No additional configuration is needed. 
If troubleshooting is needed, ensure that it's possible to sign in to the current user's account and that emails can be sent from that account to the intended recipients.

> [!IMPORTANT]
> The Exchange mail provider is: 
> -  Not supported for external users, as those users will not have Exchange accounts on the system tenant.
> -  Only available in Microsoft-managed environments. 

## Troubleshooting

### Common issues with sending email

There are some standard processes that can help you troubleshoot the configuration of email settings. 

<table>
  <tr>
    <th id="verify-email-settings">Verify email settings, and send a test email.</th>
    <td>
      <ol>
        <li>Go to <b>System administration &gt; Setup &gt; Email &gt; Email parameters</b>.</li>
        <li>Verify that SMTP is enabled.</li>
        <li>Verify the settings of the SMTP mail server.</li>
        <li>Sign in to the SMTP account in a separate window to make sure that the account and password are correct.</li>
        <li>Send a test email by going to <b>System administration &gt; Setup &gt; Email &gt; Email parameters &gt; Test email</b>.</li>
      </ol>
    </td>
  </tr>
  <tr>
    <th id="verify-email-batch-process">Verify that the email batch process is running.</th>
    <td>
      <ol>
        <li>Go to <b>System administration &gt; Periodic tasks &gt; Email processing &gt; Batch</b>.</li>
        <li>Make sure that the <b>Batch processing</b> option is set to <b>Yes</b>.</li>
        <li>Review the recurrence of the email process:
          <ol>
            <li>Select <b>No end date</b> to adjust all recurrences of the email batch process.</li>
            <li>Adjust the count as needed.</li>
          </ol>
        </li>
      </ol>
    </td>
  </tr>
  <tr>
    <th id="review-status">Review the status of batch emails.</th>
    <td>
      <ol>
        <li>Go to <b>System administration &gt; Periodic tasks &gt; Email processing &gt; Batch email sending status</b>.</li>
        <li>Verify that emails are being sent from the correct account.
          <p>If the account is incorrect, you must adjust settings such as user options, system templates, or organization templates, as needed.</p>
        </li>
        <li>Verify that all email user accounts have been granted <b>Send As</b> permission for the configured SMTP account (see <a href="#sendas_permissions">Verify that all email accounts have appropriate Send As permissions</a> later in this table).</li>
      </ol>
    </td>
  </tr>
  <tr>
    <th id="review-errors">Review any errors on the Email history page.</th>
    <td>
      <ol>        
        <li>Go to <b>System administration &gt; Setup &gt; Email &gt; Email history</b>.
          <p>The <b>Email history</b> page lets administrators review all sent emails and also any errors that prevented an email from being sent. It shows both interactive and non-interactive/batch emails.</p>
        </li>
        <li>For any emails where the <b>Email status</b> value is <b>Failed</b>, review the error message on the <b>Failure details</b> tab, and determine whether corrective actions should be taken. Some of these errors are covered later in this article.</li>
      </ol>
    </td>
  </tr>
  <tr>
    <th id="sendas_permissions">Verify that all email accounts have appropriate Send as permissions.</th>
    <td>In the Microsoft 365 admin center, verify that all user mail accounts that will be used to send emails have <b>Send As</b> and <b>Send On Behalf Of</b> permissions for the configured SMTP account. For more information, see <a href="/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user">Give mailbox permissions to another user in Microsoft 365</a>.</td>
  </tr>
  <tr>
    <th id="verify-user-mailboxes">Verify user mailboxes.</th>
    <td>Consider signing in to the affected (or all) user mailboxes to verify that they are valid and can be accessed by using sign-in.</td>
  </tr>
</table>

 ### Specific Exchange email issues

-  **<span id="unauthorized-forbidden-error">"(401) Unauthorized" or "(403) Forbidden" error when email is sent via Exchange</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>This issue might indicate an invalid or incorrectly set up mailbox in Office 365.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td><p>To fix this issue, make sure that the specified user exists in Office 365 and has appropriate permissions.</p>
        <p>To find the affected users, follow these steps:</p>
          <ol>
            <li>Open the <b>Email history</b> page.</li>
            <li>Add a filter for <b>Failed</b> emails to the <b>Email status</b> field.</li>
            <li>Make a note of the value in the <b>Email sender</b> field. This field shows the user that Exchange is indicating isn't a valid or correctly permissioned user in Office 365.</li> 
          </ol>        
        </td>
      </tr>
    </table>

-  **<span id="404-not-found">"(404) Not found" error when email is sent via Exchange</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>This issue indicates that no mailbox exists for the user account in Exchange.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td><p>To fix this issue, make sure that the specified user exists in Office 365 and has appropriate permissions, or use alternate user accounts that have valid Exchange mailboxes.</p>
        <p>To find the affected users, follow these steps:</p> 
          <ol>
            <li>Open the <b>Email history</b> page.</li>
            <li>Add a filter for <b>Failed</b> emails to the <b>Email status</b> field.</li>
            <li>Make a note of the value in the <b>Email sender</b> field. This field shows the user that doesn't have a mailbox in Exchange.</li> 
          </ol>        
        </td>
      </tr>
    </table>

### Specific SMTP email issues 

If you continue to experience issues when email is sent via SMTP, you may be running into one of the specific errors below. If not, consider entering the SMTP account information in a tool such as [SMTPer.net](https://www.smtper.net/) to verify that the SMTP server and account are valid and working correctly.

-  **<span id="single-label-domain-not-accepted-error">SMTP emails fail to be sent with "Recipient addresses in single label domains not accepted"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>An email failed to be sent because a recipient is using a single-label domain, but Office 365 doesn't support single-label domains. Single-label domains are Domain Name System (DNS) names that don't contain a suffix such as .com, .corp, .net, or .org. For example, contoso is a single-label domain. However, contoso.com, contoso.net, and contoso.local aren't single-label domains.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Specify alternate addresses for email recipients that aren't single-label domains.</td>
      </tr>
    </table>

-  **<span id="mailbox-full-error">SMTP emails fail to be sent with "Mailbox full"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>An email failed to be sent because at least one recipient's mailbox is full. For more information, see <a href="/exchange/troubleshoot/email-delivery/cannot-send-mail-mepf">Error (554 5.2.2 mailbox full) when sending email to mail-enabled public folders in Office 365</a>.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Use an alternate address for the recipient, or contact the recipient by using alternate means before you try again.</td>
      </tr>
    </table>

-  **<span id="authentication-unsuccessful-error">SMTP emails fail to be sent with "Authentication unsuccessful, the request did not meet the criteria to be authenticated successfully"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>An email failed to be sent because additional criteria are required to successfully authenticate the SMTP user account. These additional criteria might be required because multifactor authentication (MFA) is configured. However, finance and operations apps don't currently support MFA.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Adjust the user account configuration as appropriate in Office 365 before you try again. For more information, see <a href="/exchange/mail-flow-best-practices/fix-issues-with-printers-scanners-and-lob-applications-that-send-email-using-off#error-authentication-unsuccessful">Fix issues with printers, scanners, and LOB applications that send email using Microsoft 365 or Office 365</a>.</td>
      </tr>
    </table>

-  **<span id="smtpclientauthentication-disabled-error">SMTP emails fail to be sent with "Authentication unsuccessful, SmtpClientAuthentication is disabled for the Mailbox"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>An email failed to be sent because SMTP client authentication is disabled for the SMTP user account.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Enable SMTP client authentication for the user account in Office 365 before you try again. For more information, see <a href="https://aka.ms/smtp_auth_disabled">Enable or disable authenticated client SMTP submission</a>.</td>
      </tr>
    </table>

- **<span id="smtp-emails-fail-to-send-with-if-your-smtp-server-doesnt-support-authentication-please-clear-the-smtp-user-name-and-password">SMTP emails fail to be sent with "If your SMTP server doesn't support authentication, please clear the SMTP user name and password"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>This issue is related to migration from the .NET SMTP mail client (which is now obsolete) to MailKit per Microsoft recommendations. This migration causes a change in the way that SMTP user names and passwords are handled in situations where the mail server didn't support authentication. Previously, if an SMTP user name was provided, but the server didn't support authentication, the .NET SMTP mail client ignored the provided user name and password, and continued without authentication. This behavior led some customers to incorrectly believe that they were using an authenticated mail server. In MailKit, authentication is required if a user name is provided. This requirement will trigger an error for mail servers that don't support authentication, and emails will fail to be sent.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>The user must go to the <b>Email parameters</b> page (<b>System administration &gt; Setup &gt; Email</b>) and clear the <b>User name</b> and <b>Password</b> fields on the <b>SMTP settings</b> tab.</td>
      </tr>
    </table>

-  **<span id="smtp-emails-fail-to-send-with-5757-smtp-error-or-an-indication-that-youre-not-authenticated-or-authentication-is-required">SMTP emails fail to be sent with an "5.7.57 SMTP" error, or an indication that either you aren't authenticated or authentication is required</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>The mail server is indicating that the SMTP user credentials aren't valid.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Verify that the SMTP user credentials are correct.</td>
      </tr>
    </table>

- **<span id="smtp-emails-fail-to-send-with-microsoftdynamicsaxxppsecuritycryptoencryptionexception-encryption-error-occurred-with-exception">SMTP emails fail to be sent with "Microsoft.Dynamics.Ax.Xpp.Security.CryptoEncryptionException: Encryption error occurred with exception"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>The SMTP password is encrypted by using a key that is specific to a single environment. This error typically occurs when the password can no longer be decrypted after database migration between environments.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Clear and reenter the SMTP password on the <b>SMTP settings</b> tab of the <b>Email parameters</b> page.</td>
      </tr>
    </table>

-  **<span id="smtp-emails-fail-to-send-with-client-does-not-have-permissions-to-send-as-this-sender">SMTP emails fail to be sent with "Client does not have permissions to send as this sender"</span>**

    <table>
      <tr>
        <th>Explanation</th>
        <td>This issue is usually caused by incorrect setup of the <b>Send As</b> permissions for the email account.</td>
      </tr>
      <tr>
        <th>Fix</th>
        <td>Ensure that the email account has appropriate <b>Send As</b> permissions. For more information, see <a href="#sendas_permissions">Verify that all email accounts have appropriate Send As permissions</a> earlier in this article.
      </tr>
    </table>

## Frequently asked questions

### Where do workflow email templates come from?

The email templates will be sourced from either system email templates or organization email templates depending on whether the workflow is a system-level (not company specific) or organization-level (company specific) workflow.

### What email limits apply when using Exchange or SMTP?  

The system communicates with Exchange or an SMTP server like a typical email client, so standard behavior and limits apply. For example, standard [Exchange Online receiving and sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) apply.


## Additional resources

[Troubleshoot the Office integration](../../dev-itpro/office-integration/office-integration-troubleshooting.md)

[Office integration tutorial](../../dev-itpro/office-integration/office-integration-tutorial.md)

[Configure email functionality in Microsoft Dynamics AX [AX 2012]](/dynamicsax-2012/appuser-itpro/configure-email-functionality-in-microsoft-dynamics-ax)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

