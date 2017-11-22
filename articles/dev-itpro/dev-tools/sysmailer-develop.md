---
# required metadata

title: Develop email experiences
description:
author: ChrisGarty
manager: AnnBe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 270774
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-11-21
ms.dyn365.ops.version: Platform update 4

---

# Develop email experiences

## Sending emails

An application developer consumes the SysMailer framework primarily by using the **SysMailerFactory** and **SysMailerMessageBuilder** classes. The email provider factory is used to retrieve interactive or non-interactive email providers to send multiple messages at a time, or to directly send a message. The email providers expect the messages they send to be encapsulated within .NET **System.Net.Mail.MailMessage** objects. The message builder class is used to build the .NET object to pass to the email provider.

### Scenarios

Three scenarios are described:
- Sending an interative message.
- Sending a non-interactive (batch) message.
- Sending multiple non-interactive (batch) messages

#### Sending an interactive message

The following example is taken from the **CustCollectionsEmail** class. It demonstrates multiple features of the framework, including chaining message builder calls, conditionally setting the sender (from) address, and adding attachments.

```
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
        if (strLen(collectionsEmail) &gt; 0)
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

The following example is taken from the **VendRequestCompanyWorkflowManager** class. It demonstrates how to send a single message in non-interactively.

```
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

The following example is taken from the **UserAdAddManager** class. It demonstrates how to get an instance of a batch email provider before iterating over a list of emails to send.

```
var mail = SysMailerFactory::getNonInteractiveMailer();
var messageBuilder = new SysMailerMessageBuilder();
for (i = 1; i &lt;= conLen(\_notifyCon); i++)
{
    notifyEmailsStr = conPeek(\_notifyCon, i);
    select firstonly RecId, Email from sysUser where sysUser.Id == notifyEmailsStr;
    if (sysUser.RecId && sysUser.Email != '')
    {
        messageBuilder.reset()
            .setFrom(\_emailFrom)
            .addTo(sysUser.Email)
            .setSubject("@SYS129183")
            .setBody(errorStr);
        mail.sendNonInteractive(messageBuilder.getMessage());
        delete_from tmpUserErrorNotification;
    }
}
```

### Important considerations

- A sender address (from) is required when sending a message to an email provider. A receiver address (to) is required when sending messages non-interactively. If these conditions are not met the framework throws an exception. If **getMessage** is called on the message builder before any call to **setFrom** is made, the builder will attempt to default the sender address to the current user’s email address or network alias.
- When sending a message, the way the sender address (from) is used depends on the provider:
    - EML provider: The sender address is removed from the message before opening it in the user’s email client. This allows the email client to default the sender address to its default account configured for sending mail.
    - SMTP provider: The SMTP server must be configured to allow sending using that (from) address i.e. the SMTP server permits the impersonation of emails sent from it. If not then the SMTP server may deny the sending of the message, flag it as spam, etc.
- When sending messages, the framework will return a Boolean value indicating the success of the operation to send the message, but will not report any messages to the Infolog upon success. It is left up to you to decide if you wish want to display any messages in the Infolog.
- All messages by default are sent with rich-text (HTML) bodies. If an application scenario requires the use of plain text to maintain newline spacing, this can be achieved by passing false to the optional **\_isHtml** parameter of the **setBody** method on the message builder.

## Adding a new email provider

You can add email providers using the pluggable framework. By using the factory class and interfaces, new email providers become instantly available for use across all relevant application scenarios. Examples of email providers can be found in the existing provider implementations, SysMailerEML and SysMailerSMTP, as well as an existing tutorial implementation, Tutorial\_SysMailerMailTo. The examples below are excerpts from the SysMailerEML email provider implementation.

In order to implement an email provider, you must create the implementation class with the following properties:

- The class must be attributed with the appropriate **Export** attributes.
- The class must implement the base **SysIMailer** methods, **getId** and **getDescription**.
- The class must implement either the **SysImailerInteractive** or **SysIMailerNonInteractive** interfaces, or both.

### Step 1: Attribute the implementation class


The first step is to attribute the implementation class. Two attributes must be specified:

-   ExportAttribute – This attribute is used by the SysPlugin framework to discover the plugin. It specifies that the plugin is an implementation of SysIMailer and therefore part of the SysMailer framework.

-   ExportMetadataAttribute – This attribute is used by the SysPlugin framework to find specific instances of a plugin with specific metadata. It specifies the ID of the email provider so that a single provider may be discovered quickly. **No two email providers should ever share the same ID.**

using System.IO;

using System.Net.Mail;

using System.Text.RegularExpressions;

\#define.SysMailerEML\_ID('EML')

*/// &lt;summary&gt;*

*/// The &lt;c&gt;SysMailerEML&lt;/c&gt; class is an interactive email provider implementation that sends messages by generating*

*/// an EML file, uploading it to Azure temporary blob storage, and then redirecting the user's browser to*

*/// the file to save or open for sending using their default email client.*

*/// &lt;/summary&gt;*

*// This is a framework class. Customizing this class may cause problems with future upgrades to the software.*

\[System.ComponentModel.Composition.ExportAttribute(identifierStr(Dynamics.AX.Application.SysIMailer)),

System.ComponentModel.Composition.ExportMetadataAttribute(extendedTypeStr(SysMailerId), \#SysMailerEML\_ID)\]

public class SysMailerEML implements SysIMailerInteractive

{

### Step 2: Implement the SysIMailer interface


The SysIMailer interface includes identifiable information about an email provider regardless of the capabilities of the email provider itself. Implementing it involves creating two methods:

-   getId() – This should return the same ID as specified in the ExportMetadataAttribute.

-   getDescription() – This should return a non-technical description of how the email will be sent.

public SysMailerId getId()

{

return \#SysMailerEML\_ID;

}

public SysMailerDescription getDescription()

{

*// Use an email app, such as Outlook*

return "@ApplicationFoundation:EmailProviderEMLDescription";

}

### Step 3: Implement a combination of the SysIMailerInteractive and SysIMailerNonInteractive interfaces


The SysIMailerInteractive and SysIMailerNonInteractive interfaces are extremely simple. They implement either a sendInteractive() or sendNonInteractive() method respectively. An email provider may implement one or both based on its capabilities. Each of the implemented methods take a .NET System.Net.Mail.MailMessage object which should be used to construct and send the email.

public boolean sendInteractive(System.Net.Mail.MailMessage \_message)

{

using (var emlStream = this.generateEmlFile(\_message))

{

Dynamics.AX.Application.File::SendFileToUser(emlStream, 'message.eml');

}

return true;

}

Note that the System.Net.Mail.MailMessage object is fully featured and contains a large amount of advanced functionality related to MIME messages. It is possible for an application team to build a relatively complex message object and pass it to an email provider. If there are certain functionalities that an email provider does not support, it is expected that the email provider will handle it either actively by modifying the message, passively by calling to another email provider internally, or not at all by throwing an error.

## Migration from AX2012 to AX7

Migration from AX2012 to AX7 involves using the SysMailerMessageBuilder object to build a message and then use the SysMailerFactory to send it, as outlined in the examples in this document. Where extensions were made to the old mail system functionality, those extensions should be evaluated to determine whether that functionality needs to be built into the new framework as well.
