---
title: Configure email channels
description: Learn how to configure an email channel to receive electronic invoices.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Configure email channels

[!include [banner](../../includes/banner.md)]

If the Electronic invoicing feature that you created imports electronic vendor invoices from attached files that you receive by email, configure an email account channel.

1. Select the Electronic invoicing feature that you created. Select the version that has a status of **Draft**.
1. On the **Setups** tab, select **Add**.
1. In the **Create feature setup** drop-down dialog box, in the **New** field group, select the **Custom setup** option.
1. In the **Setup type** field group, select the **Data channel** option.
1. In the **Select data channel** field, enter **Incoming e-mail**.
1. Select **Create**.
1. Select the line that you created, and then select **Edit**.
1. On the **Data channel** tab, in the **Parameters** section, set the following required fields.

    | Field                | Description |
    |----------------------|-------------|
    | Data channel         | Enter a unique name to identify the data channel. The name can have a maximum of 10 characters. The system references it in applicability rules and in connected applications during the communication process. |
    | Server address       | Enter the server address of the email account provider for Internet Message Access Protocol (IMAP). For example, the server address for the `https://outlook.live.com` provider is imap-mail.outlook.com. |
    | Server port          | Enter the number of the port that the email account provider uses. For example, the server port for the `https://outlook.live.com` provider is 993. |
    | User name secret     | Enter the name of the Microsoft Azure Key Vault secret that contains the ID of the email user account. Create this secret in Key Vault and set it up in your service environment. |
    | User password secret | Enter the name of the Key Vault secret that contains the password of the email user account. |
    | Timeout              | Enter the maximum time limit, in milliseconds (ms), that the system should wait for a response. The default value is 10,000 ms (10 seconds). |
    | Main folder          | Specify the email import source, or the folder that the service should process emails from. |
    | Archive folder       | Specify the folder where processed emails should be stored. If you don't specify this folder, the system automatically creates it. |
    | Error folder         | Specify the folder that the system should move emails to if the processing fails. If you don't specify this folder, the system automatically creates it. |
    | Max message size     | Enter the maximum size, in bytes, of a single message that is processed. The default value is 20,000,000 bytes. |
    | Max message number   | Enter the maximum number of messages to process for a single action. If you don't want to limit the number of messages, set the value to **0** (zero). |
    | From filter          | Enter a string to filter by sender address. Only emails where the sender address matches the filter are processed. This field is optional. To specify multiple sender addresses, use semicolons (;) as separators. |
    | Subject filter       | Enter a string to filter by subject. Only emails where the subject matches the filter are processed. This field is optional. A simple mask such as **\*smth\*.ext** is supported, where each asterisk (\*) represents zero or more occurrences of any character. |
    | Date filter          | Specify a date to define the maximum age, in days, of messages that are processed. This field is optional. The default value is 30 days. |
    | Processing mode      | <p>Select one of the following options to specify whether the system can process all the attachments in an email together or whether it should process each attachment separately:</p><ul><li><b>By attachment</b> – The system creates a new electronic document for each attachment in the email. For example, if one email includes several files that contain e-invoice data, each file is considered a new e-invoice in the system.</li><li><b>By email</b> – One attachment is considered a base attachment, and one electronic invoice is created in the system. Other attachments can be used as supporting files.</li></ul> |

1. In the **Attachments filter** section, add the file filtering information. The system processes only attachments that satisfy the defined filter. For example, **\*.xml** filters for attachments that have the .xml file name extension. Use the name of the attachment in Dynamics 365 Finance or Dynamics 365 Supply Chain Management during setup.

    - If you set the **Processing mode** field to **By email** in the previous step, you can add multiple filters. The name identifies the specific document.
    - If you set the **Processing mode** field to **By attachment**, you can add only one filter.

1. On the **Applicability rules** tab, review and update the criteria as required. The value of the **Channel** field must equal the value that you entered in the **Data channel** field in step 8.
1. Select **Save**, and close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]