---
title: Configure an email channel
description: This article explains how to configure an email channel to receive electronic invoices.
author: gionoder
ms.date: 12/09/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Configure an email channel

[!include [banner](../includes/banner.md)]

If the Electronic invoicing feature that you created imports electronic vendor invoices from attached files that are received by email, configure an email account channel.

1. In Regulatory Configuration Service (RCS), select the Electronic invoicing feature that you created. Select the version that has a status of **Draft**.
2. On the **Setups** tab, select **Add**.
3. In the **Create feature setup** drop-down dialog box, in the **New** field group, select the **Custom setup** option.
4. In the **Setup type** field group, select the **Data channel** option.
5. In the **Select data channel** field, enter **Incoming e-mail**.
6. Select **Create**.
7. Select the line that you created, and then select **Edit**.
8. On the **Data channel** tab, in the **Parameters** section, set the following required fields.

    | Field                | Description |
    |----------------------|-------------|
    | Data channel         | Enter a unique name to identify the data channel. The name can have a maximum of 10 characters. It will be referenced in applicability rules and in connected applications during the communication process. |
    | Server address       | Enter the server address of the email account provider for Internet Message Access Protocol (IMAP). For example, the server address for the `https://outlook.live.com` provider is imap-mail.outlook.com. |
    | Server port          | Enter the number of the port that the email account provider uses. For example, the server port for the `https://outlook.live.com` provider is 993. |
    | User name secret     | Enter the name of the Microsoft Azure Key Vault secret that contains the ID of the email user account. This secret must be created in Key Vault and set up in your service environment. |
    | User password secret | Enter the name of the Key Vault secret that contains the password of the email user account. |
    | Timeout              | The maximum time limit, in milliseconds (ms), that the system should wait for a response. The default value is 10,000 ms (10 seconds). |
    | Main folder          | Specify the email import source, or the folder that the service should process emails from. |
    | Archive folder       | Specify the folder where processed emails should be stored. If you don't specify this folder, the system will automatically create it. |
    | Error folder         | Specify the folder that the system should move emails to if the processing fails. If you don't specify this folder, the system will automatically create it. |
    | Max message size     | Enter the maximum size, in bytes, of a single message that is processed. The default value is 20,000,000 bytes. |
    | Max message number   | Enter the maximum number of messages to process for a single action. If you don't want to limit the number of messages, set the value to **0** (zero). |
    | From filter          | Enter a string to filter by sender address. Only emails where the sender address matches the filter will be processed. This field is optional. To specify multiple sender addresses, use semicolons (;) as separators. |
    | Subject filter       | Enter a string to filter by subject. Only emails where the subject matches the filter will be processed. This field is optional. A simple mask such as **\*smth\*.ext** is supported, where each asterisk (\*) represents zero or more occurrences of any character. |
    | Date filter          | Specify a date to define the maximum age, in days, of messages that are processed. This field is optional. The default value is 30 days. |
    | Processing mode      | <p>Select one of the following options to specify whether all the attachments in an email can be processed together or whether each attachment should be processed separately:</p><ul><li><b>By attachment</b> – A new electronic document will be created for each attachment in the email. For example, if one email includes several files that contain e-invoice data, each file will be considered a new e-invoice in the system.</li><li><b>By email</b> – One attachment will be considered a base attachment, and one electronic invoice will be created in the system. Other attachments can be used as supporting files.</li></ul> |

9. In the **Attachments filter** section, add the file filtering information. Only attachments that satisfy the defined filter will be processed. For example, **\*.xml** will filter for attachments that have the .xml file name extension. The name of the attachment is used in Dynamics 365 Finance or Dynamics 365 Supply Chain Management during setup.

    - If you set the **Processing mode** field to **By email** in the previous step, you can add multiple filters here. The name will identify the specific document.
    - If you set the **Processing mode** field to **By attachment**, you can add only one filter.

10. On the **Applicability rules** tab, review and update the criteria as required. The value of the **Channel** field must equal the value that you entered in the **Data channel** field in step 8.
11. Select **Save**, and close the page.
