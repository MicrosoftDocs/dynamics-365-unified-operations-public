---
title: Develop email experiences by using the SysMailer framework
description: Learn about how you can use the SysMailer framework to send email, including various scenarios and code examples.
author: ChrisGarty
ms.author: cgarty
ms.topic: article
ms.date: 05/23/2018
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-11-21
ms.dyn365.ops.version: Platform update 4
---

# Develop email experiences by using the SysMailer framework

[!include [banner](../includes/banner.md)]

## Sending emails

The SysMailer framework is a new, extensible way to send email. It replaces all previous application programming interfaces (APIs) for mail, such as CDO.Messaging (SysMailer), MAPI (SysINetMail), and Outlook COM (SmmOutlookEmail). Those older mail APIs won't work correctly in finance and operations applications. By taking advantage of the SysPlugin framework and several .NET technologies, SysMailer provides a configurable experience for users and enables the application consumers to remain agnostic to the email option that users use to send email.

The SysMailer framework consists of a factory class that is used to retrieve an email provider, a set of email providers that send messages, a message builder that builds the messages, and the forms that are related to configuring and interacting with the email providers. To consume the SysMailer framework, an application developer primarily uses the **SysMailerFactory** and **SysMailerMessageBuilder** classes. The email provider factory is used to retrieve interactive or non-interactive email providers, so that multiple messages can be sent at the same time, or so that a message can be sent directly. The email providers expect the messages that they send to be encapsulated in .NET **System.Net.Mail.MailMessage** objects. The message builder class is used to build the .NET object that is passed to the email provider.

### Scenarios

This article describes three scenarios:

- Sending an interactive message
- Sending a non-interactive (batch) message
- Sending multiple non-interactive (batch) messages

#### Sending an interactive message

The following example is taken from the **CustCollectionsEmail** class. It demonstrates multiple features of the framework, such as the ability to chain message builder calls, conditionally set the sender address ("from" address), and add attachments.

```xpp
using (System.IO.Stream attachmentStream = this.generateAttachment())
{
    var messageBuilder = new SysMailerMessageBuilder();
    messageBuilder.addTo(context.parmEmailAddress())
    .setSubject(emailSubject)
    .setBody(SysEmailMessage::stringExpand(emailBody,
    SysEmailTable::htmlEncodeParameters(templateTokens)));
    if (emailSenderAddr)
    {
        messageBuilder.setFrom(emailSenderAddr, emailSenderName);
    }
    else if (custParameters.CollectionsOMTeam)
    {
        var collectionsEmail = OMTeam::find(custParameters.CollectionsOMTeam).primaryEmail();
        if (strLen(collectionsEmail) > 0)
        {
            messageBuilder.setFrom(collectionsEmail);
        }
    }
    if (attachmentStream != null)
    {
        messageBuilder.addAttachment(
            attachmentStream,
            strFmt('%1%2', strReplace(DateTimeUtil::toStr(DateTimeUtil::utcNow()), ':', ''), '.xlsx'));
    }
    SysMailerFactory::sendInteractive(messageBuilder.getMessage());
}
```

#### Sending a non-interactive (batch) message

The following example is taken from the **VendRequestCompanyWorkflowManager** class. It shows how you can send a single message non-interactively.

```xpp
// The vendor <vendor name> has been approved and has been added to the vendor master.
messageText = strFmt("@SYS134393", DirPartyTable::findRec(vendRequestCompany.VendParty).Name);
// Request
var messageBuilder = new SysMailerMessageBuilder();
messageBuilder.setFrom(senderEmail)
    .addTo(recipientEmail)
    .setSubject("@SYS130372")
    .setBody(messageText);
SysMailerFactory::sendNonInteractive(messageBuilder.getMessage());
```

#### Sending multiple non-interactive (batch) messages

The following example is taken from the **UserAdAddManager** class. It shows how you can get an instance of a batch email provider before you iterate over a list of emails to send.

```xpp
var mail = SysMailerFactory::getNonInteractiveMailer();
var messageBuilder = new SysMailerMessageBuilder();
for (i = 1; i <= conLen(_notifyCon); i++)
{
    notifyEmailsStr = conPeek(_notifyCon, i);
    select firstonly RecId, Email from sysUser where sysUser.Id == notifyEmailsStr;
    if (sysUser.RecId && sysUser.Email != '')
    {
        messageBuilder.reset()
            .setFrom(_emailFrom)
            .addTo(sysUser.Email)
            .setSubject("@SYS129183")
            .setBody(errorStr);
        mail.sendNonInteractive(messageBuilder.getMessage());
        delete_from tmpUserErrorNotification;
    }
}
```

### Important considerations

- A sender address ("from" address) is required when messages are sent to an email provider. A receiver address ("to" address) is required when messages are sent non-interactively. If these conditions aren't met, the framework throws an exception. If **getMessage** is called on the message builder before any call to **setFrom** is made, the builder tries to set the sender address to the current user's email address or network alias.
- When messages are sent, the way that the sender address ("from" address) is used depends on the provider:

    - **EML provider:** The sender address is removed from the message before the message is opened in the user's email client. Therefore, the email client can set the sender address to the default account that is configured for sending mail.
    - **SMTP provider:** The Simple Mail Transfer Protocol (SMTP) server must be configured to allow messages to be sent by using the sender address. In other words, the SMTP server must allow the impersonation of emails that are sent from it. Otherwise, the SMTP server might prevent the messages from being sent, flag them as spam, and so on.

- When messages are sent, the framework returns a Boolean value that indicates whether the operation to send the message was successful. However, it doesn't report any messages to the Action Center when the operation is successful. You decide whether messages are shown in the Action Center.
- By default, the body of all messages that are sent is in rich-text (HTML) format. If an application scenario requires that plain text be used to maintain newline spacing, you can pass **false** to the optional **\_isHtml** parameter of the **setBody** method on the message builder.

## Adding a new email provider

You can add email providers by using the pluggable framework. When you use the factory class and interfaces, new email providers immediately become available for use across all relevant application scenarios. Examples of email providers can be found in the existing provider implementations, SysMailerEML and SysMailerSMTP, and also in an existing tutorial implementation, Tutorial\_SysMailerMailTo. The examples that follow are excerpts from the implementation of the SysMailerEML email provider.

To implement an email provider, you must create an implementation class that has the following properties:

- The class must have the appropriate **Export** attributes.
- The class must implement the base **SysIMailer** methods, **getId** and **getDescription**.
- The class must implement the **SysImailerInteractive** interface, the **SysIMailerNonInteractive** interface, or both interfaces.

### Specify attributes for the implementation class

The first step is to specify attributes for the implementation class. The class must have two attributes:

- **ExportAttribute** – The framework uses this attribute to discover the plug-in. The attribute specifies that the plug-in is an implementation of **SysIMailer** and therefore part of the SysMailer framework.
- **ExportMetadataAttribute** – The framework uses this attribute to find specific instances of a plug-in that have specific metadata. The attribute specifies the ID of the email provider, so that a single provider can be discovered quickly. **No two email providers should ever have the same ID.**

```xpp
using System.IO;
using System.Net.Mail;
using System.Text.RegularExpressions;
#define.SysMailerEML_ID('EML')
/// <summary>
/// The <c>SysMailerEML</c> class is an interactive email provider implementation that sends messages by generating
/// an EML file, uploading it to Azure temporary blob storage, and then redirecting the user's browser to
/// the file to save or open for sending using their default email client.
/// </summary>
// This is a framework class. Customizing this class may cause problems with future upgrades to the software.
[System.ComponentModel.Composition.ExportAttribute(identifierStr(Dynamics.AX.Application.SysIMailer)),
System.ComponentModel.Composition.ExportMetadataAttribute(extendedTypeStr(SysMailerId), #SysMailerEML_ID)]
public class SysMailerEML implements SysIMailerInteractive
{
```

### Implement the SysIMailer interface

The **SysIMailer** interface includes identifiable information about an email provider, regardless of the capabilities of the email provider itself. To implement this interface, you must create two methods:

- **getId** – This method returns the same ID that is specified in the **ExportMetadataAttribute** attribute.
- **getDescription** – This method returns a non-technical description that indicates how the email will be sent.

```xpp
public SysMailerId getId()
{
    return #SysMailerEML_ID;
}
public SysMailerDescription getDescription()
{
    // Use an email app, such as Outlook
    return "@ApplicationFoundation:EmailProviderEMLDescription";
}
```

### Implement a combination of the SysIMailerInteractive and SysIMailerNonInteractive interfaces

The **SysIMailerInteractive** and **SysIMailerNonInteractive** interfaces are very simple. They implement the **sendInteractive** and **sendNonInteractive** methods, respectively. An email provider might implement one or both methods, depending on its capabilities. Each method that is implemented takes a .NET **System.Net.Mail.MailMessage** object that you use to construct and send the email.

```xpp
public boolean sendInteractive(System.Net.Mail.MailMessage _message)
{
    using (var emlStream = this.generateEmlFile(_message))
    {
        Dynamics.AX.Application.File::SendFileToUser(emlStream, 'message.eml');
    }
    return true;
}
```

The **System.Net.Mail.MailMessage** object contains a large amount of advanced functionality that is related to MIME messages. You can build a relatively complex message object and pass it to an email provider. If there is specific functionality that an email provider doesn't support, the email provider is expected to handle the functionality actively (by modifying the message), passively (by making an internal call to another email provider), or not at all (by throwing an error).

## Migration from Microsoft Dynamics AX 2012 to finance and operations applications

Migration involves using the **SysMailerMessageBuilder** object to build a message and then using the **SysMailerFactory** to send it, as outlined in the examples in this article.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
