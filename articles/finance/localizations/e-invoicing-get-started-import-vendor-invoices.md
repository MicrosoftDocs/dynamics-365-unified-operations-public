---
# required metadata

title: Use the electronic invoicing service to import vendor invoices
description: This topic provides information about how to import vendor invoices using the Electronic Invoicing service.
author: gionoder
ms.date: 08/03/2021
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
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Use the electronic invoicing service to import vendor invoices

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides you information that will help you get started with the importation of vendor invoices using the Electronic Invoicing service. It guides you through the configuration steps in Regulatory Configuration Services (RCS) and Dynamics 365 Finance and Supply Chain Management that you must follow to receive electronic vendor invoices from the vendors.

## Set up vendor invoice import in RCS

1. Consult the list of [generally available Electronic invoicing features](dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#generally-available-features).
2. Select and import the Electronic invoicing feature. For more information, see [Import an Electronic invoicing feature from Microsoft configuration provider](e-invoicing-get-started.md#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider)
3. Create an Electronic invoicing feature for your organization. For more information, see [Create an Electronic invoicing feature under your organization provider](e-invoicing-get-started.md#create-an-electronic-invoicing-feature-under-your-organization-provider)

## Configure an e-mail account channel

Configure an e-mail account channel if the Electronic invoicing feature you created imports electronic vendor invoices from attached files that are received by e-mail.

1. In RCS, select the Electronic invoicing feature that you created. Make sure you select the version with a status of **Draft**.
2. On **Setups** tab, in the grid, select a feature setup, and then select **Edit**.
3. On the **Data channel** tab in the **Parameters** field group, select **Server address** and enter the e-mail account provider.
4. Select **Server port** and enter the port used by the e-mail account provider.
5. Select **User name secret** and enter the name of the Key vault secret that contains the ID of the e-mail user account.
6. Select **User password secret** and enter the name of the Key vault secret that contains the password of the e-mail user account.
7. Select **Subject filter**. Review and update the string that contains the default e-mail subject to identify the e-mail that contains the electronic vendor invoice to import.
8. On the **Applicability rules** tab, review and update the criteria if necessary. For more information, see [Applicability rules](e-invoicing-configuration-rcs.md#applicability-rules).
9. Select **Save** and close the page.

### Configure a Microsoft SharePoint channel

Configure a Microsoft SharePoint channel if the Electronic invoicing feature imports electronic vendor invoices from files placed in SharePoint folders:

1. In RCS, select the Electronic invoicing feature that you created. Make sure you selected the **Version** with status **Draft**.
2. On **Setups** tab, in the grid, select a Feature setup and then select **Edit**.
3. On the **Data channel** tab, in the **Parameters** field group, select **SharePoint address** and enter the SharePoint URL.
4. Select **Server port** and enter the port used by the e-mail account provider.
5. Select **Application Id** and enter the name of the Key vault secret that contains the ID of the SharePoint client.
6. Select **Application secret** and enter the name of the Key vault secret that contains the password of the SharePoint client.
7. Select **File filter**. Review and update the mask to filter the files that contain the electronic vendor invoice to import.
8. On the **Applicability rules** tab, review and update the criteria if necessary. For more information, see [Applicability rules](e-invoicing-configuration-rcs.md#applicability-rules).
9. Select **Save** and close the page

### Deploy an Electronic invoicing feature

To deploy the Electronic invoicing feature, see [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment).

## Set up vendor invoice import in Finance and Supply Chain Management
Complete the steps in the following two sections to set up different types of vendor invoice import.

### Import vendor invoices from e-mail

1. Sign in to your Finance or Supply Chain Management environment and verify that you are in the correct legal entity.
2. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
3. On **Features** tab, make sure the **NF-e Federal - Brazilian electronic invoice** is selected.
4. On **External channels** tab, on **Channels** field group, select **Add.**
5. In the **Channel** field, enter **NFe** (the name of the channel given in the configuration of the data channel for the Electronic invoicing feature in RCS).
6. In the **Description** field, enter a description and in the **Company** field, select the legal entity.
7. In the **Document context** field, select **Fiscal document context – Customer invoice context model**
8. In the **Import sources** field group, select **Add.**
9. In the **Name** field, enter **XmlFile** (the name of the **Attachment filter** given in the configuration of the data channel for the Electronic invoicing feature in RCS)
10. In the **Description** field, enter a description, and in the **Data entity name** field, select **Received NF-e XML documents**.
11. In the **Model mapping** field, select **NF-e mail import – NF-e email import (BR)** and then select **Save**.
12. On the **Electronic document** tab, in the **Electronic reporting** field group select **Add**, and in the **Table name** field, select **Received NF-e XML document**.
13. In the **Document context** field, select **Inquire fiscal document context – Customer invoice context**.
14. In the **Electronic document model mapping** field, select **Inquire mapping – Fiscal document mapping**.
15. Select **Response types**, and then select **New.**
16. In the **Response type** field, enter **Response** and in the **Submission status** field, enter **Scheduled.**
17. In the **Model mapping** field, select **Model mapping from response message – Response message import format**.
18. Select **Save** and then close the page.

### Import PEPPOL electronic vendor invoices

1. Go to the **Electronic reporting** workspace and select **Reporting configurations**.
2. Select **Customer invoice context model** and create a derived configuration.
3. On the **Draft** version, select **Designer**.
4. In the **Data model** tree, select **Customer invoice**, and then select **Map model to datasource**.
5. In the **Definitions** tree, select **CustomerInvoice** and then select **Designer**.
6. In the **Data sources** tree, select **Context\_Channel**, and in the **Value** field, select **PEPPOL**. This is the name of the channel given in the configuration of the data channel for the Electronic invoicing feature in RCS. 
7. Select **Save** and close the page.
8. Close the page.
9. Select **Customer invoice context model**, and on the **Versions** FastTab, select **Change Status** > **Completed**.
10. Go to **Organization administration** > **Setup** > **Electronic document parameters** and on the **Features** tab, make sure the **PEPPOL Global electronic invoices** is selected. 
11. On the **External channels** tab, in the **Channels** field group, select **Add**.
12. In the **Channel** field, enter **PEPPOL** and in the **Description** field, enter a description.
13. In the **Company** field, select the legal entity, and in the **Document context** field, select **Customer invoice context – Customer invoice context model**
14. Select **Save** and then close the page.


## Receive electronic invoices

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Receive electronic documents**.
2. Select **OK** and then close the page.

## View receive logs for electronic invoices

To view the receive logs for electronic invoices, go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
