---
# required metadata

title: Configure and send email
description: The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. This topic is divided into sections for administrators and users. This topic is divided into sections for administrators and users to make it easy to find relevant information.
author: ChrisGarty
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
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

The behavior of the email subsystem is influenced by a combination of administrator configuration, user configuration, and user choices. This topic is divided into sections for administrators and users. This topic is divided into sections for administrators and users to make it easy to find relevant information.

In Dynamics 365 for Operations, both administrators and users set the behavior of the email subsystem.

## Administrator: Email parameters page
On the **Email parameters** page, note the following settings on the **Email providers** tab.

| Field                     | Description                                                                                                                 |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Batch email provider**  | Specifies which email provider will be used to send emails that are sent by processes in a batch or non-interactive manner. |
| **Attachment size limit** | Specifies the maximum size of a single email that can be sent via the email subsystem.                                      |

On the **Email parameters** page, note the following settings on the **SMTP settings** tab.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Outgoing mail server </strong></td>
<td>The host name of the desired SMTP server.
<ul>
<li>For <a href="https://support.office.com/en-us/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c">Office 365 production</a> (including *.onmicrosoft.com accounts) use smtp.office365.com. (You can find this setting at outlook.office.com at <strong>Settings</strong> &gt; <strong>Mail</strong> &gt; <strong>POP and IMAP</strong>.)</li>
<li>For Outlook/Hotmail use smtp-mail.outlook.com.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SMTP port number</strong></td>
<td>Typically, the port number should be set to 587 for secure transport.</td>
</tr>
<tr class="odd">
<td><strong>User name</strong> and <strong>Password</strong></td>
<td>Specify, as needed, to send the email via the appropriate mail account. All users need to provide the SMTP account <strong>Send As</strong> or <strong>Send On Behalf Of</strong> permissions to enable the ability to send Simple Mail Transfer Protocol (SMTP) mail. You can configure Send As permissions in the Office 365 admin center (portal.office.com/Admin), at <strong>Users</strong> &gt; <strong>Active users</strong> &gt; <strong>User</strong> &gt; <strong>Edit mailbox permissions</strong> &gt; <strong>Send email from this mailbox</strong>. For more information, see <a href="https://support.office.com/en-us/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E">Enable sending email from another user’s mailbox in Office 365</a>.</td>
</tr>
<tr class="even">
<td><strong>Specify if SSL is required</strong></td>
<td>Determines whether secure transport is used. Typically, this is <strong>Yes</strong>, except for internal or troubleshooting scenarios.</td>
</tr>
</tbody>
</table>

## Administrator: Email Distributor batch process
Email that is sent directly from the server, without user interaction, via SMTP is sent by the **Email distributor batch** process. That batch process must be started to process the email queue. To start the process, open the **Email distributor batch** pane (**System administration** &gt; **Periodic tasks** &gt; **Email processing** &gt; **Batch**) and turn on **Batch processing**.

## Administrator: User email
The default email address for each user is pulled from the **Email** field on the **Users** page (**System administration** &gt; **Users** &gt; **Users**). An email address should be specified for each user for sign in, so this field should be populated. Users can override this default if needed.

## User: Email provider selection section on the Options page
The **Options** page can be opened via **Settings &gt; Options**. The **Email provider selection** section is on the **Account** tab.

| Field                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Email provider ID** | Allows the user to select the email provider that should be used when sending an email. Selecting an option here is the equivalent of selecting **Do not ask again** in the **How would you like to send email** dialog box. Selecting the blank option **Prompt for which email provider to use** will cause the **How would you like to send email** dialog box to display when an email is going to be sent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Email**             | Allows the user to provide an email address override for the **From** field of the email. By default, the email alias that associated with the user account is used as the **From** field in new emails, but this user option email address will override that. When sending email via SMTP the user needs to have appropriate **Send As** or **Send On Behalf Of** permissions configured in Exchange or on the SMTP server. **Note:** You can configure **Send As** permissions in the Office 365 admin center (portal.office.com/Admin) at **Users** &gt; **Active users** &gt; **User** &gt; **Edit mailbox permissions** &gt; **Send email from this mailbox**. For more information, see [Enable sending email from another user’s mailbox in Office 365](https://support.office.com/en-us/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E). |

## User (optional): How would you like to send email dialog box
When an email is going to be sent, the user will see the **How would you like to send email** dialog box that will list the available options for sending email.

| Field                                                          | Description                                                                                                                                    |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **Use an email app, such as Outlook**                          | Provides the user with a generated email (.eml) file.                                                                                          |
| **Use Exchange email server**                                  | Uses the Exchange Server associated with the tenant. The email will be sent using Exchange Web Services (EWS).                                 |
| **Use the Microsoft Dynamics 365 for Operations email client** | Opens the **Send email** composition dialog box and then sends the resulting email via SMTP.                                                   |
| **Do not ask again**                                           | If this field is not selected, the next time an email is sent the most recently selected option will be used and the dialog box will not open. |

## User (optional): Send email dialog box
The **Send email **dialog box is opened to allow the user to edit the contents of the email that will be sent. Some of the following fields will be pre-populated in this window.

| Field                                                     | Description                                                                                                                                        |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **From**                                                  | Populated from the **Email** field on the **Options** page.                                                                                        |
| **To**, **Cc**, **Bcc**, **Subject**, and **Body** fields | Populated with values specified by the process that initiated the sending of the email. These fields can be edited as needed by the user.          |
| **Attachments list**                                      | May be populated with attachments specified by the process that initiated the sending of the email. This list can be edited as needed by the user. |

When the email is ready to be sent, the **Send** button will cause the email to be sent via SMTP.

### Usage scenarios to verify if email is configured correctly

##### Send mail via a local mail client

Email workflows that are enabled via the SysEmail framework can generate email messages (.eml files) that contain attachments. You can then send these messages via Microsoft Outlook or another email client.

1.  In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
2.  Select **US-008 Sparrow Retail**.
3.  Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
4.  Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
5.  Click **OK** to accept the default values in the dialog box.
6.  If you’re prompted for the mail option to use, clear the **Do not ask again** check box (you can change this option from the **User options** page), select **Use an email app, such as Outlook**, and then click **OK**.
7.  If you’re using Internet Explorer on your computer, open the email (.eml) file that is generated. If you’re using Internet Explorer on the VM, copy the file to your computer, and open it there.
8.  Note the email address in the **To** field and the generated workbook attachment.

##### Send mail via SMTP

Email workflows that are enabled via the SysEmail framework can also be created in a simple email dialog box and then sent via Simple Mail Transfer Protocol (SMTP).

1.  In Dynamics 365 for Operations, go to the **Email parameters** page.
2.  Click **SMTP settings**.
3.  Set the **Outgoing mail server** to the desired SMTP server:
    -   For [Office 365 production](https://support.office.com/en-us/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including \*.onmicrosoft.com accounts) use smtp.office365.com. (Find this setting via outlook.office.com, at **Settings** &gt; **Mail** &gt; **POP and IMAP**.)
    -   For Outlook/Hotmail use smtp-mail.outlook.com.

4.  Set the user name and password to an appropriate email account and password.
5.  Leave **SSLRequired** turned on, and leave **SMTP port number** set to **587**.
6.  Click **Save**.
7.  In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
8.  Select **US-008 Sparrow Retail**.
9.  Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
10. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
11. Click **OK** to accept the default values in the dialog box.
12. If you’re prompted for the mail option to use, select **Use the Microsoft Dynamics 365 for Operations email client**, and then click **OK**.
13. To receive the test message, change the **To address** to your email address.
    -   Ensure that the account specified in the SMTP settings is able to **Send As** or **Send On Behalf Of** your email account. The easiest way to ensure this to use your email account in the SMTP settings.

14. Enter a subject and body for the message.
15. Click **Send**. The message should be delivered in one to five minutes.


See also
--------

[Office integration troubleshooting](https:/docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/office-integration/office-integration-troubleshooting)

[Office integration tutorial](https:/docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/office-integration/office-integration-tutorial)

[Configure email functionality in Microsoft Dynamics AX [AX 2012]](https://technet.microsoft.com/en-us/library/aa834374.aspx)

