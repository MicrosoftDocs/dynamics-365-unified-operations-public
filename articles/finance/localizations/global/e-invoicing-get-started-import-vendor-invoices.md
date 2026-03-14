---
title: Use the electronic invoicing service to import vendor invoices
description: Learn about how to import vendor invoices using the Electronic Invoicing service, including an outline on setting up vendor invoice import in the Globalization studio workspace.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2020-07-08
---

# Use the electronic invoicing service to import vendor invoices

[!include [banner](../../includes/banner.md)]

This article provides information to help you get started with importing vendor invoices by using the Electronic Invoicing service. It guides you through the configuration steps that you must complete in the **Globalization studio** workspace in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management to receive electronic vendor invoices from vendors.

## Set up vendor invoice import in the Electronic Invoicing service

To set up vendor invoice import in the **Globalization studio** workspace, follow these steps:

1. Consult the list of generally available Electronic invoicing features.
1. Select and import the Electronic invoicing feature. For more information, see [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create an Electronic invoicing feature for your organization. For more information, see [Create Globalization features](../global/gs-e-invoicing-create-new-globalization-feature.md).

## Configure an email account channel

Configure an email account channel if the Electronic invoicing feature you created imports electronic vendor invoices from attached files that you receive by email.

1. In the **Globalization studio** workspace, select the Electronic invoicing feature that you created. Make sure that you select the version with a status of **Draft**.
1. On the **Setups** tab, in the grid, select a feature setup, and then select **Edit**.
1. On the **Data channel** tab in the **Parameters** field group, enter the name of the channel in the **Data channel** field. The channel name can't be more than ten characters.
1. In the **Server address** field, enter the email account provider. For example, the server address for **<https://outlook.live.com/>** is **imap-mail.outlook.com**.
1. In the **Server port** field, enter the port used by the email account provider. For example, the server port for **<https://outlook.live.com/>** is **993**.
1. In the **User name secret** field, enter the name of the Key vault secret that contains the ID of the email user account. Create this secret in Azure Key Vault and set it up in your service environment.
1. In the **User password secret** field, enter the name of the Key vault secret that contains the password of the email user account.
1. (Optional) Enter values in the **From filter**, **Subject filter**, and **Date filter** fields.
1. Enter the names of the mailbox folders where mails are:

    - Imported from: **Main folder**
    - Saved after successful processing: **Archive folder**
    - Saved after not successful processing: **Error folder**

    You don't need to create these folders in the mailbox. The folders are created automatically after the first e-invoice import and processing.

1. In the **Attachments filter** field group, add the file filtering information. Only attachments that satisfy the defined filter are processed. For example, you can set up "\*.xml" for attachments with an XML extension. Use the name of the attachment in Dynamics 365 Finance or Dynamics 365 Supply Chain Management during setup.
1. On the **Applicability rules** tab, review and update the criteria as necessary. The value of the **Channel** field must equal the **Data channel** value that you provided earlier. For more information, see [Applicability rules](../global/gs-e-invoicing-feature-setup.md#applicability-rules).
1. Select **Save** and close the page.

### Configure a Microsoft SharePoint channel

Configure a Microsoft SharePoint channel if the Electronic invoicing feature imports electronic vendor invoices from files placed in SharePoint folders.

1. In the **Globalization studio** workspace, select the Electronic invoicing feature that you created. Make sure that you select the version that has a status **Draft**.
1. On the **Setups** tab, in the grid, select a Feature setup and then select **Edit**.
1. On the **Data channel** tab, in the **Parameters** field group, select **SharePoint address** and enter the SharePoint URL.
1. Select **Server port** and enter the port used by the email account provider.
1. Select **Application Id** and enter the name of the Key vault secret that contains the ID of the SharePoint client.
1. Select **Application secret** and enter the name of the Key vault secret that contains the password of the SharePoint client.
1. Select **File filter** and review and update the mask to filter the files that contain the electronic vendor invoice to import.
1. On the **Applicability rules** tab, review and update the criteria as necessary. For more information, see [Applicability rules](../global/gs-e-invoicing-feature-setup.md#applicability-rules).
1. Select **Save** and close the page.

### Deploy an Electronic invoicing feature

To deploy the Electronic invoicing feature, see [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Set up vendor invoice import in Finance or Supply Chain Management

Complete the steps in the following section to set up a PEPPOL-type vendor invoice import as an example.

### Import PEPPOL electronic vendor invoices

1. Go to the **Electronic reporting** workspace and select **Reporting configurations**.
1. Select **Customer invoice context model**, and then select **Create configuration** > **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.
1. On the **Draft** version, select **Designer** and in the **Data model** tree, select **Map model to datasource**.
1. In the **Definitions** tree, select **DataChannel** and then select **Designer**.
1. In the **Data sources** tree, expand the **$Context\_Channel** container.
1. In the **Value** field, select **Edit** > **Edit formula**, and enter the name of the channel as it's given in the configuration of the data channel for the Electronic invoicing feature in Globalization studio.
1. Select **Save** and close the page.
1. Close the page.
1. Select the derived configuration you just created from the **Customer invoice context model**, and on the **Versions** FastTab, select **Change Status** > **Completed**.
1. Go to **Organization administration** > **Setup** > **Electronic document parameters** and on the **Features** tab, make sure that **PEPPOL Global electronic invoices** is selected.
1. On the **External channels** tab, in the **Channels** field group, select **Add**.
1. In the **Channel** field, enter the data channel name and in the **Description** field, enter a description.
1. In the **Company** field, select the legal entity.
1. In the **Document context** field, select the new derived configuration from **Customer invoice context model**. The mapping description should be **Data channel context**.
1. In the **Import sources** field group, select **Add**.
1. In the **Name** field enter **Attachments filter name** and in the **Data entity name** field, select **Vendor invoice header**.
1. In the **Model mapping** field, select **Vendor invoice imprt - Import vendor invoice**.
1. Select **Save** and then close the page.

## Receive electronic invoices

The Electronic Invoicing service performs two steps during invoice import from the data channels:

1. Accesses the mailbox and reads the emails.
1. Processes the emails.

To perform these two steps, the client must call the service manually for each step. However, set up a batch for receiving electronic documents.

To receive electronic invoices, follow these steps:

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Receive electronic documents**.
1. Select **OK** and then close the page.

## View receive logs for electronic invoices

To view the receive logs for electronic invoices, go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log**.
If you don't see successfully processed invoices, remove the table filter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
