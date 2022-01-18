---
# required metadata

title: Confier an e-mail channel
description: This topic provides description of the process of configuring e-mail channel for receiving electronic invoices
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]

Configure an email account channel if the Electronic invoicing feature you created imports electronic vendor invoices from attached files that are received by email.

 1. In RCS, select the Electronic invoicing feature that you created. Make sure you selected the Version with status Draft.
 2. On **Setups** tab, in the grid, select **Add**.
 3. Select **Custom setup**, and then define **Setup type** set to **Data channel**.
 4. In the **Select data channel** field enter **Incoming e-mail**.
 5. Select **Create**.
 6. Locate just created line and select **Edit**.
 7. On the **Data channel** tab, in the **Parameters** field group, configure required parameters:
    |**Name** |**Description** |**Details** |
    |----------------|----------------------------------|-----------------------------------------------------|
    |Data channel|Data channel identifier|Enter unique name of Data channel up to 10 symbols. It will be referenced to in Applicability rules, and in connected applications during communication process.|
    |Server address|E-mail server address|Enter the email account provider. For example, the server address for https://outlook.live.com/ is _imap-mail.outlook.com_|
    |Server port|E-mail server port number|Enter the port used by the email account provider. For example, the server port for https://outlook.live.com/ is _993_|
    |User name secret|Azure Key Vault secret name to store user name|Enter the name of the Key vault secret that contains the ID of the email user account. This secret must be created in Azure key vault and setup in your service environment.|
    |User password secret|Azure Key Vault secret name to store user password|Enter the name of the Key vault secret that contains the password of the email user account.|
    |Timeout|It limits the max time to wait for a response in milliseconds|Default is 10 sec|
    |Main folder|E-mail import source|This is the folder from which service will process e-mails|
    |Archive folder|E-mail archive folder|Processed e-mails will be stored in this folder. If you don't specify this folder, system will create it automatically.|
    |Error folder|E-mail error folder|If the processing resulted with failure, system will move the e-mail to this folder. If you don't specify this folder, system will create it automatically.|
    |Max message size|Max size of a single message to process in bytes|Default value is 20000000. You can limit the size.|
    |Max message number|Max amount of messages to process for a single action|Set 0 if you don't limit this number.|
    |From filter|String to filter by sender address. Use semicolon (;) to separate addresses|Optional. Define sender addresses to process e-mails|
    |Subject filter|String to filter by subject. Simple mask of type `*smth*.ext` is supported where `"*"` means 0 or more of any symbol|Optional. Process only e-mail that match Subject filter|
    |Date filter|Max date to determine the age of message to process in days|Optional. Process e-mail based on the dates. Default is 30 days.|
    |Processing mode|All attachments within an email could be processed together or each attachment could be processed separately| By Attachment: This option will result in creation of new electronic document for each attachment in the mail. I.e. if one mail contains several files with e-invoice data, each one will be considered as a new e-invoice in the system. <p> By email: This option will take one attachment as a base one and create one electronic invoice in the system. Other attachments can be used as supporting files.|

 6. In the **Attachments filter** field group, add the file filtering information. Only attachments that satisfy the defined filter are processed. For example, you can setup `*.xml` for attachments with an xml extension. The name of the attachment is used in Dynamics 365 Finance and Supply Chain management applications during setup.
 
    If the **Processing mode** is ***By email***, you can add multiple filters here, and the name will identify particular document.
	
    If the **Processing mode** is ***By attachment***, you can define only on filter.
	
 8. On the **Applicability rules** tab, review and update the criteria as necessary. The **Channel** field must be equal to the **Data** channel provided above.
 9. Select **Save** and close the page.
