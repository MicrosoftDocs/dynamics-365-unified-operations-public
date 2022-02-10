---
# required metadata

title: Configure an e-mail channel
description: This topic provides information about how to configure an e-mail channel to receive electronic invoices.
author: dkalyuzh
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Configure an email channel

[!include [banner](../includes/banner.md)]

If the Electronic invoicing feature you created imports electronic vendor invoices from attached files that are received by email, you should configure an email account channel.

1. In RCS, select the Electronic invoicing feature that you created. Make sure you selected the version with a status of **Draft**.
2. On teh **Setups** tab, in the grid, select **Add**.
3. Select **Custom setup**, and then in the **Setup type** field, select **Data channel**.
4. In the **Select data channel** field, enter **Incoming e-mail**.
5. Select **Create**.
6. Select the line you created, and then select **Edit**.
7. On the **Data channel** tab, in the **Parameters** field group, configure the required parameters.
    |**Name** |**Description** |**Details** |
    |----------------|----------------------------------|-----------------------------------------------------|
    |Data channel|Data channel identifier|Enter unique name of data channel up to 10 symbols. The channel will be referenced to in Applicability rules and in connected applications during communication process.|
    |Server address|E-mail server address|Enter the email account provider. For example, the server address for https://outlook.live.com/ is _imap-mail.outlook.com_|
    |Server port|E-mail server port number|Enter the port used by the email account provider. For example, the server port for https://outlook.live.com/ is _993_|
    |User name secret|Azure Key Vault secret name to store user name.|Enter the name of the Key vault secret that contains the ID of the email user account. This secret must be created in Azure key vault and set up in your service environment.|
    |User password secret|Azure Key Vault secret name to store user password.|Enter the name of the Key vault secret that contains the password of the email user account.|
    |Timeout|The maximum time limit to wait for a response is counted in milliseconds.|The default is 10 seconds.|
    |Main folder|E-mail import source|This is the folder from which the service will process e-mails.|
    |Archive folder|E-mail archive folder|Processed e-mails are stored in this folder. If you don't specify this folder, the system will automatically create it.|
    |Error folder|E-mail error folder|If the processing fails, the system moves the e-mail to this folder. If you don't specify this folder, the system will create it automatically.|
    |Max message size|Maximum size of a single message to process in bytes.|The default value is 20,000,000. You can limit the size.|
    |Max message number|Maximum amount of messages to process for a single action.|Set zero (0) if you don't limit this number.|
    |From filter|String to filter by sender address. Use semicolon (;) to separate addresses.|Optional. Define sender addresses to process e-mails.|
    |Subject filter|String to filter by subject. Simple mask of type `*smth*.ext` is supported where `"*"` means 0 or more of any symbol|Optional. Process only e-mails that match the **Subject** filter.|
    |Date filter|Maximum date to determine the age of a message to process in days.|Optional. Process e-mail based on the dates. The default is 30 days.|
    |Processing mode|All attachments in an email can be processed together or separately.| Processed by attachment: This option results in a new electronic document for each attachment in the mail. For example, if one email contains several files with e-invoice data, each file is considered a new e-invoice in the system. <br> Processed by email: This option takes one attachment as a base and creates one electronic invoice in the system. Other attachments can be used as supporting files.|

8. In the **Attachments filter** field group, add the file filtering information. Only attachments that satisfy the defined filter are processed. For example, you can set up `*.xml` for attachments with an xml extension. The name of the attachment is used in Dynamics 365 Finance or Dynamics Supply Chain management during setup.
 
    If the **Processing mode** is ***By email***, you can add multiple filters here, and the name will identify particular document.
	
    If the **Processing mode** is ***By attachment***, you can define only on filter.
	
9. On the **Applicability rules** tab, review and update the criteria as necessary. The **Channel** field must be equal to the **Data** channel provided above.
10. Select **Save** and close the page.
