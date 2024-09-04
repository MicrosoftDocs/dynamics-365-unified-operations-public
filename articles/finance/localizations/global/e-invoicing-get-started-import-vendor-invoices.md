---
title: Use the electronic invoicing service to import vendor invoices
description: Learn about how to import vendor invoices using the Electronic Invoicing service, including an outline on setting up vendor invoice import in the Globalization studio workspace.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/04/2024
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
---

# Use the electronic invoicing service to import vendor invoices

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with importing vendor invoices by using the Electronic Invoicing service. It guides you through the configuration steps that you must complete in the **Globalization studio** workspace in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management to receive electronic vendor invoices from vendors.

## Set up vendor invoice import in the Electronic Invoicing service

To set up vendor invoice import in the **Globalization studio** workspace, follow these steps.

1. Consult the list of generally available Electronic invoicing features.
2. Select and import the Electronic invoicing feature. For more information, see [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
3. Create an Electronic invoicing feature for your organization. For more information, see [Create Globalization features](../global/gs-e-invoicing-create-new-globalization-feature.md).

## Configure an email account channel

Configure an email account channel if the Electronic invoicing feature you created imports electronic vendor invoices from attached files that are received by email.

1. In the **Globalization studio** workspace, select the Electronic invoicing feature that you created. Make sure that you select the version that has a status of **Draft**.
2. On **Setups** tab, in the grid, select a feature setup, and then select **Edit**.
3. On the **Data channel** tab in the **Parameters** field group, in the **Data channel** field, enter the name of the channel. The channel name should be no more than ten characters.
4. In the **Server address** field, enter the email account provider. For example, the server address for **https://outlook.live.com/** is **imap-mail.outlook.com**.
5. In the **Server port** field, enter the port used by the email account provider. For example, the server port for **https://outlook.live.com/** is **993**.
6. In the **User name secret** field, enter the name of the Key vault secret that contains the ID of the email user account. This secret must be created in Azure key vault and set up in your service environment. 
7. In the **User password secret** field, enter the name of the Key vault secret that contains the password of the email user account.
8. Optional: Enter values in the **From filter**, **Subject filter**, and **Date filter** fields.
9. Enter the names of the mailbox folders where mails will be:

    - Imported from: **Main folder**
    - Saved after successful processing: **Archive folder**
    - Saved after not successful processing: **Error folder** 

    You aren't required to create these folders in the mailbox. The folders are created automatically after the first e-invoice import and processing. 

10. In the **Attachments filter** field group, add the file filtering information. Only attachments that satisfy the defined filter are processed. For example, you can set up "\*.xml" for attachments with an xml extension. The name of the attachment is used in Dynamics 365 Finance or Dynamics 365 Supply Chain Management during setup. 
11. On the **Applicability rules** tab, review and update the criteria as necessary. The value of the **Channel** field must equal the **Data channel** value that you provided earlier. For more information, see [Applicability rules](../global/gs-e-invoicing-feature-setup.md#applicability-rules).
12. Select **Save** and close the page.

### Configure a Microsoft SharePoint channel

Configure a Microsoft SharePoint channel if the Electronic invoicing feature imports electronic vendor invoices from files placed in SharePoint folders.

1. In the **Globalization studio** workspace, select the Electronic invoicing feature that you created. Make sure that you select the version that has a status **Draft**.
2. On **Setups** tab, in the grid, select a Feature setup and then select **Edit**.
3. On the **Data channel** tab, in the **Parameters** field group, select **SharePoint address** and enter the SharePoint URL.
4. Select **Server port** and enter the port used by the email account provider.
5. Select **Application Id** and enter the name of the Key vault secret that contains the ID of the SharePoint client.
6. Select **Application secret** and enter the name of the Key vault secret that contains the password of the SharePoint client.
7. Select **File filter**. Review and update the mask to filter the files that contain the electronic vendor invoice to import.
8. On the **Applicability rules** tab, review and update the criteria as necessary. For more information, see [Applicability rules](../global/gs-e-invoicing-feature-setup.md#applicability-rules).
9. Select **Save** and close the page.

### Deploy an Electronic invoicing feature

To deploy the Electronic invoicing feature, see [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Set up vendor invoice import in Finance or Supply Chain Management
Complete the steps in the following two sections to set up different types of vendor invoice import.

### Import PEPPOL electronic vendor invoices

1. Go to the **Electronic reporting** workspace and select **Reporting configurations**.
2. Select **Customer invoice context model**, and then select **Create configuration** > **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.
3. On the **Draft** version, select **Designer** and in the **Data model** tree, select **Map model to datasource**.
4. In the **Definitions** tree, select **DataChannel** and then select **Designer**.
5. In the **Data sources** tree, expand the **$Context\_Channel** container. 
6. In the **Value** field, select **Edit** \> **Edit formula**, and enter the name of the channel as it's given in the configuration of the data channel for the Electronic invoicing feature in Globalization studio. 
7. Select **Save** and close the page.
8. Close the page.
9. Select the derived configuration you just created from the **Customer invoice context model**, and on the **Versions** FastTab, select **Change Status** > **Completed**.
10. Go to **Organization administration** > **Setup** > **Electronic document parameters** and on the **Features** tab, make sure that **PEPPOL Global electronic invoices** is selected. 
11. On the **External channels** tab, in the **Channels** field group, select **Add**.
12. In the **Channel** field, enter the data channel name and in the **Description** field, enter a description.
13. In the **Company** field, select the legal entity. 
14. In the **Document context** field, select the new derived configuration from **Customer invoice context model**. The mapping description should be **Data channel context**.
15. In the **Import sources** field group, select **Add**.
16. In the **Name** field enter **Attachments filter name** and in the **Data entity name** field, select **Vendor invoice header**.
17. In the **Model mapping** field, select **Vendor invoice imprt - Import vendor invoice**.
18. Select **Save** and then close the page.


## Receive electronic invoices

The Electronic Invoicing service performs two steps during invoice import from the data channels:

1. Accesses the mailbox and reading e-mail.
2. Processes the emails. 

To perform these two steps, the client should call the service manually for each step. However, we recommend that you set up a batch for receiving electronic documents.

To receive electronic invoices, follow these steps:

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Receive electronic documents**.
2. Select **OK** and then close the page.


## View receive logs for electronic invoices

To view the receive logs for electronic invoices, go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log**.
If you don't see successfully processed invoices, remove the table filter.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
