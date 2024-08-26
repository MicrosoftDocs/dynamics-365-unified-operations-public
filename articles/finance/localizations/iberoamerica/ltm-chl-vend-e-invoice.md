---
title: Vendor electronic invoice import in Chile
description: Learn how to configure and use vendor electronic invoice import for Chile in Microsoft Dynamics 365 Finance, including prerequisites.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/19/2024
ms.reviewer: johnmichalak
ms.search.region: Chile
ms.search.validFrom: 2024-08-07
ms.dyn365.ops.version: AX 10.0.41
---

# Vendor electronic invoice import in Chile

[!include [banner](../../includes/banner.md)]

This article explains how to configure and use vendor electronic invoice import for Chile from the country-specific XML format in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you complete the tasks in this article, the following prerequisites must be met:

1. The primary address of the legal entity must be in Chile.
1. Ensure that the settings for the Chilean legal entity are in place. For more information, see [Set up legal entity and tax information for Chile](ltm-chile-set-up-legal-entity-tax-information.md).
1. [Configure electronic invoice parameters for Chile](ltm-chile-conf-electronic-invoice.md).
1. Gain familiarity with and understanding of Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
1. Do the common part of Electronic Invoicing service configuration as it's described in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).
1. The **Enable application response for vendor invoices** feature must be enabled in Feature management.
1. Ensure that the following Electronic reporting (ER) format configurations are imported:

    - Customer invoice context model
    - Inventory e-invoice (CL) XML Import
    - Vendor Invoice Mapping to Destination LATAM
    - Application response (CL)
    - Pending vendor invoice model mapping

> [!NOTE]
> The ER format is based on the **Invoice model LATAM** configuration and uses the **Vendor Invoice Mapping to Destination LATAM** configuration. All additional configurations that are required are automatically imported.

## Configure the Electronic invoicing feature

### Import channel

To enable an inbound flow, you must create a feature setup of the **Import channel** type for the **Chilean electronic invoice (CL) "E-Invoicing for Chile: ISV last-mile connector with Edicom"** Globalization feature.

1. Select the **Setups** tab of the derived feature.
1. Select **Add**, and then select **Custom setup**.
1. Enter a name and description for the feature setup.
1. Select **Import channel** as the setup type and **Edicom service** as the data channel.
1. Select **Create**.
1. Select the feature setup that is created for vendor invoice import.
1. Select **Edit**.
1. On the **Import channel** tab, set the import channel parameters.

    The following illustration shows the parameters for the feature setup set to the values that Edicom provided to Microsoft for testing purposes. The values that you enter will differ. Edicom provides these values to you when you're onboarded.

    ![Screenshot that shows the configured Feature setup parameters of the Import channel for the Globalization feature for Chile.](ltm-chl-vend-e-invoice-import-channel-parms.png)

### Applicability rules

Applicability rules must be correctly configured to provide context, so that the exact Electronic invoicing Globalization feature that must run in the Electronic Invoicing service can be found. Create a new applicability rule for the same channel name that you specified for the import channel configuration in the previous section. For example, add an applicability rule that has an **And** clause for the **Channel** field when its value equals the "edi\_in" string.

### Variables

Out of the box, variables are provided with the specific feature setup to support the `EdicomId`, `Response`, and `ResponseXML` variables, as shown in the following illustration.

![Screenshot of the setup on the Variables tab of the Feature version setup page.](ltm-chl-vend-e-invoice-variables.png)

> [!NOTE]
> After the feature setup is completed, save, complete, and deploy the version.

## Configure ER

1. Go to the **Electronic reporting** workspace, and open **Reporting configurations**.
1. Derive a configuration from **Customer Invoice Context Model**.
1. In the new configuration, go to **Designer** \> **Map model to datasource** \> **Data channel** \> **Designer**.
1. Point to the Data model source type under the **Mapping** tab on the left.
1. To set up the data channel context, expand the **$Context_Channel** container and update the **Value** calculated field with your channel name.
1. Save your change.

    The following illustration shows an example of the change.

    ![Screenshot of the change of data channel context.](ltm-chl-vend-e-invoice-CustInvContextModel-channel-name.png)

1. Return to **Reporting configurations**.
1. Select the **Vendor invoice Mapping to destination LATAM** configuration.
1. Set the **Default for model mapping** option to **Yes**.

## Configure parameters

### Configure electronic document parameters

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Chile are imported. For more information, see [Set up Electronic document parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic document** tab, add a record, and set the following values for it:

    - **Table name:** Application response
    - **Document context:** Customer invoice context model - Application response context
    - **Electronic document model mapping:** Pending vendor invoice model mapping - Application response

    ![Screenshot of the setup on the Electronic document tab of the Electronic document parameters page.](ltm-chl-e-invoice-documents-app-response.png)

1. On the **Integration channels** tab, create records. Specify a channel name of the **Import** type, and specify the document context configuration for every required company.
1. For each channel, add an import source, and set the following values for it:

    - **Name:** Enter the response format.
    - **Data entity name:** Select **Vendor invoice header**.
    - **Model mapping:** Specify the model mapping for the invoice import.

    ![Screenshot of the Integration channels tab of the Electronic document parameters page.](ltm-chl-vend-e-invoice-parms-integration-channels.png)

1. Save your changes, and close the page.

### Configure vendor data

During the import process, vendors are identified by their tax exempt number. To enable correct vendor identification, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select a vendor.
1. On the **LATAM** FastTab, in the **Country identification number** field, enter a valid identification number of the country for the vendor. This number is used to identify the vendor during import, by matching it to the value of the **DTE\\Documento\\Encabezado\\RUTEmisor** element in the import XML file.

### Configure products

During the import process, products are identified by their external descriptions. These descriptions are usually vendor-specific. To enable correct product identification, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select a product, and then, on the **Purchase** menu, in the **Related information** section, select **External item description**.
1. Create a new external description for the selected product.
1. In the **Account code** column, select **Table** to define an external product description for a specific vendor.
1. In the **Vendor relation** column, select a vendor.
1. In the **External item number** column, enter an external product code. This code is used to identify the product during import, by matching the code to the value of the **DTE\\Documento\\Detalle\\NmbItem** element in the import XML file.

> [!NOTE]
> If there must be non-stocked items, the system expects that these products belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page.
>
> If no related **Non-stock** products exist, the system tries to import invoice lines by referring to a default item. The default item must be configured in the system as a released product where the code is defined exactly as **DEFAULT\_ITEM**, and the product must belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page.

## Import vendor electronic invoices and send application responses

To run the import vendor electronic invoices, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
1. In the **Receive electronic documents** dialog box, specify the parameters as required.
1. Select **OK** to immediately start the import process or to schedule the import to run in the background.

### Import process description

Here is an overview of the steps in the import process and the order that they occur in.

1. Vendors are identified by using the country identification number that is defined in the vendor record. If no vendor matches the data that is being searched, the import process fails, and a related error message is shown.
1. Products that are used on invoice lines are identified by using an external item number, which might be vendor-specific. If no product matches the external description, the import process fails, and a related error message is shown.
1. If an incoming import file contains the information about purchase orders and its lines in the **DTE\\Documento\\Referencia\\FolioRef** elements, the numbers are used for invoice matching with purchase orders and lines that are entered in the system.
1. If no order or line references are defined in an incoming file, the system tries to automatically match incoming vendor invoices with existing purchase orders.
1. If no purchase order is found, the system raises a warning but continues the import. It now considers products on invoice lines **Non-stock** items. The system expects that these products belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page.
1. If no related **Non-stock** products exist, the system tries to import invoice lines by referring to a default item. The default item must be configured in the system as a released product where the code is defined exactly as **DEFAULT\_ITEM**, and the product must belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page. If no default item is configured in the system, the import process fails, and a related error message is shown.

Successfully imported vendor electronic invoices are shown in the system as pending invoices. To review imported invoices, go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

### Application response

After the imported vendor electronic invoice is reviewed on the **Pending vendor invoices** page (**Accounts payable** \> **Invoices** \> **Pending vendor invoices**), an application response can be saved and submitted. The application response indicates either acceptance or rejection of the invoice. If the invoice is either accepted with discrepancies or rejected, the response includes comments. If the invoice is rejected, the response also includes the reason for the rejection.

To fill in the application response, follow these steps.

1. Open the **Pending vendor invoices** page in edit mode for the desired invoice.
1. On the Action Pane, select **Review**.
1. In the dropdown dialog box, in the **Response type** field, select one of the following values, as required:

    - Accept
    - Accept with discrepancies
    - Reject

1. If you selected either **Accept with discrepancies** or **Reject** as the response type, enter comments in the **Comments** field.
1. If you selected **Reject** as the response type, select one of the following values in the **Reason for rejection** field:

    - Claim to the content of the document
    - Claim for Partial Shortage of Goods
    - Claim for Total Shortage of Goods

1. Select **Save**.

    ![Screenshot of an application response in the Review dropdown dialog box.](ltm-chl-vend-e-invoice-app-response.png)

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**.
1. On the **Records to include** FastTab, select **Filter**.
1. On the **Joins** tab, add vendor invoices to the join for the application response.
1. On the **Range** tab, add a criterion for the invoice number to the **Vendor invoices** table.
1. Submit the application response.

> [!IMPORTANT]
> After the application response is submitted, it can't be modified.
>
> Application responses must be sent before the pending vendor invoices are posted. The application response capability isn't available for posted invoices.

## Learn more

- [Get started with Electronic invoicing for Chile](ltm-chile-elec-invo-conncection.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
